---
title: Introduction aux tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ef1cc7de-63be-4fa3-a622-6d93b440e3ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff434efd0a9f4fcb3316143e598e636bff85f487
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358201"
---
# <a name="introduction-to-memory-optimized-tables"></a>Introduction aux tables optimisées en mémoire
  Les tables optimisées en mémoire sont des tables créées à l’aide de [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).  
  
 Les tables optimisés en mémoire résident en mémoire. Les lignes de la table sont lues et écrites dans la mémoire. L'ensemble de la table réside dans la mémoire. Une deuxième copie des données de la table est conservée sur le disque, mais uniquement pour la durabilité.  
  
 L'OLTP en mémoire est intégré à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour offrir une expérience transparente dans tous les domaines, tels que le développement, le déploiement, la gestion et la prise en charge. Une base de données peut contenir des objets en mémoire et sur disque.  
  
 Les lignes des tables optimisées en mémoire ont un contrôle de version. Cela signifie que chaque ligne de la table a potentiellement plusieurs versions. Toutes les versions de ligne sont conservées dans la même structure de données de la table. Le contrôle de version de ligne est utilisé pour autoriser les lectures et les écritures simultanées sur la même ligne. Pour plus d'informations sur les lectures et les écritures simultanées sur la même ligne, consultez [Transactions in Memory-Optimized Tables](memory-optimized-tables.md).  
  
 La figure ci-dessous illustre les contrôles de version multiples. Elle représente une table de trois lignes ayant chacune plusieurs versions.  
  
 ![Multi-versioning.](../../database-engine/media/hekaton-tables-1.gif "Multi-versioning.")  
  
 La table a trois lignes : r1, r2 et r3. r1 a trois versions, r2 a deux versions, et r3 a quatre versions. Notez que les différentes versions de la même ligne n'occupent pas nécessairement des emplacements de mémoire consécutifs. Les différentes versions de ligne peuvent être dispersées dans l'ensemble de la structure de données de la table.  
  
 La structure de données des tables optimisées en mémoire peut être considérée comme une collection de versions de ligne. Les lignes d'une table sur disque sont organisées dans des pages et des extensions, et les lignes individuelles sont traitées sur la base du numéro et du décalage de la page, les versions de ligne dans les tables optimisées en mémoire sont traitées à l'aide de pointeurs de mémoire à huit octets.  
  
## <a name="durability"></a>Durabilité  
 Les tables optimisées en mémoire sont durables par défaut, et tout comme les transactions sur des tables sur disque (traditionnelles), les transactions durables sur les tables optimisées en mémoire présentent toutes les propriétés ACID (atomicité, cohérence, isolation et durabilité). Les tables optimisées en mémoire et les procédures stockées compilées en mode natif prennent en charge un sous-ensemble de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 L'OLTP en mémoire prend en charge les tables durables avec durabilité retardée des transactions. Les transactions durables retardées sont enregistrées sur disque peu après la validation de la transaction. En revanche, les transactions validées qui n'ont pas été enregistrées sur le disque sont perdues en cas de défaillance ou de basculement du serveur.  
  
 Outre les tables optimisées en mémoire durables par défaut, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend également en charge les tables optimisées en mémoire non durables, qui ne sont pas enregistrées et dont les données ne sont pas rendues persistantes sur disque. Cela signifie que les transactions sur ces tables ne nécessitent aucune E/S disque, mais que les données ne sont pas récupérées suite à un incident ou à une défaillance du serveur.  
  
## <a name="accessing-data-in-memory-optimized-tables"></a>Accès aux données des tables optimisées en mémoire  
 Les données des tables optimisées en mémoire sont accessibles de deux manières :  
  
-   Via le [!INCLUDE[tsql](../../../includes/tsql-md.md)] interprété (en dehors d'une procédure stockée compilée en mode natif). Ces instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] peuvent être dans des procédures stockées interprétées ou des instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] ad hoc.  
  
-   Via des procédures stockées compilées en mode natif.  
  
 Les tables optimisées en mémoire sont plus efficacement accessibles à partir des procédures stockées compilées en mode natif ([Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md)). Elles peuvent également être accédées via du [!INCLUDE[tsql](../../../includes/tsql-md.md)]traditionnel et interprète. Le terme [!INCLUDE[tsql](../../../includes/tsql-md.md)] interprété fait référence à l'accès aux tables optimisées en mémoire sans procédure stockée compilée en mode natif. Parmi les exemples d'accès en [!INCLUDE[tsql](../../../includes/tsql-md.md)] interprété figure l'accès à une table optimisée en mémoire à partir d'un déclencheur DML ou d'un traitement, d'une vue ou d'une fonction table [!INCLUDE[tsql](../../../includes/tsql-md.md)] ad hoc.  
  
 Le tableau suivant résume l'accès natif et l'accès en [!INCLUDE[tsql](../../../includes/tsql-md.md)] interprété pour différents objets.  
  
|Fonctionnalité|Accès à l'aide d'une procédure stockée compilée en mode natif|Accès en [!INCLUDE[tsql](../../../includes/tsql-md.md)] interprété|Accès CLR|  
|-------------|-------------------------------------------------------|-------------------------------------------|----------------|  
|Tables optimisées en mémoire|Oui|Oui|Non <sup>1</sup>|  
|[Variables de table optimisée en mémoire](../../database-engine/memory-optimized-table-variables.md)|Oui|Oui|Non|  
|[Procédures stockées compilées en mode natif](https://msdn.microsoft.com/library/dn133184.aspx)|Vous ne pouvez pas utiliser l'instruction EXECUTE pour exécuter une procédure stockée à partir d'une procédure stockée compilée en mode natif.|Oui|Non <sup>1</sup>|  
  
 <sup>1</sup> vous ne peut pas accéder à une table mémoire optimisée ou une procédure stockée compilée en mode natif à partir de la connexion contextuelle (la connexion à partir de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lors de l’exécution d’un module CLR). Cependant, vous pouvez créer et ouvrir une autre connexion à partir de laquelle vous accédez aux tables optimisées en mémoire et aux procédures stockées compilées en mode natif. Pour plus d’informations, consultez [vs régulières. Connexions contextuelles](../clr-integration/data-access/context-connections-vs-regular-connections.md).  
  
## <a name="performance-and-scalability"></a>Performances et extensibilité  
 Les facteurs suivants affectent les gains de performance pouvant être obtenus avec l'OLTP en mémoire :  
  
 Communication  
 Une application comportant de nombreux appels à des procédures stockées courtes aura un moindre gain de performances par rapport à une application comportant moins d'appels et plus de fonctionnalités implémentées dans chaque procédure stockée.  
  
 Exécution [!INCLUDE[tsql](../../../includes/tsql-md.md)]  
 L'OLTP en mémoire offre des performances optimales si vous utilisez des procédures stockées compilées en mode natif plutôt que des procédures stockées interprétées ou l'exécution de requêtes. Les procédures stockées qui exécutent d'autres procédures stockées ne peuvent pas être compilées en mode natif, mais elles sont avantageuses pour l'accès aux tables optimisées en mémoire.  
  
 Comparaison entre l'analyse de plage et la recherche de points  
 Les index non cluster mémoire optimisés prennent en charge les analyses de plage et les analyses triées. Pour les recherches de points, les index de hachage mémoire optimisés offrent de meilleures performances que les index non cluster mémoire optimisés. Les index non cluster mémoire optimisés offrent de meilleures performances que les index sur disque.  
  
 Les opérations d'index ne sont pas stockées et existent uniquement en mémoire.  
  
 Accès concurrentiel  
 Pour les applications dont les performances sont affectées par l'accès simultané au niveau du moteur, tel que la contention de verrous internes ou le blocage, les performances s'améliorent de façon significative lorsque l'application passe à l'OLTP en mémoire.  
  
 Le tableau suivant répertorie les problèmes de performance et d'extensibilité couramment rencontrés dans les bases de données relationnelles et indique comment l'OLTP peut améliorer les performances.  
  
|Problème|Impact sur l'OLTP en mémoire|  
|-----------|----------------------------|  
|Performances<br /><br /> Utilisation importante des ressources (UC, E/S, réseau ou mémoire).|Unité centrale<br /> Les procédures stockées compilées en mode natif peuvent réduire de façon significative l'utilisation de l'UC, car elles nécessitent moins d'instructions pour exécuter une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] que les procédures stockées interprétées.<br /><br /> L'OLTP en mémoire peut vous aider à réduire l'investissement en matériel dans des charges de travail avec montée en puissance parallèle, car un serveur peut assurer à lui seul le débit de cinq à dix serveurs.<br /><br /> E/S<br /> Si vous observez un goulot d'étranglement des E/S à partir du traitement des données ou des pages d'index, l'OLTP en mémoire peut l'atténuer. En outre, les points de contrôle des objets OLTP en mémoire sont continus et n'entraînent pas une hausse soudaine des opérations d'E/S. Toutefois, si la plage de travail des tables critiques pour les performances ne tient pas en mémoire, l'OLTP en mémoire n'améliore pas les performances, car il nécessite que les données résident en mémoire. Si vous observez un goulot d'étranglement des E/S lors de la journalisation, l'OLTP en mémoire l'atténue, car il nécessite moins d'opérations de journalisation. Si une ou plusieurs tables optimisées en mémoire sont configurées en tant que tables non durables, supprimez la journalisation des données.<br /><br /> Mémoire<br /> L'OLTP en mémoire ne procure aucun gain de performance. Il peut en effet solliciter davantage la mémoire, car les objets doivent résider en mémoire.<br /><br /> Réseau<br /> L'OLTP en mémoire ne procure aucun gain de performance. Les données doivent être communiquées de la couche Données à la couche Application.|  
|Extensibilité<br /><br /> La plupart des problèmes de mise à l'échelle dans les applications [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sont dus à des problèmes d'accès concurrentiel tels que la contention dans les verrous, les verrous internes et les verrouillages tournants.|Contention de verrous internes<br /> Un scénario typique est la contention dans la dernière page d'un index lors de l'insertion simultanée de lignes dans l'ordre des clés. Étant donné que l'OLTP en mémoire ne prend pas de verrou interne lors de l'accès aux données, il n'y a plus de problèmes d'extensibilité liés à la contention de verrous internes.<br /><br /> Contention de verrouillage tournant<br /> Étant donné que l'OLTP en mémoire ne prend pas de verrou interne lors de l'accès aux données, il n'y a plus de problèmes d'extensibilité liés à la contention de verrouillage tournant.<br /><br /> Contention liée au verrouillage<br /> Si votre application de base de données rencontre des problèmes de blocage entre les opérations de lecture et d'écriture, l'OLTP en mémoire les supprime, car il utilise une nouvelle forme de contrôle d'accès concurrentiel optimiste pour implémenter tous les niveaux d'isolation des transactions. L'OLTP en mémoire n'utilise pas TempDB pour stocker les versions de ligne.<br /><br /> Si le problème de mise à l'échelle est provoqué par un conflit entre deux opérations d'écriture, telles que deux transactions simultanées tentant de mettre à jour la même ligne, l'OLTP en mémoire laisse une transaction aboutir et fait échouer l'autre. La transaction en échec doit être retentée par un nouvel envoi explicite ou implicite. Dans les deux cas, vous devez apporter des modifications à l'application.<br /><br /> Si votre application crée des conflits fréquents entre deux opérations d'écriture, la valeur du verrouillage optimiste est diminuée. L'application ne convient pas pour l'OLTP en mémoire. La plupart des applications OLTP ne connaissent pas de conflits d’écriture à moins que le conflit ne soit induit par une escalade de verrous.|  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](in-memory-oltp-in-memory-optimization.md)  
  
  
