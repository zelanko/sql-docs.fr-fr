---
title: "Créer une alerte à l’aide d’un niveau de gravité | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- severity levels [SQL Server]
- alerts [SQL Server], severity levels
ms.assetid: a1fd71bf-5bf9-4ce2-9a1d-032576a4a6e9
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 97d966e9c8f1f8bf00277467ae6f94cb87e7fe0a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="create-an-alert-using-severity-level"></a>Créer une alerte à l'aide d'un niveau de gravité
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette rubrique explique comment créer une alerte de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent qui est déclenchée quand un événement d’un niveau de gravité spécifique a lieu dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ou de [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour créer une alerte à l'aide d'un niveau de gravité, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] est un outil simple, fonctionnant en mode graphique, qui permet de gérer tout le système d'alerte. Son utilisation est recommandée pour configurer une infrastructure d'alertes.  
  
-   Les événements créés à l’aide de **xp_logevent** surviennent dans la base de données master. Ainsi, la procédure **xp_logevent** ne déclenche pas d’alerte sauf si la valeur de **@database_name** pour l’alerte est **'master'** ou NULL.  
  
-   Les niveaux de gravité compris entre 19 et 25 envoient un message [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] au journal des applications [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows et déclenchent une alerte. Les événements dont le niveau de gravité est inférieur à 19 déclenchent des alertes uniquement si vous avez utilisé **sp_altermessage**, RAISERROR WITH LOG ou **xp_logevent** pour forcer leur enregistrement dans le journal des applications Windows.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Par défaut, seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter la procédure **sp_add_alert**.  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-an-alert-using-severity-level"></a>Pour créer une alerte à l'aide d'un niveau de gravité  
  
1.  Dans **l’Explorateur d'objets** , cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez créer une alerte à l'aide d'un niveau de gravité.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit sur **Alertes** , puis sélectionnez **Nouvelle alerte**.  
  
4.  Dans la boîte de dialogue **Nouvelle alerte** , dans la zone **Nom** , entrez un nom pour cette alerte.  
  
5.  Dans la liste **Type** , sélectionnez **Alerte d'événement SQL Server**.  
  
6.  Sous **Définition d'une alerte d'événement**, dans la liste **Nom de base de données** , sélectionnez une base de données pour restreindre l'alerte à une base de données spécifique.  
  
7.  Sous **Les alertes seront déclenchées selon**, cliquez sur **Gravité** , puis sélectionnez la gravité spécifique qui déclenchera l'alerte.  
  
8.  Activez la case à cocher correspondant à **Déclencher une alerte quand le message contient** afin de limiter l'alerte à une certaine séquence de caractères, puis entrez un mot clé ou une chaîne de caractères pour le **Texte du message**. Le nombre maximal de caractères autorisé est de 100.  
  
9. Cliquez sur **OK**.  
  
## <a name="TsqlProcedure"></a>Utilisation de Transact-SQL  
  
#### <a name="to-create-an-alert-using-severity-level"></a>Pour créer une alerte à l'aide d'un niveau de gravité  
  
1.  Dans l'**Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- adds an alert (Test Alert) that runs the Back up
    -- the AdventureWorks2012 Database job when fired   
    -- assumes that the message 55001 and the Back up
    -- the AdventureWorks2012 Database job already exist.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert',  
        @message_id = 55001,   
       @severity = 0,   
       @notification_message = N'Error 55001 has occurred. The DB will be backed up...',   
       @job_name = N'Back up the AdventureWorks2012 Database' ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_add_alert (Transact-SQL)](http://msdn.microsoft.com/en-us/d9b41853-e22d-4813-a79f-57efb4511f09).  
  
