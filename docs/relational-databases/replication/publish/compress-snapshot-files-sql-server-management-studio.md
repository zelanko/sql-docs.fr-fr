---
title: "compresser des fichiers d&#39;instantan&#233;s (SQL Server Management Studio) | Microsoft Docs"
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
  - "instantanés [réplication SQL Server], compressés"
  - "réplication d’instantané [SQL Server], instantanés compressés"
ms.assetid: 174ade3e-74a1-4e67-a6da-b874be3ff50f
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# compresser des fichiers d&#39;instantan&#233;s (SQL Server Management Studio)
  Spécifiez que les fichiers doivent être compressés dans le **instantané** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### Pour compresser des fichiers d'instantanés  
  
1.  Sur le **instantané** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue :  
  
    1.  Sélectionnez **Placer les fichiers dans le dossier suivant**puis cliquez sur **Parcourir** pour accéder à un répertoire ou entrez le chemin d'accès au répertoire dans lequel stocker les fichiers d'instantanés.  
  
        > [!NOTE]  
        >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si des abonnements extraits sont utilisés, vous devez spécifier un répertoire partagé comme un chemin universal naming convention (UNC), tel que \\\computername\snapshot. Pour plus d’informations, consultez [sécuriser le dossier de capture instantanée](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
    2.  Désactivez la case à cocher **Placer les fichiers dans le dossier par défaut** sauf si les fichiers d'instantanés doivent être enregistrés dans les deux emplacements.  
  
        > [!NOTE]  
        >  Si cette case à cocher est activée, les fichiers stockés dans le dossier par défaut ne sont pas compressés. Les fichiers compressés peuvent être stockées uniquement à l'emplacement secondaire spécifié à l'étape précédente.  
  
2.  Sélectionnez **Compresser les fichiers d'instantanés dans ce dossier**.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Configurer les propriétés d’instantané & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Modifier les propriétés des publications et des articles](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Instantanés compressés](../../../relational-databases/replication/compressed-snapshots.md)   
 [Initialiser un abonnement avec un instantané](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  