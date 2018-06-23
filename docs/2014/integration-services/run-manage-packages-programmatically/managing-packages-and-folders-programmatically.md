---
title: Gestion des packages et des dossiers par programmation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 08eb3bbd5ea03b7744daa8507164576c0700f0f8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140783"
---
# <a name="managing-packages-and-folders-programmatically"></a>Gestion des packages et des dossiers par programme
  Lorsque vous travaillez par programme avec des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez avoir besoin de déterminer si un package ou un dossier individuel existe, ou de gérer les dossiers dans lesquels les packages sont stockés. La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> de l'espace de noms <xref:Microsoft.SqlServer.Dts.Runtime> fournit différentes méthodes pour répondre à ces impératifs.  
  
##  <a name="exists"></a> Détermination de l’existence d’un package ou dossier  
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
  

  
##  <a name="managing"></a> Gestion des packages et des dossiers  
 La classe <xref:Microsoft.SqlServer.Dts.Runtime.Application> de l'espace de noms <xref:Microsoft.SqlServer.Dts.Runtime> fournit des méthodes supplémentaires pour gérer les packages et les dossiers dans lesquels ils sont stockés.  
  
###  <a name="managing_rempkg"></a> Suppression d’un package  
 Pour supprimer un package enregistré par programme, appelez l'une des méthodes suivantes :  
  
|Emplacement de stockage|Méthode à appeler|  
|----------------------|--------------------|  
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|  
  

  
###  <a name="managing_create"></a> Création d’un dossier  
 Pour créer un dossier de stockage par programme, appelez l'une des méthodes suivantes :  
  
|Emplacement de stockage|Méthode à appeler|  
|----------------------|--------------------|  
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|  
  

  
###  <a name="managing_remfldr"></a> Suppression d’un dossier  
 Pour supprimer un dossier de stockage par programme, appelez l'une des méthodes suivantes :  
  
|Emplacement de stockage|Méthode à appeler|  
|----------------------|--------------------|  
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|  
  
  
  
###  <a name="managing_rename"></a> Renommage d’un dossier  
 Pour renommer un dossier de stockage par programme, appelez l'une des méthodes suivantes :  
  
|Emplacement de stockage|Méthode à appeler|  
|----------------------|--------------------|  
|Magasin de packages SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|  
  

  
![Icône Integration Services (petite)](../media/dts-16.gif "icône Integration Services (petite)")**restent jusqu'à la Date avec Integration Services** <br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de packages &#40;Service SSIS&#41;](../service/package-management-ssis-service.md)   
 [Énumération des packages disponibles par programmation](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  