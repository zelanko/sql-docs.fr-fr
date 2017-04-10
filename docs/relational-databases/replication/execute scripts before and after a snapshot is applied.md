---
title: "Ex&#233;cuter des scripts avant et apr&#232;s l&#39;application d&#39;un instantan&#233; (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instantanés [réplication SQL Server], scripts"
  - "scripts [réplication SQL Server], instantanés"
  - "réplication d’instantané [SQL Server], scripts"
ms.assetid: b7bb1e4c-5b48-4bb1-9dc8-47c911f2cc82
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Ex&#233;cuter des scripts avant et apr&#232;s l&#39;application d&#39;un instantan&#233; (SQL Server Management Studio)
  Spécifiez un script facultatif à exécuter avant ou après la capture instantanée est appliquée sur le **instantané** page de la **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
> [!NOTE]  
>  Ces options ne sont pas disponibles si le **format d’instantané** option est définie sur **caractère**.  
  
### Pour exécuter un script avant ou après l'application d'un instantané  
  
1.  Sur le **instantané** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue :  
  
    -   Pour spécifier un script à exécuter avant l'application de l'instantané, cliquez sur **Parcourir** pour rechercher le script, ou entrez un chemin d'accès pour le script dans la zone de texte **Exécuter ce script avant l'application de l'instantané** .  
  
        > [!NOTE]  
        >  Les Agents de distribution et de fusion doivent avoir des autorisations en lecture sur le répertoire spécifié. Si des abonnements extraits sont utilisés, vous devez spécifier un répertoire partagé comme un chemin universal naming convention (UNC), tel que \\\computername\scripts\myscript.sql.  
  
    -   Pour spécifier un script à exécuter après l'application de l'instantané, cliquez sur **Parcourir** pour rechercher le script, ou entrez un chemin d'accès conforme à la convention d'affectation de noms (UNC) pour le script dans la zone de texte **Exécuter ce script après l'application de l'instantané** .  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Configurer les propriétés d’instantané & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Modifier les propriétés des publications et des articles](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Exécuter des scripts avant et après l'application de l'instantané](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  