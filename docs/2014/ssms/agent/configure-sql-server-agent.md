---
title: Configurer SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0e7c8cb2230a7b6923514f0928b844f72c216d58
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63253571"
---
# <a name="configure-sql-server-agent"></a>Configurer SQL Server Agent
  Cette rubrique explique comment spécifier certaines options de configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent lors de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L’ensemble complet des options de configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent n’est disponible que dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], les objets SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects) ou dans les procédures stockées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   [Pour configurer SQL Server Agent](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Cliquez sur **SQL Server Agent** dans l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour administrer des travaux, des opérateurs, des alertes et le service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Cependant, l'Explorateur d'objets n'affiche le nœud [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent que si vous avez l'autorisation de l'utiliser.  
  
-   Le redémarrage automatique ne doit pas être activé pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou le service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sur les instances de cluster de basculement.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Pour exécuter ses fonctions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être configuré pour utiliser les informations d'identification d'un compte qui est membre du rôle serveur fixe **sysadmin** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le compte doit avoir les autorisations Windows suivantes :  
  
-   Ouvrir une session en tant que service (SeServiceLogonRight)  
  
-   Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)  
  
-   Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)  
  
-   Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)  
  
 Pour plus d’informations sur les autorisations Windows requises pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le compte de service de l’agent, consultez [Sélectionner un compte pour le service SQL Server Agent](select-an-account-for-the-sql-server-agent-service.md) et [configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-configure-sql-server-agent"></a>Pour configurer SQL Server Agent  
  
1.  Cliquez sur le bouton **Démarrer** , puis, dans le menu **Démarrer**  , cliquez sur **Panneau de configuration**.  
  
2.  Dans le Panneau de configuration, cliquez sur **Système et sécurité**, puis sur **Outils d'administration**et sélectionnez **Stratégie de sécurité locale**.  
  
3.  Dans Stratégie de sécurité locale, cliquez sur le chevron pour développer le dossier **Stratégies locales** , puis cliquez sur le dossier **Attribution des droits utilisateur** .  
  
4.  Cliquez avec le bouton droit sur l’autorisation à configurer pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et sélectionnez **Propriétés**.  
  
5.  Dans la boîte de dialogue des propriétés de l'autorisation, vérifiez que le compte sous lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent s'exécute est répertorié. Sinon, cliquez sur **Ajouter un utilisateur ou un groupe**, entrez le compte sous lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent s'exécute dans la boîte de dialogue **Choisir des utilisateurs, des ordinateurs ou des groupes** , puis cliquez sur **OK**.  
  
6.  Répétez ces étapes pour chaque autorisation à ajouter pour l'exécution de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
