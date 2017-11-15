---
title: "Définir la connexion SQL Server pour le service SQL Server Agent | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ae121d1c655caadfb447d2714601c0f24ea71c1c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a>Définir la connexion SQL Server pour le service SQL Server Agent (SQL Server Management Studio)
Cette rubrique décrit la configuration de la connexion entre l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et le [!INCLUDE[ssDE](../../includes/ssde_md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] au moyen de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Le service de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] peut se connecter à une instance locale de SQL Server en utilisant l'authentification Windows.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour définir la connexion SQL Server pour SQL Server Agent à l'aide de :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   Cependant, l'Explorateur d'objets affiche le nœud de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent uniquement si vous avez l'autorisation de l'utiliser.  
  
-   À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent ne prend pas en charge l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Cette option est disponible uniquement lorsque vous administrez une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Pour exécuter ses fonctions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent doit être configuré pour utiliser les informations d'identification d'un compte qui est membre du rôle serveur fixe **sysadmin** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Le compte doit avoir les autorisations Windows suivantes :  
  
-   Ouvrir une session en tant que service (SeServiceLogonRight)  
  
-   Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)  
  
-   Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)  
  
-   Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)  
  
Pour plus d’informations sur les autorisations Windows nécessaires pour le compte de service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, consultez [Sélectionner un compte pour le service SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) et [Setting Up Windows Service Accounts](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)(Configuration des comptes de service Windows).  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-the-sql-server-connection"></a>Pour configurer la connexion à SQL Server  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur que vous souhaitez configurer avec une connexion à son service SQL Server Agent.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent** , puis sélectionnez **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés de SQL Server Agent***nom_seveur* , sous **Sélectionner une page**, cliquez sur **Connexion**.  
  
4.  Sous **Connexion SQL Server**, sélectionnez **Utiliser l'authentification Windows** pour permettre à l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] de se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] [!INCLUDE[ssDE](../../includes/ssde_md.md)] avec [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Authentication. Les connexions aux bases de données [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] et versions ultérieures nécessitent l'authentification Windows.  
  
