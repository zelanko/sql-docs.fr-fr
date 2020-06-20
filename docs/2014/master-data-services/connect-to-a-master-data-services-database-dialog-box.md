---
title: Boîte de dialogue Connexion à une base de données Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.srvconnect.f1
ms.assetid: b2f8c9b9-c31e-4f0d-9095-978709423190
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 514b8910b1626eeb276882c379842d88f93ff45f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971979"
---
# <a name="connect-to-a-master-data-services-database-dialog-box"></a>Se connecter à la boîte de dialogue Base de données Master Data Services
  Utilisez la boîte de dialogue **Connexion à une base de données Master Data Services** pour sélectionner une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], cette boîte de dialogue est disponible à partir des pages suivantes :  
  
-   Dans la page **Configuration de la base de données** , cliquez sur **Sélectionner une base de données**. Utilisez cette boîte de dialogue pour sélectionner une base de données pour laquelle configurer les paramètres système.  
  
-   Dans la page **Configuration web** , sous **Associer l’application à une base de données**, cliquez sur **Sélectionner** pour sélectionner la base de données à associer à votre application ou site web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
## <a name="select-database"></a>Sélectionner une base de données  
 Spécifiez les informations pour la connexion à une instance [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] locale ou distante qui héberge la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Pour la connexion à une instance distante, il doit être activé pour les connexions distantes.  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Instance SQL Server**|Spécifiez le nom de l’instance du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] qui doit héberger la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Il peut s'agir d'une instance par défaut ou nommée sur un ordinateur local ou distant. Spécifiez les informations en tapant :<br /><br /> un point (.) pour se connecter à l'instance par défaut sur votre ordinateur local ;<br /><br /> le nom du serveur ou l'adresse IP pour se connecter à l'instance par défaut sur l'ordinateur local ou distant spécifié ;<br /><br /> le nom du serveur ou l'adresse IP ainsi que le nom de l'instance pour se connecter à l'instance nommée sur l'ordinateur local ou distant spécifié. Spécifiez ces informations au format *SERVER_NAME* \\ *instance_name*.|  
|**Type d’authentification**|Sélectionnez le type d’authentification à utiliser lors de la connexion à l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifiée. Les informations d’identification que vous utilisez pour la connexion déterminent les bases de données affichées dans la liste déroulante **Base de données des services de données de référence** . Les types d'authentification sont les suivants :<br /><br /> **Sécurité intégrée de l’utilisateur actuel**: utilise l’authentification Windows intégrée pour se connecter à l’aide des informations d’identification du compte d’utilisateur Windows actuel. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] utilise les informations d’identification Windows de l’utilisateur qui s’est connecté à l’ordinateur et a ouvert l’application. Vous ne pouvez pas spécifier des informations d'identification Windows différentes dans l'application. Si vous souhaitez vous connecter avec des informations d’identification Windows différentes, vous devez ouvrir une session sur l’ordinateur sous l’identité de cet utilisateur, puis ouvrir le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].<br /><br /> **Compte SQL Server**: utilise un compte SQL Server pour se connecter. Quand vous sélectionnez cette option, les champs **Nom d’utilisateur** et **Mot de passe** sont activés et vous devez spécifier des informations d’identification pour un compte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifiée.|  
|**Nom d'utilisateur**|Spécifiez le nom du compte d'utilisateur qui sera utilisé pour se connecter à l'instance SQL Server spécifiée. Le compte doit faire partie du rôle **sysadmin** sur l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifiée :<br /><br /> Lorsque le **type d’authentification** est **sécurité intégrée de l’utilisateur actuel**, la zone **nom d’utilisateur** est en lecture seule et affiche le nom du compte d’utilisateur Windows qui a ouvert une session sur l’ordinateur.<br /><br /> Lorsque le **Type d'authentification** est **Compte SQL Server**, la zone **Nom d'utilisateur** est activée et vous devez spécifier des informations d'identification pour un compte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifiée.|  
|**Mot de passe**|Spécifiez le mot de passe associé au compte d’utilisateur :<br /><br /> Lorsque le **type d’authentification** est **sécurité intégrée de l’utilisateur actuel**, la zone **mot de passe** est en lecture seule et les informations d’identification du compte d’utilisateur Windows spécifié sont utilisées pour la connexion.<br /><br /> Lorsque le **Type d'authentification** est **Compte SQL Server**, la zone **Mot de passe** est activée et vous devez spécifier le mot de passe associé au compte d'utilisateur spécifié.|  
|**Connexion**|Connectez-vous à l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec les informations d’identification spécifiées.|  
|**Base de données Master Data Services**|Affiche les bases de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] dans l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] spécifiée selon les critères suivants :<br /><br /> Lorsque l’utilisateur est un membre du rôle serveur **sysadmin** pour cette instance, toutes les bases de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] dans cette instance sont affichées.<br /><br /> Lorsque l’utilisateur est un membre du rôle de base de données **db_owner** pour toute base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] dans cette instance, ces bases de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] sont affichées.<br /><br /> <br /><br /> Pour plus d’informations sur les rôles SQL Server, consultez [Rôles de niveau serveur](../relational-databases/security/authentication-access/server-level-roles.md) et [Rôles au niveau de la base de données](../relational-databases/security/authentication-access/database-level-roles.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Page Configuration de la base de données &#40;Gestionnaire de configuration Master Data Services&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [Configurer la base de données et le site web de Master Data Services](set-up-the-database-and-website-for-master-data-services.md)  
  
  
