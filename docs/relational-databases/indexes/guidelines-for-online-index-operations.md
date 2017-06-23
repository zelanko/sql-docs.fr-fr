---
title: "Instructions pour les opérations d’index en ligne | Microsoft Docs"
ms.custom: 
ms.date: 04/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-indexes
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clustered indexes, online operations
- online index operations
- indexes [SQL Server], online operations
- disk space [SQL Server], indexes
- nonclustered indexes [SQL Server], online operations
- transaction logs [SQL Server], indexes
ms.assetid: d82942e0-4a86-4b34-a65f-9f143ebe85ce
caps.latest.revision: 64
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: cf2d74e423ab96af582d5f420065f9756e671ec2
ms.openlocfilehash: 508440b3e6cd15d4fb70f933c380e958dad74d56
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="guidelines-for-online-index-operations"></a>Instructions pour les opérations d'index en ligne
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Lorsque vous effectuez des opérations en ligne sur les index, les directives suivantes s'appliquent :  
  
-   Les index cluster doivent être créés, reconstruits ou supprimés hors connexion quand la table sous-jacente contient les types de données LOB (Large OBject) suivants : **image**, **ntext**et **text**.  
  
-   Les index non cluster non uniques peuvent être créés en ligne lorsque la table contient des types de données LOB, mais qu'aucune de ces colonnes n'est utilisée dans la définition de l'index en tant que colonne clé ou non-clé (incluse).  
  
-   Les index de tables temporaires locales ne peuvent pas être créés, reconstruits ou supprimés en ligne. Cette restriction ne s'applique pas aux index des tables temporaires globales.
- Les index peuvent être repris où il a été arrêtée après une défaillance inattendue, le basculement de la base de données, ou un **PAUSE** commande. Consultez [Alter Index](../../t-sql/statements/alter-index-transact-sql.md). Cette fonctionnalité est en version préliminaire publique pour SQL Server 2017.

> [!NOTE]  
>  Les opérations d’index en ligne ne sont pas disponibles dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 Le tableau suivant présente les opérations d’index réalisables en ligne, les index qui sont exclus de ces opérations en ligne et les restrictions d’index pouvant être reprises. Des restrictions supplémentaires sont également incluses.  
  
| Opération en ligne sur l'index | Index exclus | Autres restrictions |  
|----------------------------|----------------------|------------------------|  
|ALTER INDEX REBUILD|Index cluster désactivé ou vue indexée désactivée<br /><br /> Index XML<br /><br />Index columnstore <br /><br /> Index de table temporaire locale|Si le mot clé ALL est spécifié, l'opération peut échouer lorsque la table contient un index exclu.<br /><br /> Des restrictions supplémentaires s'appliquent pour la reconstruction d'index désactivés. Pour plus d’informations, consultez [Désactiver les index et contraintes](../../relational-databases/indexes/disable-indexes-and-constraints.md).|  
|CREATE INDEX|Index XML<br /><br /> Index cluster unique de départ sur une vue<br /><br /> Index de table temporaire locale||  
|CREATE INDEX WITH DROP_EXISTING|Index cluster désactivé ou vue indexée désactivée<br /><br /> Index de table temporaire locale<br /><br /> Index XML||  
|DROP INDEX|Index désactivés.<br /><br /> Index XML<br /><br /> Index non cluster<br /><br /> Index de table temporaire locale|Il n'est pas possible de spécifier plusieurs index dans une même instruction.|  
|ALTER TABLE ADD CONSTRAINT (PRIMARY KEY ou UNIQUE)|Index de table temporaire locale<br /><br /> Index cluster|Une seule sous-clause est autorisée à la fois. Par exemple, vous ne pouvez ni ajouter ni supprimer les contraintes PRIMARY KEY ou UNIQUE dans la même instruction ALTER TABLE.|  
|ALTER TABLE DROP CONSTRAINT (PRIMARY KEY ou UNIQUE)|Index cluster||  
  
 La table sous-jacente ne peut pas être modifiée, tronquée ou supprimée tant qu'une opération en ligne sur l'index est en cours.  
  
 Le paramètre de l'option online (ON ou OFF) spécifié lors de la création ou de la suppression d'un index cluster est appliqué à tous les index non cluster qui doivent être reconstruits. Par exemple, si l'index cluster est construit en ligne à l'aide de CREATE INDEX WITH DROP_EXISTING, ONLINE=ON, tous les index non cluster associés sont également recréés en ligne.  
  
 Lors de la création ou de la reconstruction d'un index UNIQUE en ligne, le générateur d'index et une transaction utilisateur simultanée peuvent tenter d'insérer la même clé, enfreignant ainsi la condition d'unicité. Si une ligne entrée par un utilisateur est insérée dans le nouvel index (cible) avant le déplacement de la ligne d'origine de la table source dans le nouvel index, l'opération en ligne sur l'index échoue.  
  
 Même si ce cas de figure est rare, l'opération en ligne sur l'index peut provoquer un blocage lorsqu'elle interagit avec les mises à jour de base de données en raison d'activités d'un utilisateur ou d'une application. Dans ces rares cas, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] sélectionne l'activité de l'utilisateur ou de l'application comme victime du blocage.  
  
 Vous pouvez exécuter sur les index des opérations DDL simultanées en ligne sur la même table ou sur la même vue uniquement lors de la création de plusieurs nouveaux index non cluster ou de la réorganisation d'index non cluster. Toutes les autres opérations en ligne sur les index exécutées en même temps échouent. Par exemple, vous ne pouvez pas créer un nouvel index en ligne tout en reconstruisant en ligne un index sur la même table.  
  
 Une opération en ligne ne peut pas être effectuée lorsqu'un index contient une colonne du type d'objet volumineux et qu'il existe, dans la même transaction, des opérations de mise à jour avant cette opération en ligne. Pour contourner ce problème, placez l'opération en ligne en dehors de la transaction ou avant les éventuelles mises à jour dans la transaction.  
  
## <a name="disk-space-considerations"></a>Considérations relatives à l'espace disque  
 Les opérations d’index en ligne nécessitent davantage d’espace disque que les opérations d’index hors connexion. 
 - Lors des opérations de création et de reconstruction d’index, de l’espace additionnel est requis pour pouvoir créer (ou reconstruire) l’index. 
 - De plus, de l’espace disque est requis pour l’index de mappage temporaire. Cet index temporaire est utilisé dans les opérations en ligne sur les index qui créent, reconstruisent ou suppriment un index cluster.
- La suppression d’un index cluster en ligne nécessite autant d’espace que la création (ou la reconstruction) d’un index cluster en ligne. 

Pour plus d’informations, consultez [Disk Space Requirements for Index DDL Operations](../../relational-databases/indexes/disk-space-requirements-for-index-ddl-operations.md).  
  
## <a name="performance-considerations"></a>Considérations relatives aux performances  
 Même si les opérations en ligne sur les index autorisent une activité de mise à jour utilisateur simultanée, elles durent plus longtemps si l'activité de mise à jour est très lourde. En général, les opérations en ligne sur les index sont plus lentes que leurs équivalents hors connexion, quel que soit le niveau d'activité de mise à jour.  
  
 Comme les structures source et cible sont conservées pendant l'opération en ligne sur l'index, l'utilisation des ressources pour les transactions d'insertion, de mise à jour et de suppression peuvent augmenter jusqu'à doubler. Il pourrait s'ensuivre une dégradation des performances et une utilisation plus intense des ressources, en particulier du temps processeur, pendant l'opération d'index. Les opérations en ligne sur les index sont intégralement enregistrées dans le journal.  
  
 Même si les opérations en ligne sont préférables, vous devez évaluer votre environnement et les conditions spécifiques requises. Il peut être plus approprié d'exécuter hors connexion des opérations sur les index. Ce faisant, les utilisateurs disposent d'un accès restreint aux données pendant l'opération, mais l'opération est réalisée plus vite et consomme moins de ressources.  
  
 Sur les ordinateurs multiprocesseurs qui exécutent SQL Server 2016, les instructions d’index peuvent, à l’instar d’autres requêtes, utiliser davantage de processeurs pour réaliser les opérations d’analyse et de tri associées à l’instruction d’index. Vous pouvez utiliser l'option d'index MAXDOP pour contrôler le nombre de processeurs dédiés à l'opération d'index en ligne. De cette manière, vous pouvez équilibrer les ressources utilisées par l'opération d'index avec celles des utilisateurs simultanés. Pour plus d’informations, consultez [Configurer des opérations d’index parallèles](../../relational-databases/indexes/configure-parallel-index-operations.md). Pour plus d’informations sur les éditions de SQL Server qui prennent en charge les opérations d’index parallèles, consultez [Fonctionnalités prises en charge par les éditions](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 Du fait qu'un verrou S ou Sch-M lock est conservé dans la phase finale de l'opération sur un index, soyez prudent lorsque vous exécutez une opération en ligne sur un index dans une transaction utilisateur explicite, telle qu'un blocage BEGIN TRANSACTION...COMMIT. Cette action maintient le verrou jusqu'à la fin de la transaction, gênant ainsi l'accès concurrentiel des utilisateurs.  
  
 La reconstruction d'index en ligne peut augmenter la fragmentation lorsqu'elle est autorisée à s'exécuter avec les options `MAX DOP > 1` et `ALLOW_PAGE_LOCKS = OFF` . Pour plus d’informations, consultez [Fonctionnement : La reconstruction d’index en ligne peut entraîner une fragmentation accrue](http://blogs.msdn.com/b/psssql/archive/2012/09/05/how-it-works-online-index-rebuild-can-cause-increased-fragmentation.aspx).  
  
## <a name="transaction-log-considerations"></a>Considérations relatives aux journaux de transactions  
 Les opérations d'index à grande échelle, réalisées hors connexion ou en ligne, peuvent générer de fortes charges de données susceptibles de remplir rapidement le journal de transactions. Pour garantir que l'opération d'index peut être restaurée, le journal des transactions ne doit pas être tronqué tant que l'opération d'index n'est pas terminée ; toutefois, le journal peut être sauvegardé pendant l'opération d'index. Par conséquent, le journal des transactions doit disposer d'un espace suffisant pour stocker les transactions des opérations d'index et les éventuelles transactions utilisateur simultanées pendant la durée de l'opération d'index. Pour plus d’informations, consultez [Espace disque du journal des transactions pour les opérations d’index](../../relational-databases/indexes/transaction-log-disk-space-for-index-operations.md).  

## <a name="resumable-index-rebuild-considerations"></a>Considérations relatives à la reconstruction d’Index pouvant être reprises

> [!NOTE]
> Consultez [Alter Index](../../t-sql/statements/alter-index-transact-sql.md). Cette fonctionnalité est en version préliminaire publique pour SQL Server 2017.
>

Lorsque vous effectuez la reconstruction d’index en ligne peut être repris les indications suivantes s’appliquent :
-   La gestion, planification et l’extension des fenêtres de maintenance d’index. Vous pouvez suspendre et redémarrer une opération de reconstruction d’index plusieurs fois en fonction de vos fenêtres de maintenance.
- Récupération à partir d’échecs de reconstruction d’index (par exemple, les basculements de base de données ou manque d’espace disque).
- Lorsqu’une opération d’index est en pause, à la fois l’index d’origine et celui qui vient d’être créé nécessitent l’espace disque et doivent être mis à jour au cours des opérations DML.

- Permet la troncation des journaux de troncation pendant une opération de reconstruction d’index (cette opération ne peut pas être effectuée pour une opération d’index en ligne normal).
- SORT_IN_TEMPDB = ON option n’est pas prise en charge.

> [!IMPORTANT]
> Rebuild peut être repris ne nécessite pas vous permet de maintenir une troncation longue, ce qui permet la troncation du journal au cours de cette opération et une meilleure gestion de l’espace journal. Avec la nouvelle conception, nous managé conserver les données nécessaires dans une base de données ainsi que toutes les références requises pour redémarrer l’opération peut être reprise.
>

En règle générale, il n’existe aucune différence de performances entre la reconstruction d’index en ligne de reprise et sans reprise possible. Lorsque vous mettez à jour un index peut être repris lors de la reconstruction d’un index est interrompue :
- Pour en lecture principalement les charges de travail, l’impact sur les performances est insignifiante. 
- Pour les charges de travail à nombre élevé de mise à jour, vous pouvez rencontrer une baisse de débit (notre test montre inférieure à 10 % de dégradation).

En règle générale, il n’existe aucune différence de qualité de défragmentation entre la reconstruction d’index en ligne de reprise et sans reprise possible.
 
## <a name="related-content"></a>Contenu associé  
 [Fonctionnement des opérations d’index en ligne](../../relational-databases/indexes/how-online-index-operations-work.md)  
  
 [Exécuter des opérations en ligne sur les index](../../relational-databases/indexes/perform-index-operations-online.md)  
  
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)  
  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
  
  

