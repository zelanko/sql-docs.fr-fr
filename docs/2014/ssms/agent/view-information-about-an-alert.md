---
title: Afficher les informations relatives à une alerte | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5df32cf165780fcda1a51c3e76d52313a2d85bdb
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43814915"
---
# <a name="view-information-about-an-alert"></a>Afficher les informations relatives à une alerte
  Cette rubrique explique comment afficher des infou demations relatives aux alertes [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher des informations relatives à une alerte, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent afficher des informations sur une alerte. Les autres utilisateurs doivent disposer du rôle de base de données fixe **SQLAgentOperatorRole** dans la base de données **msdb** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-information-about-an-alert"></a>Pour afficher des informations relatives à une alerte  
  
1.  Dans l' **Explorateur d'objets** , cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez afficher des informations sur une alerte.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Alertes** .  
  
4.  Cliquez avec le bouton droit sur l'alerte comportant les informations que vous voulez afficher, puis sélectionnez **Propriétés**.  
  
     Pour plus d’informations sur les options disponibles contenues dans la boîte de dialogue *Propriétés de l’alerte***nom_alerte*, consultez :  
  
    -   [Propriétés de nouvelle alerte d’alerte &#40;Page Général&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [Propriétés de nouvelle alerte d’alerte &#40;Page de réponse&#41;](alert-properties-new-alert-response-page.md)  
  
    -   [Propriétés de l’alerte : Nouvelle alerte &#40;Page Options&#41;](alert-properties-new-alert-options-page.md)  
  
    -   [Propriétés de l'alerte &#40;page Historique&#41;](alert-properties-history-page.md)  
  
5.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-information-about-an-alert"></a>Pour afficher des informations relatives à une alerte  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
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
  
 Pour plus d’informations, consultez [sp_help_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql).  
  
  
