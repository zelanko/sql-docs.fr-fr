---
title: '&#39;nouveautés de Générateur de rapports pour SQL Server 2014 | Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8223c19b-4b0d-4b1d-a042-9a726c18e708
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35ac6191407e02a2dc15ab210c5e9276e761df75
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098680"
---
# <a name="what39s-new-in-report-builder-for-sql-server-2014"></a>&#39;nouveautés de Générateur de rapports pour SQL Server 2014
  
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] inclut plusieurs fonctionnalités [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
 Pour plus d’informations sur les fonctionnalités de cette [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] version pour d’autres produits et technologies, consultez [nouveautés de SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
> [!TIP]  
>  Pour obtenir les dernières informations et ressources sur les nouvelles fonctionnalités de cette version, consultez [Informations supplémentaires sur les nouveautés de SQL Server Reporting Services (SSRS)](https://go.microsoft.com/fwlink/?LinkId=207147).  
  
##  <a name="ExcelRenderer"></a>Convertisseur Excel pour Microsoft Excel 2007-2010 et Microsoft Excel 2003  
 L'extension de rendu Excel [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , nouvelle dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], restitue un rapport sous la forme d'un document Excel compatible avec [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010, ainsi qu'avec [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 moyennant l'installation préalable du Module de compatibilité pour formats de fichiers Microsoft Office Word, Excel et PowerPoint. Le format est Office Open XML et l'extension de fichier est .xlsx.  
  
 Cette extension de rendu Excel supprime les limitations de la version antérieure, compatible avec Excel 2003. Voici les améliorations apportées à l'extension de rendu :  
  
-   Le nombre maximal de lignes par feuille de travail est de 1 048 576.  
  
-   Le nombre maximal de colonnes par feuille de travail est de 16 384.  
  
-   Le nombre de couleurs autorisé dans une feuille de travail est approximativement de 16 millions (couleurs 24 bits).  
  
-   La compression ZIP réduit la taille des fichiers.  
  
 Pour plus d’informations, consultez [Exportation vers Microsoft Excel &#40;Générateur de rapports et SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).  
  
##  <a name="WordRenderer"></a>Convertisseur Word pour Microsoft Word 2007-2010 et Microsoft Word 2003  
 L'extension de rendu Word [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , nouvelle dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], restitue un rapport sous la forme d'un document Word compatible avec [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010, ainsi qu'avec [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2003 moyennant l'installation préalable du Module de compatibilité pour formats de fichiers [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Word, Excel et PowerPoint. Le format est Office Open XML et l'extension de fichier est .docx.  
  
 En plus de rendre les nouvelles fonctions de Word 2007-2010 disponibles dans les rapports exportés, les fichiers *.docx des rapports exportés paraissent plus petits. Les rapports exportés à l'aide du convertisseur Word sont généralement beaucoup plus petits que les mêmes rapports exportés à l'aide du convertisseur Word 2003.  
  
 Pour plus d’informations, consultez [Exportation vers Microsoft Word &#40;Générateur de rapports et SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
