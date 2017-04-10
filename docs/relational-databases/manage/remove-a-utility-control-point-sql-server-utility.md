---
title: "Supprimer un point de contr&#244;le de l&#39;utilitaire (utilitaire SQL&#160;Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# Supprimer un point de contr&#244;le de l&#39;utilitaire (utilitaire SQL&#160;Server)
  Cette rubrique explique comment supprimer un point de contrôle de l'utilitaire (UCP) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer un point de contrôle de l'utilitaire, utilisez :**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Avant d'utiliser cette procédure pour supprimer le point de contrôle de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , notez les conditions suivantes. La procédure stockée effectuera des vérifications des conditions préalables dans le cadre de l'opération.  
  
-   Avant d'exécuter cette procédure, toutes les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent être supprimées du point de contrôle de l'utilitaire. Notez que le point de contrôle de l'utilitaire est une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Supprimer une instance de SQL Server de l’utilitaire SQL Server](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
-   Cette procédure doit être exécutée sur un ordinateur qui est un UCP.  
  
-   Si l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de laquelle le point de contrôle de l'utilitaire est supprimé comporte un jeu d'éléments de collecte de données qui n'est pas d'utilitaire, la base de données UMDW (sysutility_mdw) ne sera pas supprimée par la procédure. Si tel est le cas, la base de données UMDW (sysutility_mdw) doit être supprimée manuellement avant que le point de contrôle de l’utilitaire soit à nouveau créé.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Cette procédure doit être exécutée par un utilisateur disposant d'autorisations **sysadmin** ; les mêmes autorisations sont requises pour créer un point de contrôle de l'utilitaire.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour supprimer un point de contrôle de l'utilitaire  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## Voir aussi  
 [Fonctionnalités et tâches de l'utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Utiliser l'Explorateur de l'utilitaire pour gérer l'Utilitaire SQL Server](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Résolution des problèmes liés à l'utilitaire SQL Server](../Topic/Troubleshoot%20the%20SQL%20Server%20Utility.md)  
  
  