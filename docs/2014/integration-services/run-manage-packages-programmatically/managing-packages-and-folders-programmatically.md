---
title: Gestion des packages et des dossiers par programmation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ae44d737f596b72dc535812a628740474f2a114f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964469"
---
# <a name="managing-packages-and-folders-programmatically"></a>Gestion des packages et des dossiers par programme
  Lorsque vous travaillez par programme avec des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez avoir besoin de déterminer si un package ou un dossier individuel existe, ou de gérer les dossiers dans lesquels les packages sont stockés. La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> de l'espace de noms <xref:Microsoft.SqlServer.Dts.Runtime> fournit différentes méthodes pour répondre à ces impératifs.  
  
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a> Détermination de l’existence d’un package ou dossier  
 Pour déterminer par programmation si un package enregistré existe, appelez l’une des méthodes suivantes avant de tenter de le charger et l’exécuter :  
  
|Emplacement de stockage|Méthode à appeler|  
|----------------------|--------------------|  
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|  
  
 Pour déterminer par programme si un dossier existe, appelez l'une des méthodes suivantes avant de tenter de répertorier les packages stockés dans ce dossier :  
  
|Emplacement de stockage|Méthode à appeler|  
|----------------------|--------------------|  
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|  
  

  
##  <a name="managing-packages-and-folders"></a><a name="managing"></a> Gestion des packages et des dossiers  
 La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> de l'espace de noms <xref:Microsoft.SqlServer.Dts.Runtime> fournit des méthodes supplémentaires pour gérer les packages et les dossiers dans lesquels ils sont stockés.  
  
###  <a name="removing-a-package"></a><a name="managing_rempkg"></a> Suppression d’un package  
 Pour supprimer un package enregistré par programme, appelez l'une des méthodes suivantes :  
  
|Emplacement de stockage|Méthode à appeler|  
|----------------------|--------------------|  
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|  
  

  
###  <a name="creating-a-folder"></a><a name="managing_create"></a> Création d’un dossier  
 Pour créer un dossier de stockage par programme, appelez l'une des méthodes suivantes :  
  
|Emplacement de stockage|Méthode à appeler|  
|----------------------|--------------------|  
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|  
  

  
###  <a name="removing-a-folder"></a><a name="managing_remfldr"></a> Suppression d’un dossier  
 Pour supprimer un dossier de stockage par programme, appelez l'une des méthodes suivantes :  
  
|Emplacement de stockage|Méthode à appeler|  
|----------------------|--------------------|  
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|  
  
  
  
###  <a name="renaming-a-folder"></a><a name="managing_rename"></a> Renommage d’un dossier  
 Pour renommer un dossier de stockage par programme, appelez l'une des méthodes suivantes :  
  
|Emplacement de stockage|Méthode à appeler|  
|----------------------|--------------------|  
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|  
  

  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Package Management &#40;service SSIS&#41;](../service/package-management-ssis-service.md)   
 [Énumération des packages disponibles par programme](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
