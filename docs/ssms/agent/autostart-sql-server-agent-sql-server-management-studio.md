---
title: "Démarrer automatiquement l’Agent SQL Server (SQL Server Management Studio) | Microsoft Docs"
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
- SQL Server Agent, starting
- autostart SQL Server Agent
ms.assetid: 2ea332da-0ede-4d2b-b122-c4c10eaca191
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0eb657592f6d7f8a7004d337d880f5eefde3edd0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="autostart-sql-server-agent-sql-server-management-studio"></a>Démarrer automatiquement SQL Server Agent (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette rubrique explique comment configurer [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent pour qu’il redémarre automatiquement en cas d’arrêt inopiné dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   [Pour configurer SQL Server Agent en vue d'un redémarrage automatique, à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
Cependant, l'Explorateur d'objets affiche le nœud de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent uniquement si vous avez l'autorisation de l'utiliser.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Pour exécuter ses fonctions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent doit être configuré pour utiliser les informations d'identification d'un compte qui est membre du rôle serveur fixe **sysadmin** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Le compte doit avoir les autorisations Windows suivantes :  
  
-   Ouvrir une session en tant que service (SeServiceLogonRight)  
  
-   Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)  
  
-   Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)  
  
-   Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)  
  
Pour plus d’informations sur les autorisations Windows nécessaires pour le compte de service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, consultez [Sélectionner un compte pour le service SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) et [Setting Up Windows Service Accounts](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)(Configuration des comptes de service Windows).  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-sql-server-agent-to-automatically-restart"></a>Pour configurer SQL Server Agent en vue d'un redémarrage automatique  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez configurer SQL Server Agent afin qu'il redémarre automatiquement.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, puis cliquez sur **Propriétés**.  
  
3.  Dans la page **Général** , activez la case à cocher **Redémarrage automatique de SQL Server Agent après un arrêt inattendu**.  
  
