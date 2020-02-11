---
title: Sélectionner l’emplacement de destination (Assistant Mise à niveau de packages SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectdestinationlocation.f1
ms.assetid: 89274a71-0ffe-4889-84df-f5a7d78459ef
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d891f456f9c4922b3c680913f767d4e9b14a76a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66056008"
---
# <a name="select-destination-location-ssis-package-upgrade-wizard"></a>Sélectionner l'emplacement de destination (Assistant Mise à niveau de packages SSIS)
  Utilisez la page **Sélectionner l’emplacement de destination** pour spécifier la destination dans laquelle enregistrer les packages mis à niveau.  
  
> [!NOTE]  
>  Cette page est disponible uniquement quand vous exécutez l’Assistant Mise à niveau de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou de l’invite de commandes.  
  
 **Pour exécuter l’Assistant Mise à niveau de packages SSIS**  
  
-   [Mettre à niveau des packages Integration Services à l'aide de l'Assistant Mise à niveau de packages SSIS](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a>Options statiques  
 **Enregistrer à l’emplacement source**  
 Enregistrez les packages mis à niveau dans le même emplacement que celui spécifié dans la page **Sélectionner l’emplacement source** de l’Assistant.  
  
 Si vous voulez que l’Assistant sauvegarde les packages d’origine quand ils sont stockés dans le système de fichiers, sélectionnez l’option **Enregistrer à l’emplacement source** . Pour plus d’informations, consultez [Mettre à niveau des packages Integration Services à l’aide de l’Assistant Mise à niveau de packages SSIS](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).  
  
 **Sélectionner un nouvel emplacement de destination**  
 Enregistrez les packages mis à niveau dans l'emplacement de destination qui est spécifié sur cette page.  
  
 **Source du package**  
 Spécifiez l'emplacement où les packages de mise à niveau doivent être stockés. Cette option a les valeurs répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Système de fichiers**|Indique que les packages mis à niveau doivent être enregistrés dans un dossier sur l'ordinateur local.|  
|**Magasin de packages SSIS**|Indique que les packages mis à niveau doivent être enregistrés dans le magasin de packages Integration Services. Le magasin de packages se compose de l'ensemble des dossiers du système de fichiers gérés par Integration Services. Pour plus d’informations, consultez [Gestion de packages &#40;Service SSIS&#41;](service/package-management-ssis-service.md).<br /><br /> La sélection de cette valeur affiche les options dynamiques **Source du package** correspondantes.|  
|**Microsoft SQL Server**|Indique que les packages mis à niveau doivent enregistrés dans une instance existante de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].<br /><br /> La sélection de cette valeur affiche les options **Source du package** dynamiques correspondantes.|  
  
 **Folder**  
 Tapez le nom d’un dossier dans lequel enregistrer les packages mis à niveau, ou cliquez sur **Parcourir** et recherchez le dossier.  
  
 **Parcourir**  
 Recherchez le dossier dans lequel les packages mis à niveau seront enregistrés.  
  
## <a name="package-source-dynamic-options"></a>Options dynamiques de la source du package  
  
### <a name="package-source--ssis-package-store"></a>Source du package = Magasin de packages SSIS  
 **Serveur**  
 Tapez le nom du serveur sur lequel les packages de mise à niveau seront enregistrés, ou sélectionnez un serveur dans la liste.  
  
### <a name="package-source--microsoft-sql-server"></a>Source du package = Microsoft SQL Server  
 **Serveur**  
 Tapez le nom du serveur sur lequel les packages de mise à niveau seront enregistrés, ou sélectionnez ce serveur dans la liste.  
  
 **Utiliser l’authentification Windows**  
 Permet d'utiliser l'authentification Windows pour se connecter au serveur.  
  
 **Utiliser l’authentification SQL Server**  
 Permet d’utiliser l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour se connecter au serveur. Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , vous devez fournir un nom d’utilisateur et un mot de passe.  
  
 **Nom d'utilisateur**  
 Tapez le nom d’utilisateur à utiliser pendant l’utilisation de l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour se connecter au serveur.  
  
 **Mot de passe**  
 Tapez le mot de passe à utiliser pendant l’utilisation de l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour se connecter au serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Mettre à niveau des packages Integration Services](install-windows/upgrade-integration-services-packages.md)  
  
  
