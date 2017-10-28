---
title: "Affecter des alertes à un opérateur | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, operators
- assigning alerts to operator
- SQL Server Agent, alerts
- alerts [SQL Server], assigning to operator
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: aa818155-6fa2-4565-a09f-5c7e31c89754
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0dc10ef2ce9fd666cef48bc286ae5c0d4acc6514
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="assign-alerts-to-an-operator"></a>Affecter des alertes à un opérateur
Cette rubrique explique comment affecter des alertes de l'Agent [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] à des opérateurs afin qu'ils puissent recevoir des notifications concernant des travaux dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ou de [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour affecter des alertes à un opérateur, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] est un outil simple, basé sur une interface graphique, qui permet de gérer le système d'alertes dans sa totalité. L’utilisation de [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] est recommandée pour configurer l’infrastructure d’alertes.  
  
-   Pour envoyer une notification en réponse à une alerte, vous devez d'abord configurer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] pour l'envoi de messages électroniques. Pour plus d’informations, consultez [Configurer la messagerie de SQL Server Agent en vue de l’utilisation de la messagerie de base de données](http://msdn.microsoft.com/en-us/4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce).  
  
-   En cas d’échec au moment de l’envoi d’un message par e-mail ou d’une notification par radiomessagerie, l’échec est consigné dans le journal des erreurs du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Autorisations  
Seuls les membres du rôle serveur fixe **sysadmin** peuvent affecter des alertes aux opérateurs.  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-assign-alerts-to-an-operator"></a>Pour affecter des alertes à un opérateur  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur qui contient l'opérateur auquel vous souhaitez affecter une alerte.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Opérateurs** .  
  
4.  Cliquez avec le bouton droit sur l’opérateur auquel vous souhaitez affecter une alerte et sélectionnez **Propriétés**, puis la page **Notifications** .  
  
5.  Dans la boîte de dialogue *Propriétés***nom_opérateur** , sous **Sélectionner une page**, sélectionnez **Notifications**.  
  
6.  Sous **Afficher les notifications envoyées à cet utilisateur par**, sélectionnez **Alertes** pour afficher la liste des alertes envoyées à cet opérateur, ou sélectionnez **Travaux** pour afficher la liste des travaux qui envoient des notifications à cet opérateur. Cochez une ou plusieurs cases parmi les suivantes pour définir, en fonction de vos besoins, la méthode de notification pour chaque notification : **Messagerie électronique**, **Radiomessagerie**ou **Net send**.  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
## <a name="TsqlProcedure"></a>Utilisation de Transact-SQL  
  
#### <a name="to-assign-alerts-to-an-operator"></a>Pour affecter des alertes à un opérateur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert)  
    -- This example assumes that Test Alert already exists
    -- and that François Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'François Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_add_notification (Transact-SQL)](http://msdn.microsoft.com/en-us/0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd).  
  

