---
title: Afficher les informations relatives aux conflits pour les Publications de fusion (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- sp_helpmergeconflictrows
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
- sp_helpmergearticleconflicts
ms.assetid: 4907fe35-10ee-4f81-b924-fc419b1864d2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f0f36e74462b8237a3661748d137f67d3bad13ea
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194279"
---
# <a name="view-conflict-information-for-merge-publications-replication-transact-sql-programming"></a>Afficher les informations relatives aux conflits pour les publications de fusion (programmation Transact-SQL de la réplication)
  Lorsqu'un conflit est résolu dans une réplication de fusion, les données de la ligne perdante sont écrites dans une table de conflits. Ces données peuvent être affichées par programme en utilisant des procédures stockées de réplication. Pour plus d’informations, consultez [Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
### <a name="to-view-conflict-information-and-losing-row-data-for-all-types-of-conflicts"></a>Pour afficher les informations relatives au conflit et les données de ligne perdante pour tous les types de conflits  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql). Notez les valeurs des colonnes suivantes dans le jeu de résultats :  
  
    -   **centralized_conflicts** - 1 indique que les lignes présentant des conflits sont stockées sur le serveur de publication, et 0 indique que les lignes présentant des conflits ne sont pas stockées sur le serveur de publication.  
  
    -   **decentralized_conflicts** - 1 indique que les lignes présentant des conflits sont stockées sur l'Abonné, et 0 indique que les lignes présentant des conflits ne sont pas stockées sur l'Abonné.  
  
        > [!NOTE]  
        >  Le comportement de journalisation des conflits d'une publication de fusion est défini à l'aide du paramètre **@conflict_logging** de [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). L'utilisation du paramètre **@centralized_conflicts** est déconseillée.  
  
     Le tableau suivant décrit les valeurs de ces colonnes en fonction de la valeur spécifiée pour **@conflict_logging**.  
  
    |Valeur @conflict_logging|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |`publisher`|1|0|  
    |`subscriber`|0|1|  
    |`both`|1|1|  
  
2.  Dans la base de données de publication sur le serveur de publication ou dans la base de données d'abonnement de l'Abonné, exécutez [sp_helpmergearticleconflicts](/sql/relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql). Affectez une valeur à **@publication** afin de retourner uniquement des informations sur les conflits pour les articles qui appartiennent à une publication spécifique. Des informations sur les tables de conflits sont alors retournées pour les articles présentant des conflits. Notez la valeur de **conflict_table** pour tout article qui vous intéresse. Si la valeur de **conflict_table** d'un article est NULL, seuls des conflits de suppression se sont produits dans cet article.  
  
3.  (Facultatif) Examinez les lignes présentant des conflits pour les articles qui vous intéressent. Selon la valeur de **centralized_conflicts** et **decentralized_conflicts** obtenues à l'étape 1, effectuez l'une des opérations suivantes :  
  
    -   Dans la base de données de publication sur le serveur de publication, exécutez [sp_helpmergeconflictrows](/sql/relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql). Spécifiez une table de conflits pour l'article (obtenue à l'étape 1) pour **@conflict_table**. (Facultatif) Spécifiez une valeur pour **@publication** afin de limiter à une publication spécifique les informations sur les conflits retournées. Des données de ligne et autres informations sur la ligne perdante sont alors retournées.  
  
    -   Dans la base de données d'abonnement de l'Abonné, exécutez [sp_helpmergeconflictrows](/sql/relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql). Spécifiez une table de conflits pour l'article (obtenue à l'étape 1) pour **@conflict_table**. Des données de ligne et autres informations sur la ligne perdante sont alors retournées.  
  
### <a name="to-view-information-only-on-conflicts-where-the-delete-failed"></a>Pour afficher des informations uniquement sur les conflits avec échec de suppression  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql). Notez les valeurs des colonnes suivantes dans le jeu de résultats :  
  
    -   **centralized_conflicts** - 1 indique que les lignes présentant des conflits sont stockées sur le serveur de publication, et 0 indique que les lignes présentant des conflits ne sont pas stockées sur le serveur de publication.  
  
    -   **decentralized_conflicts** - 1 indique que les lignes présentant des conflits sont stockées sur l'Abonné, et 0 indique que les lignes présentant des conflits ne sont pas stockées sur l'Abonné.  
  
        > [!NOTE]  
        >  Le comportement de journalisation des conflits d'une publication de fusion est défini à l'aide du paramètre **@conflict_logging** de [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). L'utilisation du paramètre **@centralized_conflicts** est déconseillée.  
  
2.  Dans la base de données de publication sur le serveur de publication ou dans la base de données d'abonnement de l'Abonné, exécutez [sp_helpmergearticleconflicts](/sql/relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql). Affectez une valeur à **@publication** afin de retourner uniquement des informations sur les tables de conflits pour les articles qui appartiennent à une publication spécifique. Des informations sur les tables de conflits sont alors retournées pour les articles présentant des conflits. Notez la valeur de **source_object** pour tout article qui vous intéresse. Si la valeur de **conflict_table** d'un article est NULL, seuls des conflits de suppression se sont produits dans cet article.  
  
3.  (Facultatif) Examinez les informations sur les conflits pour les conflits de suppression. Selon la valeur de **centralized_conflicts** et **decentralized_conflicts** obtenues à l'étape 1, effectuez l'une des opérations suivantes :  
  
    -   Dans la base de données de publication sur le serveur de publication, exécutez [sp_helpmergedeleteconflictrows](/sql/relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql). Spécifiez le nom de la table source (obtenue à l'étape 1) sur laquelle le conflit s'est produit pour **@source_object**. (Facultatif) Spécifiez une valeur pour **@publication** afin de limiter à une publication spécifique les informations sur les conflits retournées. Les informations sur les conflits de suppression stockées sur le serveur de publication sont alors retournées.  
  
    -   Dans la base de données d'abonnement de l'Abonné, exécutez [sp_helpmergedeleteconflictrows](/sql/relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql). Spécifiez le nom de la table source (obtenue à l'étape 1) sur laquelle le conflit s'est produit pour **@source_object**. (Facultatif) Spécifiez une valeur pour **@publication** afin de limiter à une publication spécifique les informations sur les conflits retournées. Les informations sur les conflits de suppression stockées sur l'Abonné sont alors retournées.  
  
## <a name="see-also"></a>Voir aussi  
 [Détection et résolution des conflits de réplication de fusion avancée](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
