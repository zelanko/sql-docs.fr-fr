---
title: Paramètres d’informations de périphérique ATOM | Microsoft Docs
description: Découvrez les paramètres d’informations de périphérique concernant le rendu des rapports Reporting Services au format PPTX.
ms.date: 09/11/2015
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- render
- powerpoint
- pptx
- export
ms.assetid: 4dc2045f-8025-41a3-8f9d-5635fb24cf4a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a43b6ef919c75711af60a084e9019fa2d3b555b1
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247499"
---
# <a name="pptx-device-information-settings"></a>Paramètres d’informations de périphérique PPTX
  Le tableau ci-après répertorie les paramètres d’informations de périphérique qui permettent de restituer les rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] au format PPTX.  
  
|Paramètre|Valeur|  
|-------------|-----------|  
|**Colonnes**|Nombre de colonnes à définir pour le rapport. Cette valeur remplace les paramètres d'origine du rapport.|  
|**ColumnSpacing**|Espacement entre les colonnes à définir pour le rapport. Cette valeur remplace les paramètres d'origine du rapport.|  
|**DpiX**|Résolution horizontale de l'image de sortie. La valeur par défaut est **96**. S'applique aux formats de sortie **BMP**, **GIF**, **PNG**et **TIFF** .|  
|**DpiY**|Résolution verticale de l'image de sortie. La valeur par défaut est **96**. S'applique aux formats de sortie **BMP**, **GIF**, **PNG**et **TIFF** .|  
|**EndPage**|Dernière page du rapport à restituer. La valeur par défaut correspond à la valeur définie pour **StartPage**.|  
|**MarginBottom**|Valeur de marge inférieure, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **1in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginLeft**|Valeur de marge de gauche, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **1in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginRight**|Valeur de marge de droite, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **1in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginTop**|Valeur de marge supérieure, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **1in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PageHeight**|Hauteur de page, exprimée en pouces, à définir pour le rapport. Vous devez inclure un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **11in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PageWidth**|Largeur de page, exprimée en pouces, à définir pour le rapport. Vous devez inclure un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **8.5in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**StartPage**|Première page du rapport à restituer. Lorsque ce paramètre a pour valeur **0** , cela signifie que toutes les pages sont restituées. La valeur par défaut est **1**.|  
|**UseReportPageSize**|Si UseReportPageSize =**false**, la taille de diapositive par défaut correspond à la valeur par défaut de PowerPoint, à savoir 13,333” x 7,5” (proportions 16:9). Si UseReportPageSize = true, la taille de diapositive par défaut est la taille de page de définition du rapport.<br /><br /> La valeur par défaut est **false**<br /><br /> Notez que les paramètres PageWidth et PageHeight remplacent les valeurs de largeur et de hauteur par défaut.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
