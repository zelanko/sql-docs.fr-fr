---
title: "sp&#233;cifier le format d&#39;instantan&#233; (SQL Server Management Studio) | Microsoft Docs"
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
  - "instantanés [réplication SQL Server], formats"
  - "réplication d’instantané [SQL Server], formats"
ms.assetid: 7c95f545-731a-4743-9acb-0b325ef9b98b
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# sp&#233;cifier le format d&#39;instantan&#233; (SQL Server Management Studio)
  Spécifier le format d’instantané sur le **instantané** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### Pour spécifier le format d'instantané  
  
1.  Sur le **instantané** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez **SQL Server natif - tous les abonnés doivent être des serveurs exécutant SQL Server** ou **caractère - obligatoire si un serveur de publication ou un abonné n’exécute pas SQL Server**.  
  
    > [!NOTE]  
    >  Il est conseillé de sélectionner le format natif, à moins que cette publication ne doive prendre en charge les abonnements à une base de données [!INCLUDE[ssEW](../../../includes/ssew-md.md)] ou à une base de données non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Configurer les propriétés d’instantané & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Modifier les propriétés des publications et des articles](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Initialiser un abonnement avec un instantané](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  