---
title: "Démarrer, arrêter ou suspendre le service SQL Server Agent | Microsoft Docs"
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
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: af137c019a7f96769b801d01f882e1d98b0da2ea
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a>Démarrer, arrêter ou suspendre le service SQL Server Agent
Cette rubrique explique comment démarrer, arrêter ou redémarrer le service de SQL Server Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
Vous pouvez configurer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent pour qu'il démarre automatiquement lorsque le système d'exploitation démarre, ou vous pouvez le démarrer manuellement lorsque vous avez besoin d'exécuter des travaux. Vous pouvez arrêter ou interrompre le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent pour interrompre les travaux, les notifications de l'opérateur et les alertes.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   [Pour démarrer, arrêter ou redémarrer le service SQL Server Agent à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] doit être exécuté en tant que service pour automatiser les tâches administratives. Pour plus d’informations, consultez [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).  
  
-   Cependant, l'Explorateur d'objets affiche le nœud de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent uniquement si vous avez l'autorisation de l'utiliser.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Pour exécuter ses fonctions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent doit être configuré pour utiliser les informations d'identification d'un compte qui est membre du rôle serveur fixe **sysadmin** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Le compte doit avoir les autorisations Windows suivantes :  
  
-   Ouvrir une session en tant que service (SeServiceLogonRight)  
  
-   Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)  
  
-   Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)  
  
-   Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)  
  
Pour plus d’informations sur les autorisations Windows requises pour le compte du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, consultez [Sélectionner un compte pour le service SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) et [Configuration des comptes de service Windows](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a>Pour démarrer, arrêter ou redémarrer le service SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez gérer le service de SQL Server Agent.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, puis sélectionnez **Démarrer**, **Arrêter**ou **Redémarrer**.  
  
3.  Dans la boîte de dialogue **Contrôle de compte d'utilisateur** , cliquez sur **Oui**.  
  
4.  Lorsque vous y êtes invité, et si vous souhaitez exécuter l'action, cliquez sur **Oui**.  
  
Pour plus d'informations, consultez :  
  
-   [Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser](http://msdn.microsoft.com/en-us/32660a02-e5a1-411a-9e57-7066ca459df6)  
  
-   [Démarrer automatiquement SQL Server Agent &amp;#40;SQL Server Management Studio&amp;#41;](../../ssms/agent/autostart-sql-server-agent-sql-server-management-studio.md)  
  

