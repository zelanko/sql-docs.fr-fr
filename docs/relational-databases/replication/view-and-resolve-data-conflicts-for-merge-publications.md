---
title: Afficher et résoudre les conflits de données pour les publications de fusion | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db445d9c80c6a6e2552160dcff721c06d5c107e6
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72907786"
---
# <a name="conflict-resolution-for-merge-replication"></a>Résolution de conflit pour la réplication de fusion
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Les conflits de réplication de fusion sont résolus en fonction de l'outil de résolution spécifié pour chaque article. Par défaut, les conflits sont résolus sans que l'utilisateur doive intervenir. Mais il est possible de les afficher et de modifier le résultat de la résolution dans la Visionneuse des conflits de réplication de [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
 Les données de conflit sont disponibles dans la Visionneuse des conflits de réplication pendant la durée définie comme période de rétention des conflits (par défaut 14 jours). Pour définir la période de rétention des conflits :  
  
-   Spécifiez une valeur de conservation pour le paramètre `@conflict_retention` de [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).  
  
-   Spécifiez la valeur **conflict_retention** pour le paramètre `@property` et une valeur de conservation pour le paramètre `@value` de [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 Par défaut, les informations sur les conflits sont stockées dans les emplacements suivants :    
-   Sur le serveur de publication et sur l'Abonné, si le niveau de compatibilité est égal ou supérieur à 90RTM.   
-   Sur le serveur de publication, si le niveau de compatibilité est inférieur à 80RTM.   
-   Sur le serveur de publication si les Abonnées exécutent [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Les données conflictuelles ne peuvent pas être stockées sur les Abonnés [!INCLUDE[ssEW](../../includes/ssew-md.md)] .  
  
 Le stockage des informations de conflits est contrôlé par la propriété de publication **conflict_logging** . Pour plus d’informations, consultez [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) et [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 Il est également possible de résoudre les conflits de façon interactive au cours de la synchronisation à l'aide du programme de résolution interactif [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Le résolveur interactif est disponible via le Gestionnaire de synchronisation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Pour plus d’informations, consultez [Synchroniser un abonnement à l’aide du Gestionnaire de synchronisation Windows &#40;Gestionnaire de synchronisation Windows&#41;](../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
## <a name="resolve-conflicts"></a>Résoudre les conflits  
  
1.  Connectez-vous au serveur de publication (ou à l'Abonné, le cas échéant) dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Cliquez avec le bouton droit sur la publication dont vous souhaitez afficher les conflits puis cliquez sur **Afficher les conflits**.  
  
    > [!NOTE]  
    >  Si vous spécifiez une valeur **'subscriber'** pour la propriété **conflict_logging** , l'option de menu **Afficher les conflits** n'est pas disponible. Pour afficher les conflits, démarrez ConflictViewer.exe à partir de l'invite de commandes. Par défaut, ConflictViewer.exe est disponible dans le répertoire suivant : Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE. Pour obtenir la liste des paramètres de démarrage valides, exécutez ConflictViewer.exe -?.  
  
4.  Dans la boîte de dialogue **Sélectionner la table de conflits** , sélectionnez une base de données et une table dont il faut afficher les conflits.  
  
5.  Dans la Visionneuse des conflits de réplication, vous pouvez effectuer les actions suivantes :  
  
    -   Filtrer des lignes avec les boutons situés à droite de la grille supérieure.  
  
    -   Sélectionner une ligne dans la grille supérieure pour afficher des informations sur cette ligne dans la grille inférieure.  
  
    -   Sélectionner une ou plusieurs lignes dans la grille supérieure puis cliquer sur **Supprimer**, ce qui équivaut à cliquer sur le bouton **Soumettre le gagnant** (sans modifier les données).  
  
    -   Cliquer sur le bouton des propriétés ( **...** ) pour afficher des informations plus détaillées sur une colonne concernée par un conflit.  
  
    -   Modifier des données dans la colonne **Gagnant du conflit** ou **Perdant du conflit** avant de soumettre les données (les données sont en lecture seule si la colonne est grisée).  
  
    -   Cliquer sur **Soumettre le gagnant** pour accepter la ligne désignée comme gagnante du conflit.  
  
    -   Cliquer sur **Soumettre le perdant** pour substituer la résolution et propager la valeur désignée comme perdante du conflit à tous les nœuds de la topologie.  
  
    -   Sélectionner l'option **Consigner les détails de ce conflit** pour enregistrer les données de conflit dans un journal. Pour spécifier l'emplacement du fichier, pointez sur le menu **Affichage** puis cliquez sur **Options**. Entrez une valeur ou cliquez sur le bouton Parcourir ( **...** ) pour accéder au fichier approprié. Cliquez sur **OK** pour fermer la boîte de dialogue **Options** .  
  
6.  Fermer la Visionneuse des conflits de réplication.  

## <a name="view-conflict-information"></a>Afficher les informations de conflit
Lorsqu'un conflit est résolu dans une réplication de fusion, les données de la ligne perdante sont écrites dans une table de conflits. Ces données peuvent être affichées par programme en utilisant des procédures stockées de réplication. Pour plus d’informations, consultez [Détection et résolution avancées des conflits de réplication de fusion](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md). Notez les valeurs des colonnes suivantes dans le jeu de résultats :  
  
    -   **centralized_conflicts** - 1 indique que les lignes présentant des conflits sont stockées sur le serveur de publication, et 0 indique que les lignes présentant des conflits ne sont pas stockées sur le serveur de publication.  
  
    -   **decentralized_conflicts** - 1 indique que les lignes présentant des conflits sont stockées sur l'Abonné, et 0 indique que les lignes présentant des conflits ne sont pas stockées sur l'Abonné.  
  
        > [!NOTE]  
        >  Le comportement de journalisation des conflits d’une publication de fusion est défini à l’aide du paramètre `@conflict_logging` de [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). L’utilisation du paramètre `@centralized_conflicts` est dépréciée.  
  
     Le tableau suivant décrit les valeurs de ces colonnes en fonction de la valeur spécifiée pour `@conflict_logging`.  
  
    |Valeur @conflict_logging|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |**publisher** (serveur de publication)|1|0|  
    |**subscriber** (Abonné)|0|1|  
    |**both** (les deux)|1|1|  
  
2.  Dans la base de données de publication sur le serveur de publication ou dans la base de données d'abonnement de l'Abonné, exécutez [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md). Affectez une valeur à `@publication` afin de retourner uniquement des informations sur les conflits pour les articles qui appartiennent à une publication spécifique. Des informations sur les tables de conflits sont alors retournées pour les articles présentant des conflits. Notez la valeur de **conflict_table** pour tout article qui vous intéresse. Si la valeur de **conflict_table** d'un article est NULL, seuls des conflits de suppression se sont produits dans cet article.  
  
3.  (Facultatif) Examinez les lignes présentant des conflits pour les articles qui vous intéressent. Selon la valeur de **centralized_conflicts** et **decentralized_conflicts** obtenues à l'étape 1, effectuez l'une des opérations suivantes :  
  
    -   Dans la base de données de publication sur le serveur de publication, exécutez [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Spécifiez une table de conflits pour l’article (obtenue à l’étape 1) pour `@conflict_table`. (Facultatif) Spécifiez une valeur pour `@publication` afin de retourner uniquement les informations sur les conflits qui concernent une publication spécifique. Des données de ligne et autres informations sur la ligne perdante sont alors retournées.  
  
    -   Dans la base de données d'abonnement de l'Abonné, exécutez [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md). Spécifiez une table de conflits pour l’article (obtenue à l’étape 1) pour `@conflict_table`. Des données de ligne et autres informations sur la ligne perdante sont alors retournées.  
  
## <a name="conflict-where-delete-failed"></a>Conflit où la suppression a échoué   
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md). Notez les valeurs des colonnes suivantes dans le jeu de résultats :  
  
    -   **centralized_conflicts** - 1 indique que les lignes présentant des conflits sont stockées sur le serveur de publication, et 0 indique que les lignes présentant des conflits ne sont pas stockées sur le serveur de publication.  
  
    -   **decentralized_conflicts** - 1 indique que les lignes présentant des conflits sont stockées sur l'Abonné, et 0 indique que les lignes présentant des conflits ne sont pas stockées sur l'Abonné.  
  
        > [!NOTE]  
        >  Le comportement de journalisation des conflits d’une publication de fusion est défini à l’aide du paramètre `@conflict_logging` de [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). L’utilisation du paramètre `@centralized_conflicts` est dépréciée.  
  
2.  Dans la base de données de publication sur le serveur de publication ou dans la base de données d'abonnement de l'Abonné, exécutez [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md). Spécifiez une valeur pour `@publication` afin de retourner uniquement des informations sur les tables de conflits pour les articles qui appartiennent à une publication spécifique. Des informations sur les tables de conflits sont alors retournées pour les articles présentant des conflits. Notez la valeur de **source_object** pour tout article qui vous intéresse. Si la valeur de **conflict_table** d'un article est NULL, seuls des conflits de suppression se sont produits dans cet article.  
  
3.  (Facultatif) Examinez les informations sur les conflits pour les conflits de suppression. Selon la valeur de **centralized_conflicts** et **decentralized_conflicts** obtenues à l'étape 1, effectuez l'une des opérations suivantes :  
  
    -   Dans la base de données de publication sur le serveur de publication, exécutez [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Spécifiez le nom de la table source (obtenue à l’étape 1) sur laquelle le conflit s’est produit pour `@source_object`. (Facultatif) Spécifiez une valeur pour `@publication` afin de retourner uniquement les informations sur les conflits qui concernent une publication spécifique. Les informations sur les conflits de suppression stockées sur le serveur de publication sont alors retournées.  
  
    -   Dans la base de données d'abonnement de l'Abonné, exécutez [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md). Spécifiez le nom de la table source (obtenue à l’étape 1) sur laquelle le conflit s’est produit pour `@source_object`. (Facultatif) Spécifiez une valeur pour `@publication` afin de retourner uniquement les informations sur les conflits qui concernent une publication spécifique. Les informations sur les conflits de suppression stockées sur l'Abonné sont alors retournées.  
  
## <a name="see-also"></a>Voir aussi  
 [Détection et résolution des conflits de réplication de fusion avancée](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Spécifier un programme de résolution d’articles de fusion](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)  
  
  
