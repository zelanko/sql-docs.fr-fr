---
title: "Consid&#233;rations sur l&#39;ex&#233;cution de jeux d&#39;&#233;l&#233;ments de collecte de l&#39;utilitaire et non-utilitaire sur la m&#234;me instance de SQL&#160;Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# Consid&#233;rations sur l&#39;ex&#233;cution de jeux d&#39;&#233;l&#233;ments de collecte de l&#39;utilitaire et non-utilitaire sur la m&#234;me instance de SQL&#160;Server
  Le jeu d'éléments de collecte de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est pris en charge côte à côte avec les jeux d'éléments de collecte d'utilitaires non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Autrement dit, une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être surveillée par d'autres jeux d'éléments de collecte bien qu'elle soit membre d'un utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Toutefois, vous devez désactiver les fonctionnalités du jeu d'éléments de collecte de l'utilitaire non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pendant que l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est inscrite dans l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Une fois l'instance inscrite avec l'UCP, vous pouvez redémarrer le jeu d'éléments de collecte de l'utilitaire non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Notez, toutefois, que tous les jeux d'éléments de collecte sur l'instance gérée téléchargeront leurs données dans l'entrepôt de données de gestion de l'utilitaire (UMDW). Le nom de fichier UMDW est sysutility_mdw.  
  
 Pour exécuter des jeux d'éléments de collecte d'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] côte à côte avec des jeux d'éléments de collecte d'utilitaire non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], prenez en considération les points suivants :  
  
-   Les jeux d'éléments de collecte côte à côte sont pris en charge.  
  
-   Vous devez désactiver les collecteurs de données existants en inscrivant des instances dans l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pour satisfaire aux exigences de validation, vous devez exécuter les procédures stockées suivantes sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de créer un UCP, et sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de l'inscrire dans l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     Si vous n'exécutez pas ces procédures stockées avant de lancer l'Assistant Créer un UCP ou l'Assistant Ajouter une instance gérée, l'opération échouera.  
  
-   Vous devez utiliser l'UMDW (sysutility_mdw) de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour tous les jeux d'éléments de collecte sur une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Voir aussi  
 [Fonctionnalités et tâches de l'utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Configurer votre entrepôt de données de point de contrôle de l’utilitaire &#40;utilitaire SQL Server&#41;](../../relational-databases/manage/configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  