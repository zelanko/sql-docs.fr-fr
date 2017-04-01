---
title: "afficher les conflits de donn&#233;es pour les publications de fusion (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "résolution des conflits [réplication SQL Server], abonnements avec mise à jour en attente"
  - "abonnements mis à jour en attente [SQL Server replication]"
  - "affichage des informations sur les conflits"
ms.assetid: 9977dd75-b0de-4376-9c13-86d80567d8aa
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# afficher les conflits de donn&#233;es pour les publications de fusion (SQL Server Management Studio)
  Vous pouvez afficher les conflits pour la réplication transactionnelle d'égal à égal et la réplication transactionnelle avec des abonnements mis à jour en attente dans l'outil de résolution des conflits de réplication de [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Pour savoir comment les conflits sont détectés et résolus, consultez [la détection de conflit lors de la réplication d’égal à égal](../../relational-databases/replication/transactional/conflict-detection-in-peer-to-peer-replication.md) et [définie en file d’attente mise à jour de conflit d’Options de résolution & #40 ; SQL Server Management Studio & #41 ;](../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md).  
  
 La disponibilité des données de conflit dépend du type de réplication et de la période de rétention des conflits :  
  
-   Pour la réplication d'égal à égal, par défaut, l'Agent de distribution échoue lorsqu'il détecte un conflit. Une erreur de conflit est enregistrée dans le journal des erreurs, mais aucune donnée de conflit n'est enregistrée dans la table de conflits ; par conséquent, la consultation de cette erreur n'est pas possible. Si l'Agent de distribution est autorisé à continuer, un conflit est enregistré localement sur chaque nœud où il a été détecté. Pour plus d’informations, consultez « Gestion des conflits » dans [la détection de conflit lors de la réplication d’égal à égal](../../relational-databases/replication/transactional/conflict-detection-in-peer-to-peer-replication.md).  
  
-   Pour des abonnements mis à jour en attente, les données sont disponibles pour chaque conflit. Les données de conflit sont disponibles dans l'outil de résolution des conflits de réplication pendant la durée définie comme période de rétention des conflits (par défaut, 14 jours). Pour définir la période de rétention des conflits, effectuez l'une des opérations suivantes :  
  
    -   Spécifiez une valeur de rétention pour le paramètre @conflict_retention de [sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md).  
  
    -   Spécifiez la valeur **'conflict_retention'** pour le paramètre @property et une valeur de rétention pour le paramètre @value de [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md).  
  
### Pour afficher les conflits  
  
1.  Connectez-vous au serveur approprié dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur :  
  
    -   Pour la réplication d'égal à égal, il s'agit du nœud où le conflit s'est produit.  
  
    -   Pour les abonnements mis à jour en attente, il s'agit du serveur de publication.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .  
  
3.  Avec le bouton droit de la publication pour laquelle vous souhaitez afficher les conflits, puis cliquez sur **Afficher les conflits**.  
  
4.  Dans la **Sélectionner la Table de conflit** boîte de dialogue, sélectionnez une base de données de publication et la table pour laquelle afficher les conflits.  
  
5.  Dans l'outil de résolution des conflits de réplication, vous pouvez effectuer les actions suivantes :  
  
    -   Filtrer des lignes avec les boutons situés à droite de la grille supérieure.  
  
    -   Sélectionner une ligne dans la grille supérieure pour afficher des informations sur cette ligne dans la grille inférieure.  
  
    -   Sélectionnez une ou plusieurs lignes dans la grille supérieure, puis cliquez sur **Supprimer**, qui supprime la ligne de la table de conflits de métadonnées.  
  
    -   Cliquez sur le bouton des propriétés (**...**) pour afficher plus d’informations sur une colonne impliquée dans un conflit.  
  
    -   Sélectionnez **consigner les détails de ce conflit** pour enregistrer les données de conflit dans un fichier. Pour spécifier un emplacement pour le fichier, pointez sur le **vue** menu, puis sur **Options**. Entrez une valeur ou cliquez sur le bouton Parcourir (**...**), puis accédez au fichier approprié. Cliquez sur **OK** pour fermer la **Options** boîte de dialogue.  
  
6.  Fermer l'outil de résolution de conflits.  
  
## Voir aussi  
 [Réplication transactionnelle d'égal à égal](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Détection et résolution des conflits de mise à jour en attente](../../relational-databases/replication/transactional/queued-updating-conflict-detection-and-resolution.md)  
  
  