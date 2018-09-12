---
title: Démarrer, arrêter ou suspendre le service SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, starting
- SQL Server Agent, pausing
- SQL Server Agent, stopping
ms.assetid: c95a9759-dd30-4ab6-9ab0-087bb3bfb97c
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8927a6aa19937f85616a3e7a28ca0c4316519343
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43818465"
---
# <a name="start-stop-or-pause-the-sql-server-agent-service"></a>Start, Stop, or Pause the SQL Server Agent Service
  Cette rubrique explique comment démarrer, arrêter ou redémarrer le service de l'Agent SQL Server dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Vous pouvez configurer le service l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour qu'il démarre automatiquement lorsque le système d'exploitation démarre, ou vous pouvez le démarrer manuellement lorsque vous avez besoin d'exécuter des travaux. Vous pouvez arrêter ou interrompre le service de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour interrompre les travaux, les notifications de l'opérateur et les alertes.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   [Pour démarrer, arrêter ou redémarrer le service de l'Agent SQL Server à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être exécuté en tant que service pour automatiser les tâches administratives. Pour plus d’informations, consultez [Configure SQL Server Agent](configure-sql-server-agent.md).  
  
-   Cependant, l'Explorateur d'objets affiche le nœud [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent uniquement si vous avez l'autorisation de l'utiliser.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Pour exécuter ses fonctions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être configuré pour utiliser les informations d'identification d'un compte qui est membre du rôle serveur fixe **sysadmin** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le compte doit avoir les autorisations Windows suivantes :  
  
-   Ouvrir une session en tant que service (SeServiceLogonRight)  
  
-   Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)  
  
-   Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)  
  
-   Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)  
  
 Pour plus d’informations sur les autorisations Windows requises pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte de service de l’Agent, consultez [sélectionner un compte pour le Service SQL Server Agent](select-an-account-for-the-sql-server-agent-service.md) et [configurer les comptes de Service Windows et Autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-start-stop-or-restart-the-sql-server-agent-service"></a>Pour démarrer, arrêter ou redémarrer le service de l'Agent SQL Server  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez gérer le service de l'Agent SQL Server.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, puis sélectionnez **Démarrer**, **Arrêter**ou **Redémarrer**.  
  
3.  Dans la boîte de dialogue **Contrôle de compte d'utilisateur** , cliquez sur **Oui**.  
  
4.  Lorsque vous y êtes invité, et si vous souhaitez exécuter l'action, cliquez sur **Oui**.  
  
 Pour plus d'informations, consultez :  
  
-   [Démarrer, arrêter, suspendre, reprendre, redémarrer le moteur de base de données, SQL Server Agent ou le service SQL Server Browser](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
-   [Démarrer automatiquement SQL Server Agent &#40;SQL Server Management Studio&#41;](autostart-sql-server-agent-sql-server-management-studio.md)  
  
  
