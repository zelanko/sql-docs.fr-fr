---
title: Configuration requise pour l'application Web
description: Découvrez les conditions requises pour installer et exécuter l’application Web Master Data Services hébergée par Internet Information Services.
ms.custom: ''
ms.date: 02/13/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
keywords:
- master data services
ms.assetid: 9455d3cf-c1b7-4d48-8aff-7dc636ed5dc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 513e376199c6f53953d49b70eae17f8da916f6bf
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87362963"
---
# <a name="web-application-requirements-master-data-services"></a>Configuration requise pour l'application Web (Master Data Services)

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] est une application web hébergée par IIS (Internet Information Services). [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] fonctionne seulement dans Internet Explorer 9 ou ultérieur. Internet Explorer 8 et versions antérieures, Microsoft Edge et Chrome ne sont pas pris en charge.  

**Pour obtenir des instructions sur la façon d’installer et de configurer IIS**, consultez [Installation et configuration d’IIS](../../master-data-services/master-data-services-installation-and-configuration.md#InstallIIS).
  
 Utilisez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] pour créer et configurer l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] configure IIS sur l'ordinateur local, il est dont le mieux adapté aux tâches de configuration Web initiales. Par exemple, configurez un environnement [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] avec une application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] unique, ou configurez la première application web dans un déploiement par montée en puissance parallèle de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Utilisez les outils IIS pour effectuer des tâches plus complexes, telles que la configuration de plusieurs serveurs Web dans un déploiement avec montée en puissance parallèle.  
  
> [!NOTE]  
>  Tout ordinateur sur lequel vous installez les composants de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] doit disposer d'une licence. Pour plus d'informations, reportez-vous au Contrat de Licence Utilisateur Final (CLUF).  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="operating-system"></a>Système d’exploitation  
 Avant d’installer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], vérifiez les éléments requis suivants :    
    
-   [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)    
  
### <a name="microsoft-silverlight"></a>Microsoft Silverlight  
 Pour travailler dans l'application Web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , Silverlight 5 doit être installé sur l'ordinateur client. Si vous n'avez pas la version requise de Silverlight, vous êtes invité à l'installer lorsque vous accédez à une partie de l'application Web qui l'utilise. Vous pouvez installer Silverlight 5 à partir de [cet emplacement](https://go.microsoft.com/fwlink/?LinkId=243096).  
  
### <a name="role-and-role-services"></a>Rôle et services de rôle  
 Dans Windows Server 2012 ou Windows Server 2012 R2, vous pouvez utiliser le **Gestionnaire de serveur**, disponible dans Microsoft Management Console (MMC), pour installer le rôle **Serveur web (IIS)** et les services de rôle nécessaires.  
 
 
> [!IMPORTANT]  
>La**compression du contenu dynamique** est activée par défaut. Cela réduit considérablement la taille de la réponse xml et épargne des E/S réseau, mais le processeur est davantage sollicité.  Pour plus d’informations, consultez **[CTP 2.0] Performances améliorées** in [Nouveautés de Master Data Services &#40;MDS&#41;](../../master-data-services/what-s-new-in-master-data-services-mds.md).  
  
- Services Internet (IIS)
- Outils d’administration Web
- Console de gestion d’IIS
- Services World Wide Web
- Développement d'applications
- Extensibilité .NET 3.5
- Extensibilité .NET 4.5
- ASP.NET 3.5
- ASP.NET 4.5
- Extensions ISAPI
- Filtres ISAPI
- Fonctionnalités HTTP communes
- Document par défaut
- Exploration de répertoire
- Erreurs HTTP
- Contenu statique [Remarque : n’installez pas la publication WebDAV.]
- Intégrité et diagnostics
- Journalisation HTTP
- Observateur de demandes
- Performances
- Compression du contenu statique
- Sécurité
- Filtrage des demandes
- Authentification Windows
  
### <a name="features"></a>Fonctionnalités 
 Dans Windows Server 2012 et Windows Server 2012 R2, vous pouvez utiliser le **Gestionnaire de serveur** pour installer les fonctionnalités requises suivantes :  
  
- .NET Framework 3.5 (inclut .NET 2.0 et 3.0)
- .NET Framework 4.5 Advanced Services
- ASP.NET 4.5
- Services WCF
- Activation HTTP [Remarque : celle-ci est obligatoire.]
- Partage de port TCP
- Service d’activation des processus Windows
- Modèle de processus
- Environnement .NET
- API de configuration
- compression du contenu dynamique
  
 Voici un exemple de script PowerShell pour ajouter des fonctionnalités et des rôles serveur prérequis. Les fonctionnalités et rôles serveur prérequis varient en fonction de l’environnement.  
  
```powershell  
Install-WindowsFeature Web-Mgmt-Console, AS-NET-Framework, Web-Asp-Net, Web-Asp-Net45, Web-Default-Doc, Web-Dir-Browsing, Web-Http-Errors, Web-Static-Content, Web-Http-Logging, Web-Request-Monitor, Web-Stat-Compression, Web-Filtering, Web-Windows-Auth, NET-Framework-Core, WAS-Process-Model, WAS-NET-Environment, WAS-Config-APIs  
  
Install-WindowsFeature Web-App-Dev, NET-Framework-45-Features -IncludeAllSubFeature -Restart  
```  
  
 Pour plus d’informations sur la commande PowerShell, consultez [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature).  
  
### <a name="accounts-and-permissions"></a>Comptes et autorisations  
  
|Type|Description|  
|----------|-----------------|  
|Compte Windows|Vous devez ouvrir une session sur l'ordinateur serveur Web avec un compte Windows qui a l'autorisation de configurer des rôles, des services de rôle et des fonctionnalités Windows, et créer et gérer des pools d'applications, des sites Web et des applications Web dans IIS sur l'ordinateur local.|  
|Compte de service|Lorsque vous créez l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] dans [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], vous devez spécifier une identité pour le pool d'applications dans lequel elle s'exécute. Ce compte peut être différent du compte de service spécifié lors de la création de la base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .<br /><br /> Cette identité doit être un compte d'utilisateur de domaine et est ajoutée au rôle de base de données mds_exec dans la base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] pour l'accès aux bases de données. Pour plus d’informations, consultez [Connexions, utilisateurs et rôles de base de données](../../master-data-services/database-logins-users-and-roles-master-data-services.md). Ce compte est également ajouté à un groupe Windows [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , **MDS_ServiceAccounts**, qui est autorisé à accéder au répertoire de compilation temporaire, **MDSTempDir**, dans le système de fichiers. Pour plus d’informations, consultez [Autorisations d’accès aux dossiers et aux fichiers &#40;Master Data Services&#41;](../../master-data-services/folder-and-file-permissions-master-data-services.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)   
      
 [Créer une application Web Data Manager principale &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)   
 [Page Configuration web &#40;Gestionnaire de configuration de Master Data Services&#41;](../../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
