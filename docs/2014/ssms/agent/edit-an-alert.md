---
title: Modifier une alerte | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], modifying
- modifying alerts
ms.assetid: f518e528-cc8f-446a-b37d-98505b86e430
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: acc1472501d21be27ffa8e71190a79961e8eb824
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808835"
---
# <a name="edit-an-alert"></a>Modifier une alerte
  Cette rubrique explique comment modifier une alerte de l'Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour modifier une alerte, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent modifier les informations dans une alerte. Les autres utilisateurs doivent disposer du rôle de base de données fixe **SQLAgentOperatorRole** dans la base de données **msdb** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-edit-an-alert"></a>Pour modifier une alerte  
  
1.  Dans l' **Explorateur d'objets** , cliquez sur le signe plus (+) pour développer le serveur contenant l'alerte que vous souhaitez modifier.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Alertes** .  
  
4.  Cliquez avec le bouton droit sur l’alerte à modifier, puis sélectionnez **Propriétés**.  
  
5.  Mettez à jour les propriétés de l'alerte dans les pages **Général**, **Réponse**et **Options** .  
  
6.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-edit-an-alert"></a>Pour modifier une alerte  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- changes the enabled setting of Test Alert to 0  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_alert  
        @name = N'Test Alert',  
        @enabled = 0 ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_update_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql).  
  
  
