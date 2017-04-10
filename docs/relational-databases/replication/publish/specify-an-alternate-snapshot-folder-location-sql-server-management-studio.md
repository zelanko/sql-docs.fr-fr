---
title: "Sp&#233;cifier un autre emplacement de dossier d&#39;instantan&#233; (SQL Server Management Studio) | Microsoft Docs"
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
  - "instantanés [réplication SQL Server], emplacements des autres dossiers"
  - "réplication d’instantané [SQL Server], emplacements des autres dossiers"
  - "autres dossiers d'instantané [réplication SQL Server]"
ms.assetid: 9293f0eb-5531-47ec-b6e2-0392823ce5cc
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# Sp&#233;cifier un autre emplacement de dossier d&#39;instantan&#233; (SQL Server Management Studio)
  Spécifier un autre emplacement d’instantanés sur le **instantané** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### Pour spécifier un autre emplacement d'instantané  
  
1.  Sur le **instantané** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue :  
  
    1.  Sélectionnez **Placer les fichiers dans le dossier suivant**puis cliquez sur **Parcourir** pour accéder à un répertoire ou entrez le chemin d'accès au répertoire dans lequel stocker les fichiers d'instantanés.  
  
        > [!NOTE]  
        >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si des abonnements extraits sont utilisés, vous devez spécifier un répertoire partagé comme un chemin universal naming convention (UNC), tel que \\\computername\snapshot. Pour plus d’informations, consultez [sécuriser le dossier de capture instantanée](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
    2.  Désactivez la case à cocher **Placer les fichiers dans le dossier par défaut** sauf si les fichiers d'instantanés doivent être enregistrés dans les deux emplacements.  
  
     Pour compresser les fichiers d'instantanés, sélectionnez **Compresser les fichiers d'instantanés à cet emplacement**. La compression est généralement utilisée avec les connexions à faible bande passante et d'autres emplacements d'instantané sur des supports amovibles, par exemple un CD-ROM.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Autres emplacements du dossier d'instantané](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Configurer les propriétés d’instantané & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Spécifier l’emplacement par défaut des instantanés & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Modifier les propriétés des publications et des articles](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Initialiser un abonnement avec un instantané](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  