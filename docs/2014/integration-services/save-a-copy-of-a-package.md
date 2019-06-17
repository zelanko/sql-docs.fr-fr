---
title: Enregistrer une copie d’un Package | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 21482a20-e420-4452-b7eb-8f9fa1929f31
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bdd8754ac3d4a63e038218c054d064f20485344b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66056264"
---
# <a name="save-a-copy-of-a-package"></a>Enregistrer une copie d'un package
  Cette procédure décrit comment enregistrer une copie d’un package dans le système de fichiers, dans le magasin de packages ou dans la base de données **msdb** dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Lorsque vous spécifiez un emplacement dans lequel enregistrer la copie du package, vous pouvez également mettre à jour le nom de celui-ci.  
  
 Le magasin de packages peut comprendre à la fois la base de données **msdb** et les dossiers du système de fichiers, uniquement la base de données **msdb**, ou uniquement les dossiers du système de fichiers. Dans la base de données **msdb**, les packages sont enregistrés dans la table **sysssispackages** . Cette table comprend une colonne **folderid** qui identifie le dossier logique auquel le package appartient. Les dossiers logiques permettent de regrouper les packages enregistrés dans la base de données **msdb** , à l’image des dossiers du système de fichiers qui permettent de regrouper les packages enregistrés dans le système de fichiers. Les lignes de la table **sysssispackagefolders** de la base de données **msdb** définissent les dossiers.  
  
 Si la base de données **msdb** n’est pas définie dans le cadre du magasin de packages, vous pouvez néanmoins associer les packages aux dossiers logiques existants en sélectionnant SQL Server dans l’option **Chemin d’accès au package** .  
  
> [!NOTE]  
>  Pour pouvoir enregistrer une copie du package, le package doit être ouvert dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
### <a name="to-save-a-copy-of-a-package"></a>Pour enregistrer une copie d'un package  
  
1.  Dans l'Explorateur de solutions, double-cliquez sur le package dont vous voulez enregistrer une copie.  
  
2.  Dans le menu **Fichier**, cliquez sur **Enregistrer une copie de \<fichier_package> sous**.  
  
3.  Dans la boîte de dialogue **Enregistrer une copie du package**, sélectionnez l’emplacement d’un package dans la liste **Emplacement du package**.  
  
4.  Si l’emplacement est **SQL Server** ou **Magasin de packages SSIS**, indiquez un nom de serveur.  
  
5.  Si vous enregistrez une copie du package dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], indiquez le type d'authentification et, si vous utilisez l'authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , indiquez un nom d'utilisateur et un mot de passe.  
  
6.  Pour spécifier le chemin du package, tapez le chemin ou cliquez sur le bouton Parcourir **(...)** pour indiquer l’emplacement du package. Le nom par défaut du package est Package. Le cas échéant, attribuez au package un nom qui réponde mieux à vos besoins.  
  
     Si vous sélectionnez **SQL Server** dans l’option **Chemin d’accès au package** , le chemin du package comprend les dossiers logiques enregistrés dans la base de données **msdb** et le nom du package. Par exemple, si le package DownloadMonthlyData est associé au sous-dossier Finance du dossier MSDB (nom par défaut du dossier logique racine dans la base de données **msdb**), le chemin du package nommé DownloadMonthlyData est MSDB/Finance/DownloadMonthlyData.  
  
     Si vous sélectionnez **Magasin de packages SSIS** dans l’option **Chemin d’accès au package** , le chemin du package comprend le dossier géré par le service Integration Services. Par exemple, si le package UpdateDeductions se trouve dans le sous-dossier HumanResources du dossier de système de fichiers géré par le service, le chemin d'accès au package est /File System/HumanResources/UpdateDeductions ; de même, si le package PostResumes est associé au sous-dossier HumanResources du dossier MSDB, le chemin d'accès au package est MSDB/HumanResources/PostResumes.  
  
     Si vous sélectionnez **Système de fichiers** dans l’option **Chemin d’accès au package** , le chemin du package se compose de l’emplacement dans le système de fichiers et du nom de fichier. Par exemple, si le nom du package est UpdateDemographics, le chemin d'accès au package est C:\HumanResources\Quarterly\UpdateDemographics.dtsx.  
  
7.  Vérifiez le niveau de protection du package.  
  
8.  Si vous le souhaitez, cliquez sur le bouton **(...)** en regard de la zone **Niveau de protection** pour changer le niveau de protection.  
  
    -   Dans la boîte de dialogue **Niveau de protection du package** , sélectionnez un niveau de protection différent.  
  
    -   Cliquez sur **OK**.  
  
9. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Packages Integration Services &#40;SSIS&#41;](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Configuration de l’intégration des Services Service &#40;Service SSIS&#41;](service/integration-services-service-ssis-service.md)  
  
  
