---
title: Créer une alerte d’événement WMI | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI event alerts [SQL Server Management Studio]
ms.assetid: b8c46db6-408b-484e-98f0-a8af3e7ec763
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5af4472d80e74c9d2845e6397f815ffb1c27f4d8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211430"
---
# <a name="create-a-wmi-event-alert"></a>Create a WMI Event Alert
  Cette rubrique explique comment créer une alerte de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est déclenchée lorsqu'un événement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifique surveillé par le fournisseur WMI se produit pour les événements de serveur dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Pour plus d’informations sur l’utilisation du fournisseur WMI [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour surveiller les événements, consultez [fournisseur WMI pour les concepts des événements de serveur](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md). Pour plus d’informations sur les autorisations nécessaires pour recevoir des notifications d’alertes d’événements WMI, consultez [Sélectionner un compte pour le service SQL Server Agent](select-an-account-for-the-sql-server-agent-service.md). Pour plus d’informations sur WQL, consultez [Utilisation de WQL avec le fournisseur WMI pour les événements de serveur](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer une alerte d'événement WMI, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est un outil simple, fonctionnant en mode graphique, qui permet de gérer tout le système d'alerte. Son utilisation est recommandée pour configurer une infrastructure d'alertes.  
  
-   Les événements créés à l’aide de **xp_logevent** surviennent dans la base de données master. Ainsi, la procédure **xp_logevent** ne déclenche pas d’alerte sauf si la valeur de **@database_name** pour l’alerte est **'master'** ou NULL.  
  
-   Seuls les espaces de noms WMI résidant sur l'ordinateur qui exécute l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont pris en charge.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Par défaut, seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter la procédure **sp_add_alert**.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-wmi-event-alert"></a>Pour créer une alerte d'événement WMI  
  
1.  Dans l' **Explorateur d'objets** , cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez créer une alerte d'événement WMI.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit sur **Alertes** , puis sélectionnez **Nouvelle alerte**.  
  
4.  Dans la boîte de dialogue **Nouvelle alerte** , dans la zone **Nom** , entrez un nom pour cette alerte.  
  
5.  Sélectionnez la case à cocher **Activer** afin d'activer l'alerte à exécuter. Par défaut, l'option **Activer** est sélectionnée.  
  
6.  Dans la liste **Type** , sélectionnez **Alerte d'événement WMI**.  
  
7.  Sous **Définition d’une alerte d’événement WMI**, dans la zone **Espace de noms** , spécifiez l’espace de noms WMI pour l’instruction WQL (WMI Query Language) qui identifie l’événement WMI qui déclenchera cette alerte.  
  
8.  Dans la zone **Requête** , spécifiez l'instruction WQL qui identifie l'événement auquel cette alerte répond.  
  
9. Cliquez sur **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-wmi-event-alert"></a>Pour créer une alerte d'événement WMI  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- creates a WMI event alert that retrieves all event properties for any ALTER_TABLE event that occurs on table AdventureWorks2012.Sales.SalesOrderDetail  
    -- This example assumes that the message 54001 already exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert 2',  
        @message_id = 54001  
        @notification_message = N'Error 54001 has occurred on the Sales.SalesOrderDetail table on the AdventureWorks2012 database. Please see the following information...',  
        @wmi_namespace = '\\.\root\Microsoft\SqlServer\ServerEvents\,  
        @wmi_query = N'SELECT * FROM ALTER_TABLE   
    WHERE DatabaseName = 'AdventureWorks2012' AND SchemaName = 'Sales'   
        AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'';  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).  
  
  
