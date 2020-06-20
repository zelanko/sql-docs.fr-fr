---
title: Sélectionner l’emplacement source (Assistant Mise à niveau de packages SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectsourcelocation.f1
ms.assetid: 429f146e-edb4-4401-a225-f2c8468971c5
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 90cb7110a6b4e9372fe5397ba050f91535a58f94
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963672"
---
# <a name="select-source-location-ssis-package-upgrade-wizard"></a>Sélectionner l'emplacement source (Assistant Mise à niveau de packages SSIS)
  Utilisez la page **Sélectionner l’emplacement source** pour spécifier la source à partir de laquelle effectuer la mise à niveau de packages.  
  
> [!NOTE]  
>  Cette page est disponible uniquement quand vous exécutez l’Assistant Mise à niveau de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou de l’invite de commandes.  
  
 **Pour exécuter l'Assistant Mise à niveau de packages SSIS**  
  
-   [Mettre à niveau des packages Integration Services à l'aide de l'Assistant Mise à niveau de packages SSIS](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a>Options statiques  
 **Source du package**  
 Sélectionnez l'emplacement de stockage qui contient les packages à mettre à niveau. Cette option a les valeurs répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Système de fichiers**|Indique que les packages à mettre à niveau se trouvent dans un dossier sur l'ordinateur local.<br /><br /> Pour que l'Assistant sauvegarde les packages d'origine avant de les mettre à niveau, les packages d'origine doivent être stockés dans le système de fichiers. Pour plus d'informations, consultez la rubrique de procédure.|  
|**Magasin de packages SSIS**|Indique que les packages à mettre à niveau se trouvent dans le magasin de packages. Le magasin de packages se compose de l’ensemble des dossiers du système de fichiers gérés par le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Pour plus d’informations, consultez [Gestion de packages &#40;Service SSIS&#41;](service/package-management-ssis-service.md).<br /><br /> La sélection de cette valeur affiche les options dynamiques **Source du package** correspondantes.|  
|**Microsoft SQL Server**|Indique que les packages à mettre à niveau proviennent d’une instance existante de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].<br /><br /> La sélection de cette valeur affiche les options dynamiques **Source du package** correspondantes.|  
  
 **Dossier**  
 Tapez le nom d’un dossier qui contient les packages à mettre à niveau, ou cliquez sur **Parcourir** et recherchez le dossier.  
  
 **Parcourir**  
 Recherchez le dossier qui contient les packages à mettre à niveau.  
  
## <a name="package-source-dynamic-options"></a>Options dynamiques de la source du package  
  
### <a name="package-source--ssis-package-store"></a>Source du package = Magasin de packages SSIS  
 **Serveur**  
 Tapez le nom du serveur sur lesquels se trouvent les packages à mettre à niveau ou sélectionnez ce serveur dans la liste.  
  
### <a name="package-source--microsoft-sql-server"></a>Source du package = Microsoft SQL Server  
 **Serveur**  
 Tapez le nom du serveur sur lesquels se trouvent les packages à mettre à niveau ou sélectionnez ce serveur dans la liste.  
  
 **Utiliser l’authentification Windows**  
 Permet d'utiliser l'authentification Windows pour se connecter au serveur.  
  
 **Utiliser l'authentification SQL Server**  
 Permet d’utiliser l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour se connecter au serveur. Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , vous devez fournir un nom d’utilisateur et un mot de passe.  
  
 **Nom d'utilisateur**  
 Tapez le nom d’utilisateur que l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilisera pour se connecter au serveur.  
  
 **Mot de passe**  
 Tapez le mot de passe que l’authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilisera pour se connecter au serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Mettre à niveau des packages Integration Services](install-windows/upgrade-integration-services-packages.md)  
  
  
