---
title: "Définir un alias SQL Server pour le service SQL Server Agent | Microsoft Docs"
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
- aliases [SQL Server], creating
- SQL Server Agent, aliases
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8ab5a19e73661e5695bd98f3469c507f328c12a3
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="set-a-sql-server-alias-for-the-sql-server-agent-service-sql-server-management-studio"></a>Définir un alias SQL Server pour le service SQL Server Agent (SQL Server Management Studio)
Cette rubrique indique comment définir un alias [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] que [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent utilisera pour se connecter au [!INCLUDE[ssDE](../../includes/ssde_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Par défaut, le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent se connecte à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] par l'intermédiaire de canaux de communication nommés qui utilisent des noms de serveur dynamiques ne nécessitant aucune configuration supplémentaire du client. Vous devez configurer un alias de connexion serveur uniquement si vous n'utilisez pas le transport réseau par défaut ou si vous vous connectez à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] via un autre canal nommé.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   [Pour définir un alias SQL Server pour le service SQL Server Agent à l'aide de SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ne fonctionnera correctement que si vous sélectionnez un alias qui se réfère à l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Cependant, l'Explorateur d'objets affiche le nœud de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] uniquement si vous avez l'autorisation de l'utiliser.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Autorisations  
Pour exécuter ses fonctions, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] doit être configuré pour utiliser les informations d'identification d'un compte qui est membre du rôle serveur fixe **sysadmin** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Le compte doit avoir les autorisations Windows suivantes :  
  
-   Ouvrir une session en tant que service (SeServiceLogonRight)  
  
-   Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)  
  
-   Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)  
  
-   Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)  
  
Pour plus d’informations sur les autorisations Windows requises pour le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, consultez [Sélectionner un compte pour le service SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) et [Configuration des comptes de service Windows](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-set-a-sql-server-alias-for-the-sql-server-agent-service"></a>Pour définir un alias SQL Server pour le service SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets,**connectez-vous à une instance de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)] , puis développez cette instance.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés de l’Agent SQL Server***nom_serveur* , sous **Sélectionner une page**, sélectionnez **Connexion**et  
  
4.  Dans la zone **Alias du serveur hôte local** , tapez l'alias du serveur auquel l'agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] doit se connecter.  
  
5.  Cliquez sur **OK**.  
  

