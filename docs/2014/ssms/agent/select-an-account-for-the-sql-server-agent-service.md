---
title: Sélectionner un compte pour le service SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- roles [SQL Server], SQL Server Agent
- SQL Server Agent, accounts
- startup accounts [SQL Server]
- SQL Server Agent service, accounts
- accounts [SQL Server], SQL Server Agent
- Windows groups [SQL Server Agent]
- SQL Server Agent, permissions
- members [SQL Server], SQL Server Agent service
- Windows domain accounts [SQL Server]
- security [SQL Server], SQL Server Agent
ms.assetid: fe658e32-9e6b-4147-a189-7adc3bd28fe7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9b2fd7a22c202b1210b17f86903fce32ec8d4b5b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68811082"
---
# <a name="select-an-account-for-the-sql-server-agent-service"></a>Sélectionner un compte pour le service SQL Server Agent
  Le compte de démarrage du service définit le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows dans le contexte duquel l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute, ainsi que ses autorisations réseau. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute dans le contexte d'un compte d'utilisateur spécifié. Pour sélectionner un compte pour le service de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , utilisez le Gestionnaire de configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour choisir l'une des options suivantes :  
  
-   **Compte intégré**. Vous pouvez choisir un compte dans la liste des comptes de service intégrés Windows suivants :  
  
    -   Compte **système local** . Le nom de ce compte est NT AUTHORITY\System. Ce compte puissant bénéficie d'un accès illimité à l'ensemble des ressources système locales. Il est membre du groupe **Administrateurs** Windows de l’ordinateur local et donc membre du rôle serveur fixe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **de** .  
  
        > [!IMPORTANT]  
        >  Le **Compte système local** est fourni pour des raisons de compatibilité descendante uniquement. Le compte système local dispose d'autorisations dont l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas besoin. Évitez d'exécuter l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec ce compte. Pour une sécurité optimale, utilisez un compte de domaine Windows disposant des autorisations répertoriées dans la section suivante, « Autorisations de compte de domaine Windows ».  
  
-   **Ce compte**. Cette option vous permet de spécifier le compte de domaine Windows dans le contexte duquel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent s'exécute. Nous vous recommandons de choisir un compte d’utilisateur Windows qui n’appartient pas au groupe **Administrateurs** de Windows. En revanche, certaines restrictions s’appliquent dans le cas de l’administration multiserveur quand le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent n’est pas membre du groupe **Administrateurs** local. Pour plus d'informations, consultez « Types de compte de service pris en charge » plus bas dans cette rubrique.  
  
## <a name="windows-domain-account-permissions"></a>Autorisations de compte de domaine Windows  
 Pour améliorer la sécurité, sélectionnez **Ce compte**, qui spécifie un compte de domaine Windows. Le compte de domaine Windows que vous spécifiez doit posséder les autorisations suivantes :  
  
-   Dans toutes les versions de Windows : autorisation de se connecter en tant que service (SeServiceLogonRight).  
  
> [!NOTE]  
>  Le compte du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être membre du groupe Accès compatible pré-Windows 2000 du contrôleur de domaine. Dans le cas contraire, les travaux des utilisateurs du domaine non membres du groupe Administrateurs de Windows échouent.  
  
-   Sur les serveurs Windows, le compte sous lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent s'exécute requiert les autorisations suivantes afin de prendre en charge les proxys de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Autorisation d'outrepasser le contrôle de parcours (SeChangeNotifyPrivilege).  
  
    -   Autorisation de remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege).  
  
    -   Autorisation de modifier les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege).  
  
    -   Autorisation de se connecter au moyen du type de connexion par traitement (SeBatchLogonRight).  
  
> [!NOTE]  
>  Si le compte n’a pas les autorisations requises pour prendre en charge les proxys, seuls les membres du rôle serveur fixe **sysadmin** pourront créer un travail.  
  
> [!NOTE]  
>  Pour recevoir des alertes WMI, le compte du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit posséder une autorisation sur l'espace de noms qui contient les événements WMI, ainsi que l'autorisation ALTER ANY EVENT NOTIFICATION.  
  
## <a name="sql-server-role-membership"></a>Appartenance aux rôles SQL Server  
 Le compte avec lequel le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent est exécuté doit être membre des rôles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suivants :  
  
-   Le compte doit être membre du rôle serveur fixe **sysadmin** .  
  
-   Pour utiliser le traitement de travaux multiserveur, le compte doit être membre du rôle de base de données **msdb****TargetServersRole** sur le serveur maître.  
  
## <a name="supported-service-account-types"></a>Types de comptes de service pris en charge  
 Le tableau ci-dessous répertorie les types de comptes Windows qui peuvent être utilisés pour le service de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Type de compte de service|Serveur non-cluster|Serveur en cluster|Contrôleur de domaine (non-cluster)|  
|--------------------------|---------------------------|----------------------|------------------------------------------|  
|
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Compte de domaine Windows (membre du groupe Administrateurs Windows)|Prise en charge|Prise en charge|Prise en charge|  
|Compte de domaine Windows (non administratif)|Pris en charge<sup>1</sup>|Pris en charge<sup>1</sup>|Pris en charge<sup>1</sup>|  
|Compte Service réseau (AUTORITE NT\NetworkService)|Pris en charge<sup>1, 3, 4</sup>|Non pris en charge|Non pris en charge|  
|Compte d'utilisateur local (non administratif)|Pris en charge<sup>1</sup>|Non pris en charge|Non applicable|  
|Compte système local (AUTORITE NT\System)|Pris en charge<sup>2</sup>|Non pris en charge|Pris en charge<sup>2</sup>|  
|Compte Service local (AUTORITE NT\LocalService)|Non pris en charge|Non pris en charge|Non pris en charge|  
  
 <sup>1</sup> Voir la limitation 1 ci-dessous.  
  
 <sup>2</sup> consultez la limitation 2 ci-dessous.  
  
 <sup>3</sup> consultez la limitation 3 ci-dessous.  
  
 <sup>4</sup> consultez la limitation 4 ci-dessous.  
  
### <a name="limitation-1-using-non-administrative-accounts-for-multiserver-administration"></a>Restriction 1 : utilisation de comptes non administratifs pour l'administration multiserveur  
 L'enregistrement de serveurs cibles auprès d'un serveur maître peut échouer en affichant le message d'erreur suivant : « L'opération d'enregistrement a échoué. »  
  
 Pour résoudre cette erreur, redémarrez les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d'informations, consultez [Démarrer, arrêter, suspendre, reprendre, redémarrer les services SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
### <a name="limitation-2-using-the-local-system-account-for-multiserver-administration"></a>Restriction 2 : utilisation du compte système local pour l'administration multiserveur  
 L'administration multiserveur est prise en charge lorsque le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent est exécuté sous le compte système local, seulement si le serveur maître et le serveur cible résident sur le même ordinateur. Si vous utilisez cette configuration, le message ci-dessous est retourné lorsque vous enregistrez les serveurs cibles auprès du serveur maître :  
  
 « Vérifiez que le compte de démarrage de l’agent pour *<nom_ordinateur_serveur_cible>* dispose des autorisations pour se connecter en tant que serveur cible. »  
  
 Vous pouvez ignorer ce message d'information. L'opération d'enregistrement doit se terminer correctement. Pour plus d’informations, consultez [Créer un environnement multiserveur](create-a-multiserver-environment.md).  
  
### <a name="limitation-3-using-the-network-service-account-when-it-is-a-sql-server-user"></a>Restriction 3 : utilisation du compte Service réseau pour un utilisateur SQL Server  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent peut ne pas démarrer si vous exécutez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sous le compte Service réseau et si ce dernier a l’autorisation d’ouvrir une session sur une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant qu’utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Pour résoudre ce problème, redémarrez l'ordinateur qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cela doit être effectué une seule fois.  
  
### <a name="limitation-4-using-the-network-service-account-when-sql-server-reporting-services-is-running-on-the-same-computer"></a>Restriction 4 : utilisation du compte Service réseau lorsque SQL Server Reporting Services s'exécute sur le même ordinateur  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent peut ne pas démarrer si vous exécutez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sous le compte Service réseau, alors que [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] s’exécute aussi sur le même ordinateur.  
  
 Pour résoudre ce problème, redémarrez l'ordinateur qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , puis redémarrez les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les services de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cela doit être effectué une seule fois.  
  
## <a name="common-tasks"></a>Tâches courantes  
 **Pour spécifier le compte de démarrage pour le service SQL Server Agent**  
  
-   [Définir le compte de démarrage du service pour SQL Server Agent &#40;Gestionnaire de configuration SQL Server&#41;](set-service-startup-account-sql-server-agent-sql-server-configuration-manager.md)  
  
 **Pour spécifier le profil de messagerie pour SQL Server Agent**  
  
-   [Configurer la messagerie SQL Server Agent en vue d’utiliser la messagerie de base de données](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
> [!NOTE]  
>  Utilisez le Gestionnaire de configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour spécifier que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit démarrer lorsque le système d'exploitation démarre.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   
 [Rubriques de procédures concernant la gestion des services &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)   
 [Implémenter la sécurité de l'Agent SQL Server](implement-sql-server-agent-security.md)  
  
  
