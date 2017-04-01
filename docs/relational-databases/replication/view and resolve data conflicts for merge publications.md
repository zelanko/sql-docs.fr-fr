---
title: "afficher et r&#233;soudre les conflits de donn&#233;es pour les publications de fusion (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "résolution des conflits de réplication de fusion [réplication SQL Server], affichage des conflits"
  - "affichage des informations sur les conflits"
  - "résolution des conflits [réplication SQL Server], réplication de fusion"
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# afficher et r&#233;soudre les conflits de donn&#233;es pour les publications de fusion (SQL Server Management Studio)
  Les conflits de réplication de fusion sont résolus en fonction de l'outil de résolution spécifié pour chaque article. Par défaut, les conflits sont résolus sans que l'utilisateur doive intervenir. Mais il est possible de les afficher et de modifier le résultat de la résolution dans l'outil de résolution des conflits de réplication de [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
 Les données de conflit sont disponibles dans cet outil pendant la durée définie comme période de rétention des conflits (par défaut 14 jours). Pour définir la période de rétention des conflits :  
  
-   Spécifiez une valeur de rétention pour le **@conflict_retention** paramètre de [sp_addmergepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).  
  
-   Spécifiez la valeur **conflict_retention** pour la **@property** valeur de paramètre et une durée de rétention pour le **@value** paramètre de [sp_changemergepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 Par défaut, les informations sur les conflits sont stockées dans les emplacements suivants :  
  
-   Sur le serveur de publication et sur l'Abonné, si le niveau de compatibilité est égal ou supérieur à 90RTM.  
  
-   Sur le serveur de publication, si le niveau de compatibilité est inférieur à 80RTM.  
  
-   Sur le serveur de publication si les Abonnées exécutent [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Impossible de stocker les données de conflit sur [!INCLUDE[ssEW](../../includes/ssew-md.md)] abonnés.  
  
 Stockage des informations de conflit est contrôlée par le **conflict_logging** propriété de publication. Pour plus d’informations, consultez [sp_addmergepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) et [sp_changemergepublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 Il est également possible de résoudre les conflits de façon interactive au cours de la synchronisation à l'aide du programme de résolution interactif [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Le résolveur interactif est disponible via le Gestionnaire de synchronisation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Pour plus d’informations, consultez [synchroniser Gestionnaire de synchronisation Windows utilisant un abonnement & #40 ; Le Gestionnaire de synchronisation Windows & #41 ;](../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md).  
  
### Pour afficher et résoudre les conflits des publications de fusion  
  
1.  Se connecter à l’éditeur (ou un abonné, le cas échéant) dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Avec le bouton droit de la publication pour laquelle vous souhaitez afficher les conflits, puis cliquez sur **Afficher les conflits**.  
  
    > [!NOTE]  
    >  Si vous avez spécifié une valeur **'abonné'** pour la **conflict_logging** propriété, le **Afficher les conflits** option de menu n’est pas disponible. Pour afficher les conflits, démarrez ConflictViewer.exe à partir de l'invite de commandes. Par défaut, ConflictViewer.exe se trouve dans le répertoire suivant : Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE. Pour obtenir la liste des paramètres de démarrage valides, exécutez ConflictViewer.exe -?.  
  
4.  Dans la **Sélectionner la Table de conflit** boîte de dialogue, sélectionnez une base de données de publication et la table pour laquelle afficher les conflits.  
  
5.  Dans l'outil de résolution des conflits de réplication, vous pouvez effectuer les actions suivantes :  
  
    -   Filtrer des lignes avec les boutons situés à droite de la grille supérieure.  
  
    -   Sélectionner une ligne dans la grille supérieure pour afficher des informations sur cette ligne dans la grille inférieure.  
  
    -   Sélectionnez une ou plusieurs lignes dans la grille supérieure, puis cliquez sur **Supprimer**, ce qui revient à cliquer sur le **Soumettre le gagnant** bouton (sans apporter de modifications aux données).  
  
    -   Cliquez sur le bouton des propriétés (**...**) pour afficher plus d’informations sur une colonne impliquée dans un conflit.  
  
    -   Modifier des données dans le **vainqueur du conflit** ou **perdant du conflit** colonne avant d’envoyer les données (les données sont en lecture seule si la colonne est grisée).  
  
    -   Cliquez sur **Soumettre le gagnant** pour accepter la ligne désignée comme gagnante du conflit.  
  
    -   Cliquez sur **Soumettre le perdant** pour substituer la résolution et propager la valeur désignée comme le perdant du conflit pour tous les nœuds dans la topologie.  
  
    -   Sélectionnez **consigner les détails de ce conflit** pour enregistrer les données de conflit dans un fichier. Pour spécifier un emplacement pour le fichier, pointez sur le **vue** menu, puis sur **Options**. Entrez une valeur ou cliquez sur le bouton Parcourir (**...**), puis accédez au fichier approprié. Cliquez sur **OK** pour quitter le **Options** boîte de dialogue.  
  
6.  Fermer l'outil de résolution de conflits.  
  
## Voir aussi  
 [Détection et résolution avancées des conflits de réplication de fusion](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Spécifier un programme de résolution d'articles de fusion](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)  
  
  