---
title: "Créer la boîte de dialogue d’Application Web (Gestionnaire de Configuration Master Data Services) | Documents Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.mds.configmanager.createapp.f1
ms.assetid: e045b41a-4836-47f6-8e78-2b09494b461f
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5fb6605ae951c83b70aa6bb0499be0d077b398c8
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="create-web-application-dialog-box-master-data-services-configuration-manager"></a>Boîte de dialogue Créer une application Web (Gestionnaire de configuration des services de données de référence)
  Utilisez la boîte de dialogue **Créer une application web** pour créer l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Cette application web est créée sur le site que vous avez sélectionné dans la page **Configuration web** .  
  
## <a name="web-application"></a>Application Web  
 Le serveur web sert le contenu pour cette application web à partir du dossier [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] **WebApplication** folder in the file system. Cet emplacement est spécifié pendant l’installation et, par défaut, le chemin d’accès est *lecteur*:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication.  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|Chemin d'accès virtuel|Sélectionnez le chemin d’accès virtuel sous lequel vous souhaitez créer l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Un chemin d'accès virtuel fait partie de l'URL utilisée pour accéder à une application Web.<br /><br /> Cette liste est filtrée pour afficher uniquement les chemins d’accès virtuels des applications sous lesquelles l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] peut être créée. Vous ne pouvez pas créer d’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sous une autre application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .|  
|Alias|Tapez un nom pour l’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ou utilisez le nom par défaut. Ce nom est utilisé dans une URL pour accéder à l’application web à partir d’un navigateur web.|  
  
## <a name="application-pool"></a>Pool d'applications  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Nom**|Tapez un nom convivial unique pour un nouveau pool d'applications ou utilisez le nom par défaut. L’application web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] est ajoutée à ce pool d’applications.<br /><br /> Les pools d'applications fournissent des limites qui empêchent les applications dans un pool d'applications d'affecter les applications dans un autre pool d'applications.|  
|**Nom d'utilisateur**|Tapez un domaine et un nom d'utilisateur à partir d'Active Directory. Ce compte est l'identité du pool d'applications dans lequel s'exécute l'application Web. Ce compte doit être identique au compte spécifié en tant que compte de service au moment de la création de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> Ce compte est ajouté au rôle de base de données mds_exec dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] pour l'accès à la base de données. Pour plus d’informations, consultez [Connexions, utilisateurs et rôles de base de données &#40;Master Data Services&#41;](../master-data-services/database-logins-users-and-roles-master-data-services.md). Il est également ajouté à un groupe Windows [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], **MDS_ServiceAccounts**, qui est autorisé à accéder au répertoire de compilation temporaire, **MDSTempDir**, dans le système de fichiers. Pour plus d’informations, consultez [Autorisations d’accès aux dossiers et aux fichiers &#40;Master Data Services&#41;](../master-data-services/folder-and-file-permissions-master-data-services.md).|  
|**Mot de passe**|Tapez le mot de passe du compte d'utilisateur spécifié.|  
|**Confirmer le mot de passe**|Retapez le mot de passe du compte d'utilisateur spécifié. Les champs **Mot de passe** et **Confirmer le mot de passe** doivent contenir le même mot de passe.|  
  
## <a name="see-also"></a>Voir aussi  
 [Page Configuration web &#40;Gestionnaire de configuration de Master Data Services&#41;](../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)   
[Installation de Master Data Services et la Configuration](../master-data-services/master-data-services-installation-and-configuration.md) [Web configuration requise pour Application &#40; Master Data Services &#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md)   
 [Créer une Application Web Master Data Manager &#40; Master Data Services &#41;](../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  
