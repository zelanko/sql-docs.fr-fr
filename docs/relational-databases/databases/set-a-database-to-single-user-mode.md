---
title: "D&#233;finir une base de donn&#233;es en mode mono-utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode mono-utilisateur [SQL Server], option de base de données"
ms.assetid: fb5254eb-b635-4b39-8361-136fd36f2b1f
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# D&#233;finir une base de donn&#233;es en mode mono-utilisateur
  Cette rubrique explique comment configurer une base de données définie par l'utilisateur en mode mono-utilisateur dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Le mode mono-utilisateur signifie que seul un utilisateur à la fois peut avoir accès à la base de données. Il est généralement destiné à des opérations de maintenance.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Configuration requise](#Prerequisites)  
  
     [Sécurité](#Security)  
  
-   **Pour définir une base de données en mode mono-utilisateur, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Si d'autres utilisateurs sont connectés à la base de données au moment où vous définissez la base de données en mode mono-utilisateur, leurs connexions à la base de données sont fermées sans avertissement.  
  
-   La base de données reste en mode mono-utilisateur même si l'utilisateur qui a défini l'option se déconnecte. À ce stade, un autre utilisateur (et un seul) peut se connecter à la base de données.  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   Avant d'affecter la valeur SINGLE_USER à la base de données, vérifiez que l'option AUTO_UPDATE_STATISTICS_ASYNC a la valeur OFF. Si la valeur de cette option est ON, le thread d'arrière-plan utilisé pour mettre à jour les statistiques se connecte à la base de données et vous ne pourrez pas accéder à celle-ci en mode mono-utilisateur. Pour plus d’informations, consultez [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'autorisation ALTER sur la base de données.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour définir une base de données en mode mono-utilisateur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], puis développez-la.  
  
2.  Cliquez avec le bouton droit sur la base de données à modifier, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés de la base de données** , cliquez sur la page **Options** .  
  
4.  Dans l'option **Restreindre l'accès** , sélectionnez **Utilisateur unique**.  
  
5.  Si d'autres utilisateurs sont connectés à la base de données, un message **Ouvrir les connexions** apparaît. Pour modifier la propriété et fermer toutes les autres connexions, cliquez sur **Oui**.  
  
 Vous pouvez également définir la base de données pour un accès Multiple ou Restreint à l'aide de cette procédure. Pour plus d’informations sur les options de restriction d’accès, consultez [Propriétés de la base de données &#40;page Options&#41;](../../relational-databases/databases/database-properties-options-page.md).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour définir une base de données en mode mono-utilisateur  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple attribue à la base de données la valeur `SINGLE_USER` pour obtenir l'accès exclusif. L'exemple attribue ensuite à l'état de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] la valeur `READ_ONLY` et octroie l'accès à la base de données à tous les utilisateurs. L'option d'arrêt `WITH ROLLBACK IMMEDIATE` est spécifiée dans la première instruction `ALTER DATABASE` . Suite à celà, toutes les transactions incomplètes sont restaurées et les autres connexions à la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sont immédiatement déconnectées.  
  
 [!code-sql[DatabaseDDL#AlterDatabase8](../../relational-databases/databases/codesnippet/tsql/set-a-database-to-single_1.sql)]  
  
## Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
  