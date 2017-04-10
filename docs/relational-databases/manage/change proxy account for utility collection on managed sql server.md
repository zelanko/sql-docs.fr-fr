---
title: "Modifier le compte proxy pour le jeu d&#39;&#233;l&#233;ments de collecte de l&#39;utilitaire sur une instance g&#233;r&#233;e de SQL&#160;Server (utilitaire SQL&#160;Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Modifier le compte proxy pour le jeu d&#39;&#233;l&#233;ments de collecte de l&#39;utilitaire sur une instance g&#233;r&#233;e de SQL&#160;Server (utilitaire SQL&#160;Server)
  Cette rubrique explique comment modifier le compte proxy pour le jeu d'éléments de collecte de l'utilitaire sur une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour modifier le compte proxy pour le jeu d'éléments de collecte de l'utilitaire sur une instance gérée de SQL Server  
  
1.  Supprimez l'instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Dans l’**Explorateur de l’utilitaire** dans SSMS, cliquez sur le nœud **Instances gérées**.  
  
    -   Dans l’**Explorateur de l’utilitaire** en mode Liste, cliquez avec le bouton droit sur le nom de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et sélectionnez **Supprimer une instance gérée…**. Pour plus d’informations, consultez [Supprimer une instance de SQL Server de l’utilitaire SQL Server](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
2.  Réinscrivez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Dans l’**Explorateur de l’utilitaire** dans SSMS, cliquez avec le bouton droit sur le nœud **Instances gérées** et sélectionnez **Ajouter une instance gérée…**.  
  
    -   Suivez les indications de l'Assistant jusqu'au bout, en spécifiant le nouveau compte proxy.  
  
## Voir aussi  
 [Fonctionnalités et tâches de l'utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Résolution des problèmes liés à l'utilitaire SQL Server](../Topic/Troubleshoot%20the%20SQL%20Server%20Utility.md)  
  
  