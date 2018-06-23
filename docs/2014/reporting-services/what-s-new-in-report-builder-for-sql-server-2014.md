---
title: Ce que&#39;nouveauté dans le Générateur de rapports pour SQL Server 2014 | Documents Microsoft
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8223c19b-4b0d-4b1d-a042-9a726c18e708
caps.latest.revision: 13
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 8bf08740110d2b7517a692e0c7a7f53351767d54
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154096"
---
# <a name="what39s-new-in-report-builder-for-sql-server-2014"></a>Ce que&#39;nouveauté dans le Générateur de rapports pour SQL Server 2014
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] inclut plusieurs fonctionnalités [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
 Pour plus d’informations sur les fonctionnalités de cette version pour les autres [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] les produits et technologies, consultez [Nouveautés de SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
> [!TIP]  
>  Pour obtenir les dernières informations et ressources sur les nouvelles fonctionnalités de cette version, consultez [Informations supplémentaires sur les nouveautés de SQL Server Reporting Services (SSRS)](http://go.microsoft.com/fwlink/?LinkId=207147).  
  
##  <a name="ExcelRenderer"></a> Convertisseur Excel pour Microsoft Excel 2007-2010 et Microsoft Excel 2003  
 L'extension de rendu Excel [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], nouvelle dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], restitue un rapport sous la forme d'un document Excel compatible avec [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2007-2010, ainsi qu'avec [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 2003 moyennant l'installation préalable du Module de compatibilité pour formats de fichiers Microsoft Office Word, Excel et PowerPoint. Le format est Office Open XML et l'extension de fichier est .xlsx.  
  
 Cette extension de rendu Excel supprime les limitations de la version antérieure, compatible avec Excel 2003. Voici les améliorations apportées à l'extension de rendu :  
  
-   Le nombre maximal de lignes par feuille de travail est de 1 048 576.  
  
-   Le nombre maximal de colonnes par feuille de travail est de 16 384.  
  
-   Le nombre de couleurs autorisé dans une feuille de travail est approximativement de 16 millions (couleurs 24 bits).  
  
-   La compression ZIP réduit la taille des fichiers.  
  
 Pour plus d’informations, consultez [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).  
  
##  <a name="WordRenderer"></a> Convertisseur Word pour Microsoft Word 2007-2010 et Microsoft Word 2003  
 L'extension de rendu Word [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], nouvelle dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], restitue un rapport sous la forme d'un document Word compatible avec [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2007-2010, ainsi qu'avec [!INCLUDE[ofprword](../includes/ofprword-md.md)] 2003 moyennant l'installation préalable du Module de compatibilité pour formats de fichiers [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Word, Excel et PowerPoint. Le format est Office Open XML et l'extension de fichier est .docx.  
  
 En plus de rendre les nouvelles fonctions de Word 2007-2010 disponibles dans les rapports exportés, les fichiers *.docx des rapports exportés paraissent plus petits. Les rapports exportés à l'aide du convertisseur Word sont généralement beaucoup plus petits que les mêmes rapports exportés à l'aide du convertisseur Word 2003.  
  
 Pour plus d’informations, consultez [Exportation vers Microsoft Word &#40;Générateur de rapports et SSRS&#41;](report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  