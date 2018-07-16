---
title: Assistant Création d’une base de données (Gestionnaire de configuration Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.createdbwiz.f1
ms.assetid: 45fe7a23-a46c-4d40-8bca-3431fbfc5c9d
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1c020e8c27a7e4e2e7d22eb5a89308ddab5b8112
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296689"
---
# <a name="create-database-wizard-master-data-services-configuration-manager"></a>Assistant Création d'une base de données (Gestionnaire de configuration des services de données de référence)
  Utilisez l'Assistant **Création d'une base de données** pour créer une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="database-server"></a>Serveur de base de données  
 Spécifiez les informations pour la connexion à une instance [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] locale ou distante pour héberger la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour la connexion à une instance distante, il doit être activé pour les connexions distantes.  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Instance SQL Server**|Spécifiez le nom de l’instance du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] qui doit héberger la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Il peut s'agir d'une instance par défaut ou nommée sur un ordinateur local ou distant. Spécifiez les informations en tapant :<br /><br /> un point (.) pour se connecter à l'instance par défaut sur votre ordinateur local ;<br /><br /> le nom du serveur ou l'adresse IP pour se connecter à l'instance par défaut sur l'ordinateur local ou distant spécifié ;<br /><br /> le nom du serveur ou l'adresse IP ainsi que le nom de l'instance pour se connecter à l'instance nommée sur l'ordinateur local ou distant spécifié. Spécifiez ces informations au format *nom_serveur*\\*nom_instance*.|  
|**Type d'authentification**|Sélectionnez le type d'authentification à utiliser lors de la connexion à l'instance SQL Server spécifiée. Les informations d'identification que vous utilisez pour vous connecter doivent faire partie du rôle serveur **sysadmin** pour l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifiée. Pour plus d’informations sur le rôle sysadmin, consultez [Rôles de niveau serveur](../relational-databases/security/authentication-access/server-level-roles.md). Les types d'authentification sont les suivants :<br /><br /> **Utilisateur actuel - Sécurité intégrée**: utilise l'authentification Windows intégrée pour la connexion à l'aide des informations d'identification du compte d'utilisateur Windows actuel. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] utilise les informations d’identification Windows de l’utilisateur qui s’est connecté à l’ordinateur et a ouvert l’application. Vous ne pouvez pas spécifier des informations d'identification Windows différentes dans l'application. Si vous souhaitez vous connecter avec des informations d'identification Windows différentes, vous devez ouvrir une session sur l'ordinateur sous l'identité de cet utilisateur, puis ouvrir le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].<br /><br /> **Compte SQL Server**: utilise un compte SQL Server pour se connecter. Quand vous sélectionnez cette option, les champs **Nom d’utilisateur** et **Mot de passe** sont activés et vous devez spécifier des informations d’identification pour un compte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifiée.|  
|**Nom d'utilisateur**|Spécifiez le nom du compte d'utilisateur qui sera utilisé pour se connecter à l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifiée. Le compte doit faire partie du rôle **sysadmin** sur l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifiée.<br /><br /> Lorsque le **Type d’authentification** est **Utilisateur actuel - Sécurité intégrée**, la zone **Nom d’utilisateur** est en lecture seule et affiche le nom du compte d’utilisateur Windows qui a ouvert une session sur l’ordinateur.<br /><br /> Lorsque le **Type d'authentification** est **Compte SQL Server**, la zone **Nom d'utilisateur** est activée et vous devez spécifier des informations d'identification pour un compte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifiée.|  
|**Mot de passe**|Spécifiez le mot de passe associé au compte d'utilisateur.<br /><br /> Lorsque le **Type d’authentification** est **Utilisateur actuel - Sécurité intégrée**, la zone **Mot de passe** est en lecture seule et les informations d’identification du compte d’utilisateur Windows spécifié sont utilisées pour la connexion.<br /><br /> Lorsque le **Type d'authentification** est **Compte SQL Server**, la zone **Mot de passe** est activée et vous devez spécifier le mot de passe associé au compte d'utilisateur spécifié.|  
|**Tester la connexion**|Vérifiez que le compte d'utilisateur spécifié peut se connecter à l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et que le compte a l'autorisation de créer une base de données des [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] pour cette instance. Si vous ne cliquez pas sur **Tester la connexion**, la connexion est testée quand vous cliquez sur **Suivant**.|  
  
## <a name="database"></a>Base de données  
 Spécifiez un nom de base de données et des options de classement pour la nouvelle base de données. Les classements dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fournissent les règles de tri et les propriétés de respect de la casse et des accents pour vos données. Les classements utilisés avec les types de données character, tels que char et varchar, déterminent la page de codes et les caractères correspondants qui peuvent être représentés pour ce type de données. Pour plus d’informations sur le classement de base de données, consultez [Prise en charge d’Unicode et du classement](../relational-databases/collations/collation-and-unicode-support.md).  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Nom de la base de données**|Spécifiez un nom pour la base de données des [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|  
|**Classement par défaut de SQL Server**|Sélectionnez cette option pour utiliser le paramètre de classement de base de données actuel de l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifiée pour la nouvelle base de données.|  
|**Classement Windows**|Spécifiez les paramètres de classement Windows à utiliser pour la nouvelle base de données. Les classements Windows définissent des règles de stockage des données caractères selon les paramètres régionaux Windows associés. Pour plus d’informations sur les classements Windows et les options associées, consultez [Nom de classement Windows &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql).<br /><br /> Remarque : la liste **Classement Windows** et les options associées sont activées uniquement après que vous avez désactivé la case à cocher **Utiliser le classement SQL Server par défaut** .|  
  
## <a name="administrator-account"></a>Compte d'administrateur  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Nom d'utilisateur**|Spécifiez un compte d’utilisateur de domaine pour être le [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] administrateur système. Pour toutes les [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] applications Web associées à cette base de données, cet utilisateur peuvent mettre à jour tous les modèles et toutes les données dans toutes les zones fonctionnelles. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).|  
  
## <a name="summary"></a>Résumé  
 Affiche un résumé des options sélectionnées. Passez vos sélections en revue, puis cliquez sur **Suivant** pour commencer à créer la base de données avec les paramètres spécifiés.  
  
## <a name="progress-and-finish"></a>État d'avancement et fin  
 Affiche l'état d'avancement du processus de création. Après avoir créé la base de données, cliquez sur **Terminer** pour fermer l'Assistant de base de données et retourner à la page **Bases de données** . La nouvelle base de données est sélectionnée et vous pouvez afficher et modifier ses paramètres système.  
  
## <a name="see-also"></a>Voir aussi  
 [Page Configuration de base de données &#40;Gestionnaire de configuration Master Data Services&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [Configurer le site Web et la base de données pour Master Data Services](../../2014/master-data-services/set-up-the-database-and-website-for-master-data-services.md)   
 [Exigences de base de données &#40;Master Data Services&#41;](install-windows/database-requirements-master-data-services.md)  
  
  
