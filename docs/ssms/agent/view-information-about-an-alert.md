---
title: "Afficher les informations relatives à une alerte | Microsoft Docs"
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
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5bfe05dde95b8fdb47893ea17802b0798de9762a
ms.lasthandoff: 04/11/2017

---
# <a name="view-information-about-an-alert"></a>Afficher les informations relatives à une alerte
Cette rubrique explique comment afficher des infou demations relatives aux alertes [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ou de [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour afficher des informations relatives à une alerte, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent afficher des informations sur une alerte. Les autres utilisateurs doivent disposer du rôle de base de données fixe **SQLAgentOperatorRole** dans la base de données **msdb** .  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-information-about-an-alert"></a>Pour afficher des informations relatives à une alerte  
  
1.  Dans l' **Explorateur d'objets** , cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez afficher des informations sur une alerte.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Alertes** .  
  
4.  Cliquez avec le bouton droit sur l'alerte comportant les informations que vous voulez afficher, puis sélectionnez **Propriétés**.  
  
    Pour plus d’informations sur les options disponibles contenues dans la boîte de dialogue *Propriétés de l’alerte***nom_alerte** , consultez :  
  
    -   [Propriétés de l’alerte - Nouvelle alerte &amp;#40;page Général&amp;#41;](../../ssms/agent/alert-properties-new-alert-general-page.md)  
  
    -   [Propriétés de l’alerte - Nouvelle alerte &amp;#40;page Réponse&amp;#41;](../../ssms/agent/alert-properties-new-alert-response-page.md)  
  
    -   [Propriétés de l’alerte - Nouvelle alerte &amp;#40;page Options&amp;#41;](../../ssms/agent/alert-properties-new-alert-options-page.md)  
  
    -   [Propriétés de l'alerte &amp;#40;page Historique&amp;#41;](../../ssms/agent/alert-properties-history-page.md)  
  
5.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
## <a name="TsqlProcedure"></a>Utilisation de Transact-SQL  
  
#### <a name="to-view-information-about-an-alert"></a>Pour afficher des informations relatives à une alerte  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- reports information about the Demo: Sev. 25 Errors alert  
    -- This example assumes that the 'Demo: Sev. 25 Errors' alert exists.  
    USE msdb ;  
    GO  
  
    EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors'  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_help_alert (Transact-SQL)](http://msdn.microsoft.com/en-us/850cef4e-6348-4439-8e79-fd1bca712091).  
  

