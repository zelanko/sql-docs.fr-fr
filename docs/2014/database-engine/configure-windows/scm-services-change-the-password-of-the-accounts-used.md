---
title: Modifier le mot de passe des comptes utilisés par SQL Server (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- expired password [SQL Server], SQL Server Agent
- passwords [SQL Server], SQL Server Agent service
- passwords [SQL Server], changing
- expired password [SQL Server], Database Engine
- passwords [SQL Server], SQL Server service
- Database Engine [SQL Server], passwords
- changing passwords used by SQL Server
- modifying passwords
ms.assetid: 5b6dcc03-6cae-45d3-acef-6f85ca6d615f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1454e29835c0087fb75c93a1680f452dfe0f2c05
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935080"
---
# <a name="change-the-password-of-the-accounts-used-by-sql-server-sql-server-configuration-manager"></a>Modifier le mot de passe des comptes utilisés par SQL Server (Gestionnaire de configuration SQL Server)
  Cette rubrique explique comment modifier le mot de passe des comptes utilisés par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration SQL Server. Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécutent sur un ordinateur en tant que service, à l'aide des informations d'identification qui sont fournies au départ durant l'installation. Si l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est exécutée sous un compte de domaine et que le mot de passe de ce compte est modifié, le mot de passe utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être mis à jour pour refléter le nouveau mot de passe. Si le mot de passe n'est pas mis à jour, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut perdre l'accès à certaines ressources du domaine, et si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'arrête, le service ne redémarrera pas tant que le mot de passe n'aura pas été mis à jour.  
  
 Pour modifier les mots de passe d’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [Mot de passe expiré](../password-expired.md).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est l'outil conçu pour et autorisé à modifier les paramètres des services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le fait de modifier un service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide du Gestionnaire de contrôle des services Windows (**services.msc**) ne modifie pas toujours les paramètres nécessaires et peut empêcher le service de fonctionner correctement. Toutefois, dans un environnement cluster, après avoir modifié le mot de passe sur le nœud actif à l'aide du Gestionnaire de configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez modifier le mot de passe sur le nœud passif à l'aide du Gestionnaire de contrôle des services.  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Vous devez être administrateur de l'ordinateur pour modifier le mot de passe utilisé par un service.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### <a name="to-change-the-password-used-by-the-sql-server-database-engine-service"></a>Pour modifier le mot de passe utilisé par le service SQL Server (moteur de base de données)  
  
1.  Cliquez sur le bouton **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
    > [!NOTE]  
    >  Étant donné que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un composant logiciel enfichable pour le programme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console et non pas un programme autonome, le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’apparaît pas en tant qu’application dans les versions plus récentes de Windows.  
    >   
    >  -   **Windows 10**:  
    >          Pour ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, dans la **page de démarrage**, tapez SQLServerManager12. msc (pour [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ). Pour les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , remplacez 12 par un nombre plus petit. Le fait de cliquer sur SQLServerManager12.msc ouvre le Gestionnaire de Configuration. Pour épingler le Configuration Manager à la page de démarrage ou à la barre des tâches, cliquez avec le bouton droit sur SQLServerManager12. msc, puis cliquez sur **ouvrir l’emplacement du fichier**. Dans l’Explorateur de fichiers Windows, cliquez avec le bouton droit sur SQLServerManager12. msc, puis cliquez sur **épingler pour démarrer** ou **Épingler à la barre des tâches**.  
    > -   **Windows 8**:  
    >          Pour ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, dans l’icône **Rechercher** , sous **applications**, tapez **SQLServerManager \<version> . msc** , par exemple `SQLServerManager12.msc` , puis appuyez sur **entrée**.  
  
2.  Dans le Gestionnaire de configuration SQL Server, cliquez sur **Services SQL Server**.  
  
3.  Dans le volet d’informations, cliquez avec le bouton droit sur **SQL Server (** \<instancename> **)**, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue Propriétés de **SQL Server (** \<instancename> **)** , sous l’onglet ouvrir une session, pour le compte figurant dans la zone **nom du compte** , tapez le nouveau mot de passe dans les zones **mot** de passe et confirmer le **mot de passe** , puis cliquez sur **OK**.  
  
     Le mot de passe prend effet immédiatement, sans qu'il soit nécessaire de redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
#### <a name="to-change-the-password-used-by-the-sql-server-agent-service"></a>Pour modifier le mot de passe utilisé par le service SQL Server Agent  
  
1.  Cliquez sur le bouton **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
2.  Dans le Gestionnaire de configuration SQL Server, cliquez sur **Services SQL Server**.  
  
3.  Dans le volet d’informations, cliquez avec le bouton droit sur **SQL Server Agent (** \<instancename> **)**, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue Propriétés de **SQL Server Agent (** \<instancename> **)** , sous l’onglet ouvrir une session, pour le compte figurant dans la zone **nom du compte** , tapez le nouveau mot de passe dans les zones **mot** de passe et confirmer le **mot de passe** , puis cliquez sur **OK**.  
  
     Sur une instance autonome de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le mot de passe prend effet immédiatement, sans redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sur une instance cluster, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut mettre la ressource [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hors connexion, et nécessite un redémarrage.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures concernant la gestion des services &#40;Gestionnaire de configuration SQL Server&#41;](../managing-services-how-to-topics-sql-server-configuration-manager.md)  
  
  
