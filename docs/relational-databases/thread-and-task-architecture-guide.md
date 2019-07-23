---
title: Guide d’architecture de thread et de tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/13/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- guide, thread and task architecture
- thread and task architecture guide
ms.assetid: 925b42e0-c5ea-4829-8ece-a53c6cddad3b
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5dd4aa4c3beb769509884c6ebb75fd8c82c1c8ae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058130"
---
# <a name="thread-and-task-architecture-guide"></a>guide d’architecture de thread et de tâche
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Les threads sont une caractéristique du système d'exploitation qui permettent à la logique de l'application d'être séparée en plusieurs chemins d'exécution simultanés. Cette fonctionnalité est utile lorsque des applications complexes comprennent un grand nombre de tâches à exécuter simultanément. 

Lorsqu'un système d'exploitation exécute une instance d'application, il crée une unité appelée processus pour gérer cette instance. Ce processus est associé à un thread d'exécution. Il s'agit de la série d'instructions de programmation exécutées par le code de l'application. Par exemple, si une application simple comprend un seul jeu d'instructions pouvant être exécutées en série, il n'existe qu'un seul chemin d'exécution, ou thread, dans toute l'application. Les applications plus complexes peuvent exécuter plusieurs tâches en même temps, mais pas en série. Pour ce faire, l'application lance plusieurs processus distincts pour chaque tâche. Mais le démarrage d'un processus consomme beaucoup de ressources. Une application peut également lancer plusieurs threads. Les threads consomment relativement peu de ressources. De plus, l'exécution de chaque thread peut être programmée indépendamment des autres threads du même processus.

Les threads permettent aux applications complexes d'utiliser plus efficacement une UC, même sur des ordinateurs dotés d'une seul UC. Avec une UC, vous ne pouvez exécuter qu'un seul thread à la fois. Si un thread exécute une longue opération qui n'utilise pas l'UC, comme par exemple la lecture ou l'écriture sur le disque, un autre thread peut être exécuté avant la fin de la première opération. La possibilité d'exécuter des threads pendant que d'autres attendent la fin d'une opération permet à l'application d'optimiser l'utilisation de l'UC. Cela est particulièrement vrai pour les applications multi-utilisateurs qui utilisent beaucoup d'E/S disque, par exemple un serveur de bases de données. Les ordinateurs dotés de plusieurs microprocesseurs ou UC peuvent exécuter simultanément un thread par UC. Ainsi, si un ordinateur comprend huit UC, il peut exécuter huit threads en même temps.

## <a name="sql-server-batch-or-task-scheduling"></a>Planification de lots ou de tâches SQL Server

### <a name="allocating-threads-to-a-cpu"></a>Allocation de threads à une UC
Par défaut, chaque instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] commence chaque thread, et le système d’exploitation répartit les threads à partir des instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] entre les UC sur un ordinateur en fonction de la charge. Si l'affinité de processus a été activée au niveau du système d'exploitation, ce dernier attribue chaque thread à une UC spécifique. Par opposition, le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] attribue des threads de travail [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] aux planificateurs qui répartissent les threads de manière équitable entre les processeurs (UC).
    
Pour exécuter des travaux multitâches, par exemple lorsque plusieurs applications accèdent au même ensemble de processeurs, le système d’exploitation déplace parfois les threads de processus entre les différents processeurs. Même si cela est efficace du point de vue du système d'exploitation, cette activité peut réduire les performances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] du fait des charges système élevées, puisque chaque cache de processeur est rechargé par des données de façon répétée. L'affectation de processeurs à des threads spécifiques permet d'améliorer les performances dans ces conditions en éliminant les rechargements de processeurs et en réduisant la migration des threads entre les processeurs (réduisant ainsi les changements de contexte) ; une telle association entre un thread et un processeur est appelée affinité du processeur. Si l'affinité a été activée, le système d'exploitation attribue chaque thread à une UC spécifique. 

L’[option de masque d’affinité](../database-engine/configure-windows/affinity-mask-server-configuration-option.md) est définie à l’aide d’[ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md). Lorsque le masque d'affinité n'est pas défini, l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] alloue les threads de travail de manière équitable entre les planificateurs qui n'ont pas été masqués.

> [!CAUTION]
> Évitez de configurer l'affinité d’UC dans le système d'exploitation et le masque d'affinité dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Ces paramètres tentent d'obtenir le même résultat et, si les configurations sont incohérentes, les résultats risquent d'être imprévisibles. Pour plus d'informations, consultez l’[option de masque d'affinité](../database-engine/configure-windows/affinity-mask-server-configuration-option.md).

Le regroupement de threads permet d'optimiser les performances lorsque de nombreux clients sont connectés au serveur. Habituellement, un thread de système d'exploitation séparé est créé pour chaque demande de requête. Cependant, s'il existe des centaines de connexions au serveur, l'utilisation d'un thread par demande de requête peut consommer de grandes quantités de ressources système. L'[option Nombre maximum de threads de travail](..//database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md) permet à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de créer un pool de threads de travail afin de servir un grand nombre de demandes de requête, ce qui améliore les performances. 

### <a name="using-the-lightweight-pooling-option"></a>Utilisation de l'option Regroupement léger
La surcharge qu’implique le basculement des contextes de thread peut ne pas être significative. La plupart des instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne perçoivent aucune différence de performances entre les valeurs 0 et 1 de l'option de regroupement léger. Les seules instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] susceptibles de tirer parti du [regroupement léger](../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md) sont celles exécutées sur un ordinateur qui présente les caractéristiques suivantes :    
* Un serveur multiprocesseur de grande taille
* Exécution de toutes les UC près de leur capacité maximale
* Fréquence élevée de basculement des contextes

Ces systèmes peuvent augmenter légèrement leurs performances si la valeur 1 est attribuée à l’option Regroupement léger.

> [!IMPORTANT]
> N'utilisez pas la planification en mode fibre pour les opérations courantes. Cela peut réduire les performances en bloquant les avantages habituels du basculement de contexte. Par ailleurs, certains composants de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne peuvent pas fonctionner correctement en mode fibre. Pour plus d’informations, reportez-vous au [regroupement léger](../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).

## <a name="thread-and-fiber-execution"></a>Exécution de threads et de fibres
Microsoft Windows utilise un système de priorité numérique qui va de 1 à 31 pour planifier l'exécution des threads. Le zéro est réservé pour le système d'exploitation. Lorsque plusieurs threads attendent d'être exécutés, Windows envoie le thread dont la priorité est la plus élevée.

Par défaut, chaque instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est une priorité 7 (priorité dite normale). Ceci octroie aux threads [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] une priorité suffisamment élevée pour obtenir les ressources UC dont ils ont besoin sans pénaliser les autres applications. 

L'option de configuration [Renforcement de priorité](../database-engine/configure-windows/configure-the-priority-boost-server-configuration-option.md) peut être utilisée pour augmenter la priorité des threads d'une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à 13. (priorité dite élevée). Cette valeur donne aux threads [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] une priorité plus élevée que la plupart des autres applications. Par conséquent, les threads [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auront plutôt tendance à être distribués chaque fois qu'ils sont prêts à être exécutés et ne seront pas devancés par les threads d'autres applications. Ceci peut améliorer les performances lorsqu'un serveur n'exécute que des instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et aucune autre application. Cependant, si une opération nécessitant beaucoup de mémoire se produit dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], les autres applications n'auront sans doute pas une priorité suffisamment élevée pour devancer le thread [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 

Si vous utilisez plusieurs instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un ordinateur et activez le renforcement de priorité pour certaines d'entre elles uniquement, les performances des instances exécutées avec une priorité normale peuvent être compromises. Les performances d’autres applications et composants sur le serveur peuvent aussi diminuer si l’option Renforcement de priorité est activée. C'est pourquoi elle doit être utilisée dans certaines conditions bien définies.

## <a name="hot-add-cpu"></a>Ajout d’un processeur à chaud
L'ajout d'un processeur à chaud est la capacité d'ajouter dynamiquement des processeurs à un système en cours d'exécution. L'ajout de processeurs peut s'effectuer physiquement en ajoutant du matériel, logiquement en partitionnant du matériel en ligne ou virtuellement par l'intermédiaire d'une couche de virtualisation. À compter de [!INCLUDE[ssKatmai](../includes/ssKatmai-md.md)], [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prend en charge l'ajout de processeurs à chaud.

Spécifications pour l'ajout de processeurs à chaud :  
* Nécessite un matériel prenant en charge l'ajout de processeurs à chaud.
* Nécessite l'édition 64 bits de Windows Server 2008 Datacenter ou le système d'exploitation Windows Server 2008 Enterprise Edition pour systèmes basés sur Itanium.
* Exige [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise.
* [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne peut pas être configuré pour utiliser la configuration NUMA logicielle. Pour plus d’informations sur la configuration NUMA logicielle, consultez [Soft-NUMA (SQL Server)](../database-engine/configure-windows/soft-numa-sql-server.md).

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne commence pas automatiquement à utiliser les processeurs une fois que ceux-ci ont été ajoutés. Cela empêche [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] d'utiliser des processeurs qui peuvent être ajoutés à d'autres fins. Après avoir ajouté des processeurs (UC), exécutez l'instruction [RECONFIGURE](../t-sql/language-elements/reconfigure-transact-sql.md) pour que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] reconnaisse les nouveaux processeurs comme des ressources disponibles.

> [!NOTE]
> Si le [masque d’affinité 64](../database-engine/configure-windows/affinity64-mask-server-configuration-option.md) est configuré, il doit être modifié pour utiliser les nouveaux processeurs.
 
## <a name="best-practices-for-running-sql-server-on-computers-that-have-more-than-64-cpus"></a>Recommandations pour l'exécution de SQL Server sur des ordinateurs comportant plus de 64 unités centrales

### <a name="assigning-hardware-threads-with-cpus"></a>Affectation de threads matériels avec des unités centrales
N’utilisez pas les options de configuration de serveur masque d’affinité (affinity mask) et masque d’affinité 64 (affinity64 mask) pour lier les processeurs à des threads spécifiques. Ces options sont limitées à 64 unités centrales. Utilisez l’option SET PROCESS AFFINITY de [ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md) à la place.

### <a name="managing-the-transaction-log-file-size"></a>Gestion de la taille du fichier journal des transactions
Ne comptez pas sur la croissance automatique pour augmenter la taille du fichier journal de transactions. L'augmentation du journal des transactions doit être un processus série. L’extension du journal peut empêcher la poursuite d’opérations d’écriture de transactions jusqu’à ce que l’extension du journal soit terminée. Pré-allouez plutôt l'espace des fichiers journaux en définissant leur taille avec une valeur suffisamment élevée pour prendre en charge la charge de travail habituelle de l'environnement.

### <a name="setting-max-degree-of-parallelism-for-index-operations"></a>Définition du degré maximal de parallélisme pour les opérations d'index
Les performances des opérations d'index telles que la création ou la reconstruction d'index peuvent être améliorées sur les ordinateurs qui possèdent de nombreuses unités centrales en définissant temporairement le mode de récupération de la base de données sur le mode de récupération simple ou de journalisation en bloc. Ces opérations d'index peuvent générer une activité de journal significative et les contentions de journal peuvent affecter le meilleur choix de degré de parallélisme (DOP) effectué par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

De plus, modifiez selon les besoins l’option de configuration serveur du **degré maximum de parallélisme (MAXDOP)** pour ces opérations. Les indications suivantes sont basées sur des tests internes et constituent des recommandations générales. Essayez plusieurs paramètres MAXDOP différents pour déterminer le paramètre optimal pour votre environnement.

* Pour le mode de récupération complète, limitez la valeur de l’option Degré maximal de parallélisme à huit ou une valeur inférieure.   
* Pour le modèle de journalisation en bloc ou le mode de récupération simple, essayez de définir la valeur de l’option Degré maximal de parallélisme sur une valeur supérieure à huit.   
* Pour les serveurs pour lesquels des nœuds NUMA sont configurés, le degré maximal de parallélisme ne doit pas dépasser le nombre d'unités centrales attribuées à chaque nœud NUMA. Cela vient du fait que la requête est plus susceptible d'utiliser la mémoire locale d'un nœud NUMA, ce qui peut améliorer le temps d'accès à la mémoire.  
* Sur les serveurs ou l’hyperthreading est activé et qui ont été fabriqués avant l’année 2009 incluse (c’est-à-dire avant l’amélioration de la fonctionnalité hyperthreading), la valeur MAXDOP ne doit pas dépasser le nombre de processeurs physiques plutôt que le nombre de processeurs logiques.

Pour plus d’informations sur l’option relative au degré maximal de parallélisme, consultez [Configurer l’option de configuration du serveur Degré maximal de parallélisme](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).

### <a name="setting-the-maximum-number-of-worker-threads"></a>Configuration du nombre maximal de threads de travail
Définissez toujours le nombre maximal de threads de travail avec une valeur supérieure à celle du paramètre de degré maximal de parallélisme. Le nombre de threads de travail doit toujours être défini sur une valeur équivalant à au moins sept fois le nombre d'unités centrales qui sont présentes sur le serveur. Pour plus d’informations, consultez [Configurer l’option max worker threads](../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md).

### <a name="using-sql-trace-and-sql-server-profiler"></a>Utilisation de Trace SQL et du Générateur de profils SQL
Nous vous recommandons de ne pas utiliser Trace SQL ni SQL Server Profiler dans un environnement de production. La surcharge induite par l'exécution de ces outils augmente également proportionnellement au nombre d'unités centrales. Si vous devez utiliser Trace SQL dans un environnement de production, limitez le nombre d'événements de trace au minimum. Profilez et testez avec soin chaque événement de trace sous charge et évitez d'utiliser des combinaisons d'événements qui affectent les performances de façon significative.

### <a name="setting-the-number-of-tempdb-data-files"></a>Définition du nombre de fichiers de données tempdb
En général, le nombre de fichiers de données tempdb doit correspondre au nombre d’unités centrales. Toutefois, en prenant soigneusement en compte les besoins de concurrence de tempdb, vous pouvez réduire la gestion de la base de données. Par exemple, si un système comporte 64 unités centrales et qu'habituellement seules 32 requêtes utilisent tempdb, l'augmentation du nombre de fichiers tempdb à 64 n'améliorera pas les performances.

### <a name="sql-server-components-that-can-use-more-than-64-cpus"></a>Composants SQL Server qui peuvent utiliser plus de 64 unités centrales
Le tableau suivant liste les composants [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et indique s'ils peuvent utiliser plus de 64 UC.

|Nom du processus   |Programme exécutable |Utilisation de plus de 64 unités centrales |  
|----------|----------|----------|  
|Moteur de base de données SQL Server |Sqlserver.exe  |Oui |  
|Reporting Services |Rs.exe |Non |  
|Analysis Services  |As.exe |Non |  
|Integration Services   |Is.exe |Non |  
|Service Broker |Sb.exe |Non |  
|Recherche en texte intégral   |Fts.exe    |Non |  
|SQL Server Agent   |Sqlagent.exe   |Non |  
|SQL Server Management Studio   |Ssms.exe   |Non |  
|Programme d'installation de SQL Server   |Setup.exe  |Non |  
