---
title: "sp&#233;cifier l&#39;emplacement par d&#233;faut des instantan&#233;s (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instantanés [réplication SQL Server], emplacements par défaut"
  - "emplacements par défaut des instantanés"
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# sp&#233;cifier l&#39;emplacement par d&#233;faut des instantan&#233;s (SQL Server Management Studio)
  Spécifiez l'emplacement par défaut des instantanés dans la page **Dossier d'instantanés** de l'Assistant Configuration de la distribution. Pour plus d’informations sur l’utilisation de cet Assistant, consultez la page [configurer la publication et Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md). Si vous créez une publication sur un serveur qui n'est pas configuré en tant que serveur de distribution, spécifiez un emplacement d'instantanés par défaut dans la page **Dossier d'instantanés** de l'Assistant Nouvelle publication. Pour plus d’informations sur l’utilisation de cet Assistant, consultez la page [créer une Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
 Modifier l’emplacement de la capture instantanée par défaut sur le **éditeurs** page de le **Propriétés du serveur de distribution - \< serveur de distribution>** boîte de dialogue. Pour plus d’informations, consultez [Afficher et de modifier le serveur de distribution et de propriétés de l’éditeur](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md). Définissez le dossier de capture instantanée pour chaque publication dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d'informations, voir [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### Pour modifier l'emplacement par défaut des instantanés  
  
1.  Sur le **éditeurs** page de le **Propriétés du serveur de distribution - \< serveur de distribution>** boîte de dialogue, cliquez sur le bouton des propriétés (**...**) pour le serveur de publication pour laquelle vous souhaitez modifier l’emplacement de la capture instantanée par défaut.  
  
2.  Dans la **Propriétés du serveur de publication - \< serveur de publication>** boîte de dialogue, entrez une valeur pour le **dossier de capture instantanée par défaut** propriété.  
  
    > [!NOTE]  
    >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si des abonnements extraits sont utilisés, vous devez spécifier un répertoire partagé comme un chemin universal naming convention (UNC), tel que \\\computername\snapshot. Pour plus d’informations, consultez [sécuriser le dossier de capture instantanée](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Autres emplacements du dossier d'instantané](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  