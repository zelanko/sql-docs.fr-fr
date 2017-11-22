---
title: "Guide d’architecture de gestion de la mémoire | Microsoft Docs"
ms.custom: 
ms.date: 10/21/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: relational-databases-misc
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- guide, memory management architecture
- memory management architecture guide
ms.assetid: 7b0d0988-a3d8-4c25-a276-c1bdba80d6d5
caps.latest.revision: "6"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8e3dd8e87facc46305c7a3f86e9f7507fa29cd6b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="memory-management-architecture-guide"></a>Guide d’architecture de gestion de la mémoire
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

## <a name="memory-architecture"></a>Architecture de la mémoire

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acquiert et libère la mémoire dynamiquement selon ses besoins. En règle générale, un administrateur ne doit plus spécifier la quantité de mémoire à allouer à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], même si cette option existe toujours et est obligatoire dans certains environnements.

L'un des objectifs principaux de tous les logiciels de base de données est de réduire les E/S disque, car les opérations de lecture et écriture sur le disque font partie des opérations les plus consommatrices de ressources. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] crée un pool de mémoires tampons en mémoire afin d’y garder les pages lues à partir de la base de données. Une grande partie du code [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vise à réduire au minimum le nombre d’opérations de lecture et d’écriture physiques entre le disque et le pool de mémoires tampons. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tente d’atteindre un équilibre entre deux objectifs :

* Empêcher le pool de mémoires tampons d'atteindre une taille susceptible de priver le système de mémoire.
* Réduire les E/S physiques vers les fichiers de la base de données en augmentant la taille du pool de mémoires tampons.


> [!NOTE]
> Dans un système surchargé, certaines requêtes volumineuses dont l'exécution nécessite une importante quantité de mémoire ne peuvent pas obtenir la quantité minimale de mémoire requise et reçoivent une erreur de temporisation pendant qu'elles attendent des ressources mémoire. Pour résoudre ce problème, augmentez la valeur de [l'option query wait](../database-engine/configure-windows/configure-the-query-wait-server-configuration-option.md). Pour une requête parallèle, envisagez de réduire [l'option max degree of parallelism](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)(Degré maximum de parallélisme).
 
> [!NOTE]
> Dans un système où une charge très lourde pèse sur les ressources mémoire, les requêtes comportant jointure de fusion, tri et bitmap dans le plan de requête peuvent éliminer le bitmap si elles n'obtiennent pas la mémoire minimale nécessaire pour ce bitmap. Ceci peut affecter les performances de la requête, et, si le processus de tri ne tient pas en mémoire, ceci peut accroître l'utilisation des tables de travail dans la base de données tempdb, ce qui augmente le volume de tempdb. Pour résoudre ce problème, ajoutez de la mémoire physique ou paramétrez les requêtes de façon qu'elles utilisent un autre plan de requête plus rapide.
 
### <a name="providing-the-maximum-amount-of-memory-to-includessnoversionincludesssnoversion-mdmd"></a>Apport de la quantité maximale de mémoire à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]

L’utilisation d’AWE et du privilège de verrouillage des pages en mémoire vous permet de fournir les quantités de mémoire suivantes au moteur de base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . (le tableau suivant comprend une colonne pour les versions 32 bits qui ne sont plus disponibles).

| |32 bits <sup>1</sup> |64 bits
|-------|-------|-------| 
|Mémoire conventionnelle |Toutes les éditions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . jusqu'à la limite d'espace d'adressage virtuel de processus : <br>- 2 Go<br>- 3 Go avec le paramètre d’amorçage /3 gb <sup>2</sup> <br>- 4 Go sur WOW64 <sup>3</sup> |Toutes les éditions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . jusqu'à la limite d'espace d'adressage virtuel de processus : <br>- 7 To avec l’architecture IA64 (IA64 non pris en charge dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] et les versions ultérieures)<br>- Maximum du système d’exploitation avec architecture x64 <sup>4</sup>
|Mécanisme AWE (Permet à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] d'aller au-delà de la limite d'espace d'adressage virtuel de processus sur une plateforme 32 bits.) |Éditions[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard, Enterprise et Developer : le pool de mémoires tampons est en mesure d’accéder à 64 Go de mémoire maximum.|Non applicable <sup>5</sup> |
|Privilège de verrouillage des pages en mémoire du système d’exploitation (permet de verrouiller la mémoire physique, empêchant ainsi la pagination par le système d’exploitation de la mémoire verrouillée). <sup>6</sup> |Éditions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard, Enterprise et Developer : nécessaire pour les processus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] devant utiliser le mécanisme AWE. La mémoire allouée par le biais du mécanisme AWE ne peut pas être dépaginée. <br> L'accord de ce privilège sans l'activation de AWE n'a aucun effet sur le serveur. |[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] éditions Enterprise et Developer : recommandé, afin d’éviter la pagination par le système d’exploitation. Peut apporter un gain de performances, selon la charge de travail. La quantité de mémoire accessible est semblable au cas de mémoire conventionnelle. |

<sup>1</sup> les versions 32 bits ne sont pas disponibles à partir de la version [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
<sup>2</sup> /3gb est un paramètre d’amorçage de système d’exploitation. Pour plus d'informations, consultez la MSDN Library.  
<sup>3</sup> WOW64 (Windows on Windows 64) est un mode dans lequel [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 32 bits s’exécute sur un système d’exploitation 64 bits.  
<sup>4</sup> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] édition Standard prend en charge jusqu’à 128 Go. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] édition Enterprise prend en charge le maximum du maximum du système d’exploitation...  
<sup>5</sup> Notez que l’option sp_configure awe enabled est présente sur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]64 bits, mais qu’elle est ignorée.    
<sup>6</sup> Si le privilège de verrouillage des pages en mémoire (LPIM) est accordé (sur la version 32 bits pour la prise en charge d’AWE ou sur la version 64 bits par elle-même), nous recommandons de définir également la mémoire de serveur maximale.

> [!NOTE]
> Les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peuvent s’exécuter sur un système d’exploitation 32 bits. L’accès à plus de 4 gigaoctets de mémoire sur un système d’exploitation 32 bits nécessite Address Windowing Extensions (AWE) pour gérer la mémoire. Cela n’est pas nécessaire lorsque [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est exécuté sur des systèmes d’exploitation 64 bits. Pour plus d’informations sur AWE, consultez [Espace d’adressage de processus](https://msdn.microsoft.com/library/ms189334) et [Gestion de la mémoire pour des bases de données volumineuses](https://msdn.microsoft.com/library/ms191481) dans la documentation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2008.   


## <a name="dynamic-memory-management"></a>Gestion dynamique de la mémoire

Le comportement par défaut de la gestion de la mémoire du moteur de base de données Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] consiste à acquérir autant de mémoire que nécessaire sans causer d’insuffisance de mémoire sur le système. Pour cela, le moteur de base de données utilise les API de notification de mémoire de Microsoft Windows.

L’espace d’adressage virtuel de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut être divisé en deux zones distinctes : l’espace occupé par le pool de mémoires tampons et le reste. Si le mécanisme AWE est activé, le pool de mémoires tampons peut se trouver dans la mémoire mappée AWE, ce qui donne davantage d'espace pour les pages de base de données. 

Le pool de mémoires tampons fait office de source principale d'allocation mémoire de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Des composants externes qui résident dans le processus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , tels que les objets COM, et qui ne gèrent pas les fonctions de gestion de mémoire de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , utilisent la mémoire en dehors de l’espace d’adressage virtuel occupé par le pool de mémoires tampons.

Lorsque [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] démarre, il calcule la taille de l'espace d'adressage virtuel pour le pool de mémoires tampons d'après plusieurs paramètres, dont la quantité de mémoire physique du système, le nombre de threads serveur et diverses options de démarrage. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] réserve la quantité ainsi calculée de son espace d’adressage virtuel de processus pour le pool de mémoires tampons, mais il acquiert (valide) uniquement la quantité nécessaire de mémoire physique pour la charge actuelle.

L'instance continue alors à acquérir de la mémoire comme l'exige la prise en charge de la charge de travail. Au fur et à mesure que des utilisateurs se connectent et exécutent des requêtes, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acquiert la mémoire physique supplémentaire à la demande. Une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] continue d’acquérir de la mémoire physique jusqu’à ce qu’elle atteigne sa cible d’allocation de mémoire maximum du serveur ou jusqu’à ce que Windows indique qu’il n’y a plus de mémoire disponible en surplus. Elle libère de la mémoire quand elle en a plus que la valeur de mémoire minimum du serveur paramétrée et si Windows indique qu’il y a une insuffisance de mémoire disponible.

Étant donné que d'autres applications sont démarrées sur l'ordinateur exécutant une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], elles consomment de la mémoire et la quantité de mémoire physique disponible descend en dessous de la cible de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . L'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] règle sa consommation de mémoire. Si une autre application est arrêtée, la mémoire disponible est augmentée, et l’instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] augmente la taille de son allocation de mémoire. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut libérer et acquérir plusieurs mégaoctets de mémoire chaque seconde, ce qui lui permet de s’adapter rapidement aux changements d’allocation de mémoire.


## <a name="effects-of-min-and-max-server-memory"></a>Effets des options de configuration « min server memory » et « max server memory »

Les options de configuration min server memory et max server memory permettent d’établir les limites supérieure et inférieure de la quantité de mémoire utilisée par le pool de mémoires tampons du moteur de base de données Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Le pool de mémoires tampons n'obtient pas immédiatement la quantité de mémoire spécifiée dans min server memory. En effet, il commence seulement avec la mémoire nécessaire à l'initialisation. Au fur et à mesure que la charge de travail du moteur de base de données augmente, celui-ci acquiert la mémoire nécessaire à la prise en charge de cette charge de travail. Le pool de mémoires tampons ne libère aucune partie de la mémoire acquise avant d'atteindre la valeur spécifiée dans min server memory. Dès lors que la quantité spécifiée dans min server memory est atteinte, le pool de mémoires tampons utilise l'algorithme standard pour acquérir et libérer la mémoire en fonction des besoins. La seule différence réside dans le fait que le pool de mémoires tampons ne diminue jamais son allocation de mémoire en dessous de la valeur spécifiée dans min server memory et n'obtient jamais plus de mémoire que le niveau spécifié dans max server memory.

> [!NOTE]
> En tant que processus,[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] acquiert plus de mémoire qu’indiqué par l’option max server memory. Les composants internes et externes peuvent allouer de la mémoire en dehors du pool de mémoires tampons, qui consomme un supplément de mémoire, mais la mémoire allouée au pool de mémoires tampons représente généralement la plus grande part de mémoire consommée par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].


La quantité de mémoire acquise par le moteur de base de données dépend entièrement de la charge de travail placée dans l'instance. Une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui ne traite pas beaucoup de demandes risque de ne jamais atteindre la valeur de min server memory.

Si la valeur spécifiée pour min server memory et pour max server memory est identique, le moteur de base de données cesse de libérer et d'acquérir de la mémoire de façon dynamique pour le pool de mémoires tampons une fois que la mémoire allouée au moteur de base de données a atteint cette valeur.

Si une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fonctionne sur un ordinateur sur lequel d’autres applications sont régulièrement arrêtées ou démarrées, l’allocation et la désallocation de mémoire par l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut ralentir le démarrage de ces applications. De même, si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est une application serveur parmi d’autres exécutées sur un seul ordinateur, l’administrateur système doit éventuellement contrôler la quantité de mémoire allouée à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour ce faire, il peut utiliser les options min server memory et max server memory pour contrôler la quantité de mémoire utilisable par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Pour en savoir plus, consultez les [Options de configuration de la mémoire du serveur](../database-engine/configure-windows/server-memory-server-configuration-options.md).

Les options min server memory et max server memory sont spécifiées en mégaoctets.

## <a name="memory-used-by-includessnoversionincludesssnoversion-mdmd-objects-specifications"></a>Utilisation de la mémoire par les spécifications d’objets [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]

La liste suivante décrit la quantité estimée de mémoire utilisée par différents objets dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les quantités indiquées sont des estimations. Elles peuvent varier en fonction de l’environnement et de la manière dont les objets sont créés.

* Verrou : 64 octets + 32 octets par propriétaire   
* Connexion utilisateur : environ (3* *taille_paquet_réseau + 94 Ko)    

La taille des paquets réseau représente la taille des paquets TDS (Tabular Data Scheme) utilisés pour la communication entre des applications et le moteur de base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . La taille par défaut s'élève à 4 Ko ; elle est contrôlée par l'option de configuration Taille du paquet réseau.

Quand la fonctionnalité MARS (Multiple Active Result Sets) est activée, la connexion utilisateur est environ (3 + 3 * nombre_connexions_logiques) * taille_paquet_réseau + 94 Ko.

## <a name="buffer-management"></a>Gestion des tampons

L'objectif principal d'une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est de stocker et de récupérer les données, l'utilisation intensive d'E/S sur disque est donc une caractéristique centrale du moteur de base de données. Étant donné que les opérations d'E/S sur disque peuvent consommer beaucoup de ressources et durent relativement longtemps, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s'attache à rendre ces opérations efficaces. La gestion des tampons joue un rôle essentiel pour parvenir à cette efficacité. Le composant de gestion des tampons comprend deux mécanismes : le gestionnaire de tampons qui permet d'accéder et mettre à jour les pages de la base de données, et le cache des tampons (également appelé pool de mémoires tampons), qui permet de réduire les opérations d'E/S du fichier de la base de données. 

### <a name="how-buffer-management-works"></a>Fonctionnement de la gestion des tampons

Un tampon est une page de 8 Ko en mémoire dont la taille est similaire à une page d'index ou de données. Ainsi, le cache des tampons est divisé en pages de 8 Ko. Le gestionnaire des tampons gère les fonctions de lecture des pages d'index ou de données à partir des fichiers de disque de base de données dans le cache de tampons ainsi que la réécriture sur le disque des pages modifiées. Une page reste dans le cache des tampons jusqu'à ce que le gestionnaire de tampons ait besoin de la zone de mémoire tampon pour lire davantage de données. Les données ne sont réécrites sur le disque que si elles sont modifiées. Les données dans le cache de tampons peuvent être modifiées plusieurs fois avant leur réécriture sur le disque. Pour plus d’informations, consultez [Lecture de pages](../relational-databases/reading-pages.md) et [Écriture de pages](../relational-databases/writing-pages.md).

Lorsque [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] démarre, il calcule la taille de l’espace d’adressage virtuel pour le cache des tampons d’après plusieurs paramètres, dont la quantité de mémoire physique du système, le nombre de threads serveur maximum configuré et diverses options de démarrage. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] réserve la quantité ainsi calculée de son espace d’adressage virtuel de processus (appelée cible mémoire) pour le cache des tampons, mais il acquiert (valide) uniquement la quantité de mémoire physique nécessaire pour la charge actuelle. Vous pouvez interroger les colonnes **bpool_commit_target** et **bpool_committed** dans la vue du catalogue [sys.dm_os_sys_info](../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md) pour retourner le nombre de pages réservées comme cible mémoire et le nombre de pages actuellement réservées dans le cache des tampons, respectivement.

L’intervalle entre le démarrage de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et le moment où la mémoire tampon obtient sa cible de mémoire s’appelle l’accélération. Au cours de cette opération, les tampons se remplissent de demandes de lecture selon les besoins. Par exemple, une demande de lecture d'une page unique remplit une page de tampon unique. Cela signifie que l'accélération dépend du nombre et du type des demandes clientes. L'accélération s'effectue par la transformation des demandes de lecture de page unique en demandes de huit pages alignées. Cette opération permet au processus d'accélération de s'achever plus rapidement en particulier sur les ordinateurs possédant beaucoup de mémoire.

Comme le gestionnaire de tampons consomme l'essentiel de la mémoire dans les processus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , il collabore avec le gestionnaire de la mémoire afin de permettre aux autres composants d'utiliser ses tampons. Le gestionnaire de tampons interagit essentiellement avec les composants suivants :

* Le gestionnaire de ressources pour contrôler l'utilisation de l'ensemble de la mémoire et, sur les plateformes 32 bits, pour contrôler l'utilisation de l'espace d'adressage.  
* Le gestionnaire de base de données et le système d’exploitation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (SQLOS) pour les opérations d’E/S de fichier peu importantes.  
* le gestionnaire du journal pour la journalisation préalable.  

### <a name="supported-features"></a>Fonctionnalités prises en charge

Le gestionnaire de tampons prend en charge les fonctionnalités suivantes.

* Le gestionnaire de tampons est compatible avec la technologie NUMA (Non-Uniform Memory Access). Les pages de cache des tampons sont réparties sur les nœuds NUMA matériels, ce qui permet à un thread d'accéder à une page de tampons allouée sur le nœud NUMA local au lieu de la mémoire étrangère. 
* Le gestionnaire de tampons prend en charge l'ajout de mémoire à chaud, ce qui permet aux utilisateurs d'ajouter de la mémoire physique sans redémarrer le serveur. 
* Le gestionnaire de tampons prend en charge les grandes pages sur les plateformes 64 bits. La taille de la page est spécifique à la version de Windows. 
* Le gestionnaire de tampons fournit les diagnostics supplémentaires exposés par le biais des vues de gestion dynamique. Vous pouvez utiliser ces affichages pour contrôler un ensemble de ressources du système d'exploitation spécifiques à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Par exemple, vous pouvez utiliser la vue sys.dm_os_buffer_descriptors pour contrôler les pages dans le cache des tampons.   

### <a name="disk-io"></a>E/S disque
Le gestionnaire de tampons n'effectue que des lectures et des écritures dans la base de données. Les autres opérations de base de données et de fichier comme les opérations d'ouverture, de fermeture, d'élargissement et de compactage sont prises en charge par les composants du gestionnaire de base de données et du gestionnaire de fichiers. 

Les opérations d'E/S disque effectuées par le gestionnaire de tampons présentent les caractéristiques suivantes :

* Toutes les opérations d'E/S s'effectuent de manière asynchrone, ce qui permet au thread appelant de continuer le traitement durant l'opération d'E/S en arrière-plan.
* Toutes les opérations d'E/S ont lieu dans des threads appelants, sauf si l'option affinity I/O est utilisée. L'option affinity I/O mask lie les E/S disque de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à un sous-ensemble de processeurs spécifié. Dans les environnements de traitement transactionnel en ligne (OLTP) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] haut de gamme, cette extension permet d'améliorer les performances des threads [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] émettant des E/S.
* Les E/S de pages multiples s'effectuent à l'aide d'E/S par fragmentation-rassemblement, ce qui permet le transfert des données dans des zones contiguës de la mémoire ou hors de celles-ci. Cela signifie que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut remplir ou vider rapidement le cache de tampons tout en évitant les demandes d'E/S physiques multiples. 

#### <a name="long-io-requests"></a>Longues demandes d'E/S  
Le gestionnaire de tampons signale les demandes d'E/S en suspens pendant un délai minimum de 15 secondes. L'administrateur système peut ainsi distinguer entre les problèmes [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les problèmes au niveau du sous-système d'E/S. Le message d’erreur 833 est rapporté et consigné dans le journal des erreurs [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] comme suit :

`` 
SQL Server has encountered %d occurrence(s) of I/O requests taking longer than %d seconds to complete on file [%ls] in database [%ls] (%d). The OS file handle is 0x%p. The offset of the latest long I/O is: %#016I64x.
`` 

Une longue opération d'E/S peut correspondre à une opération de lecture ou d'écriture ; celle-ci ne figure pas dans le message actif. Les messages d'opérations d'E/S longues sont des avertissements pas des erreurs. Ils n'indiquent pas de problèmes avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les messages permettent à l'administrateur de détecter la cause des temps de réponse [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] médiocres plus rapidement et de distinguer les problèmes qui ne dépendent pas de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. De ce fait, ces problèmes ne demandent aucune intervention, mais il est nécessaire que l'administrateur système analyse les raisons de la lenteur de la demande d'E/S et si ce délai est justifié.

#### <a name="causes-of-long-io-requests"></a>Facteurs de longues demandes d'E/S  
Un message signalant une opération d'E/S longue peut indiquer qu'une E/S est bloquée de manière permanente et ne peut s'achever (E/S perdue) ou qu'elle ne s'est pas encore terminée. Il est impossible d'identifier le type de scénario à partir du message, même si une E/S perdue entraîne souvent un délai d'attente de verrou.

Une opération d'E/S longue indique souvent une charge de travail [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] trop intense pour le sous-système de disque. Un sous-système de disque inapproprié peut se manifester dans les cas suivants :

* plusieurs opérations d'E/S longues dans le journal d'erreurs au cours d'une charge [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] importante ;
* les compteurs de performance indiquent des latences de disque longues, des files d'attente de disque longues ou pas d'inactivité de disque.  

Les opérations d'E/S longues sont aussi parfois causées par un composant dans le chemin d'accès d'E/S (un pilote, un contrôleur, un microprogramme, entre autres) qui retardent continuellement une demande d'E/S antérieure pour traiter des demandes plus récentes dont la position actuelle est plus proche de la tête de disque. La technique courante de traitement prioritaire des demandes en fonction de la proximité de celles-ci de la tête de lecture-écriture est connue sous le nom de « elevator seeking ». Cette technique peut ne pas être compatible avec l'outil Moniteur système Windows (PERFMON.EXE) en raison du traitement rapide de la plupart des E/S. Les opérations d'E/S longues peuvent se compliquer en raison de charges de travail impliquant de grandes quantités d'E/S séquentielle, parmi lesquelles figurent les opérations de sauvegarde et de restauration, les analyses de table, les tris, les créations d'index, les chargements en masse et les réinitialisations de fichiers.

Les opérations d'E/S longues isolées qui ne présentent à priori aucun rapport avec les conditions décrites plus haut sont peut-être causées par un problème de matériel ou de pilote. Le journal d'événements système peut contenir un événement connexe qui permet de diagnostiquer le problème.

#### <a name="error-detection"></a>Détection d'erreurs  
Les pages de base de données peuvent faire appel à deux mécanismes facultatifs qui permettent de garantir l'intégrité de la page depuis son écriture sur le disque à sa relecture : les protections de la somme de contrôle et de la page endommagée. Ces mécanismes offrent une méthode indépendante de vérification de l'exactitude du stockage des données ainsi que des composants matériels tels que les contrôleurs, les pilotes, les câbles et même le système d'exploitation. La protection est ajoutée à la page juste avant l'écriture sur le disque, puis elle est vérifiée après sa lecture sur le disque.

#### <a name="torn-page-protection"></a>Protection de page endommagée  
La protection de page endommagée, introduite dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000, est essentiellement une méthode de détection des pages endommagées causées par les pannes d’alimentation. Par exemple, une panne d'alimentation inattendue peut n'entraîner que l'écriture partielle d'une page sur le disque. Grâce à la protection de page endommagée, une signature de 2 bits est placée à la fin de chaque secteur de 512 octets dans la page (après la copie des deux bits d'origine dans l'en-tête de la page). La signature alterne entre des binaires 01 et 10 à chaque opération d’écriture. Il est donc toujours possible de savoir si seule une partie des secteurs a été écrite sur le disque : si un bit est dans le mauvais état lors de la lecture ultérieure de la page, celle-ci a été écrite de manière incorrecte et une page endommagée est détectée. Ce type de détection fait appel à des ressources minimales ; cependant, elle ne détecte pas toutes les erreurs causées par les pannes de matériel des disques.

#### <a name="checksum-protection"></a>Protection de la somme de contrôle  
La protection de la somme de contrôle, introduite dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2005, fournit une vérification renforcée de l’intégrité des données. Une somme de contrôle est calculée pour les données de chaque page écrite, elle est stockée dans l'en-tête de page. À chaque lecture d'une page contenant une somme de contrôle stockée sur le disque, le moteur de la base de données recalcule la somme de contrôle pour les données de la page et renvoie l'erreur 824 si la nouvelle somme de contrôle n'est pas identique à la somme de contrôle stockée. La protection de la somme de contrôle peut détecter un plus grand nombre d'erreurs que la protection de page endommagée car celle-ci est affectée par chaque octet de la page, elle utilise toutefois peu de ressources. Lorsque la somme de contrôle est activée, les erreurs causées par les pannes d'alimentation et du matériel ou des microprogrammes défectueux sont détectables à chaque lecture d'une page sur le disque par le gestionnaire de tampons.

Le type de protection de page utilisé est un attribut de la base de données qui contient la page. La protection de la somme de contrôle est la protection par défaut pour les bases de données créées dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2005 et les versions ultérieures. Le mécanisme de protection de page est spécifié au moment de la création de la base de données et peut être modifié à l'aide de ALTER DATABASE. Vous pouvez déterminer le paramètre de protection de page en cours en interrogeant la colonne page_verify_option de l’affichage catalogue [sys.databases](../relational-databases/system-catalog-views/sys-databases-transact-sql.md) ou la propriété IsTornPageDetectionEnabled de la fonction [DATABASEPROPERTYEX](../t-sql/functions/databasepropertyex-transact-sql.md) . En cas de modification du paramètre de protection de page, le nouveau paramètre ne prend pas immédiatement effet dans l'ensemble de la base de données. Par contre, les pages adoptent le niveau de protection en cours de la base de données lors de leur écriture ultérieure. Cela signifie que la base de données peut contenir des pages utilisant différents types de protection. 

## <a name="understanding-non-uniform-memory-access"></a>Présentation de l'accès NUMA (Non-uniform Memory Access)

Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est compatible avec la technologie NUMA (Non-Uniform Memory Access) et fonctionne correctement avec l’accès NUMA matériel sans configuration particulière. À mesure que la vitesse et le nombre de processeurs augmentent, il devient de plus en plus difficile de réduire le temps de réponse de la mémoire requis pour exploiter cette puissance de traitement supplémentaire. Pour contourner ce problème, les fournisseurs de matériel proposent des caches L3 de grande capacité, mais cette solution présente des limites. L’architecture NUMA fournit une solution évolutive à ce problème. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a été conçu pour tirer parti des ordinateurs reposant sur la technologie NUMA sans qu’il soit nécessaire d’apporter des modifications aux applications. Pour en savoir plus, référez-vous à [Procédure : configurer SQL Server pour utiliser soft-NUMA](../database-engine/configure-windows/soft-numa-sql-server.md).

## <a name="see-also"></a>Voir aussi
[Lecture de pages](../relational-databases/reading-pages.md)   
 [Écriture de pages](../relational-databases/writing-pages.md)

