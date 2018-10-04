---
title: Définir la connexion SQL Server pour le Service SQL Server Agent (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a05c720a2db962683c81ad948aa616b5c6b20fd1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48161419"
---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a>Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)
  Cette rubrique décrit la configuration de la connexion entre l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] au moyen de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Le service de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut se connecter à une instance locale de SQL Server en utilisant l'authentification Windows.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour définir la connexion SQL Server pour SQL Server Agent à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Cependant, l'Explorateur d'objets affiche le nœud [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent uniquement si vous avez l'autorisation de l'utiliser.  
  
-   À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ne prend pas en charge l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cette option est disponible uniquement lorsque vous administrez une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Pour exécuter ses fonctions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être configuré pour utiliser les informations d'identification d'un compte qui est membre du rôle serveur fixe **sysadmin** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le compte doit avoir les autorisations Windows suivantes :  
  
-   Ouvrir une session en tant que service (SeServiceLogonRight)  
  
-   Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)  
  
-   Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)  
  
-   Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)  
  
 Pour plus d’informations sur les autorisations Windows requises pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte de service de l’Agent, consultez [sélectionner un compte pour le Service SQL Server Agent](select-an-account-for-the-sql-server-agent-service.md) et [configurer les comptes de Service Windows et Autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-the-sql-server-connection"></a>Pour configurer la connexion à SQL Server  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur que vous souhaitez configurer avec une connexion à son service SQL Server Agent.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent** , puis sélectionnez **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés de SQL Server Agent***nom_serveur*, sous **Sélectionner une page**, cliquez sur **Connexion**.  
  
4.  Sous **Connexion SQL Server**, sélectionnez **Utiliser l'authentification Windows** pour permettre à l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] avec [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication. Les connexions aux bases de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures nécessitent l'authentification Windows.  
  
  
