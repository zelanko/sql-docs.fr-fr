---
title: Paramètres d’informations de périphérique pour l’image | Microsoft Docs
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- images [Reporting Services], rendering
- device information settings [Reporting Services], IMAGE rendering
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 295784ba9f2c14ce0f73f9639ec6ed129e447e76
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "65503078"
---
# <a name="image-device-information-settings"></a>Paramètres d'informations de périphérique pour l'image
  Le tableau suivant répertorie les paramètres des informations de périphérique qui permettent un rendu du rapport au format IMAGE.  
  
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
|**OutputFormat**|Un des formats de sortie [!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) pris en charge : **BMP**, **EMF**, **GIF**, **JPEG**, **PNG**ou **TIFF**.|  
|**PageHeight**|Hauteur de page, exprimée en pouces, à définir pour le rapport. Vous devez inclure un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **11in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PageWidth**|Largeur de page, exprimée en pouces, à définir pour le rapport. Vous devez inclure un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **8.5in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PrintDpiX**|Résolution horizontale de l'image de sortie. La valeur par défaut est **300**. S’applique au format de sortie Enhanced MetaFile (**EMF**).|  
|**PrintDpiY**|Résolution verticale de l'image de sortie. La valeur par défaut est **300**. S’applique au format de sortie Enhanced MetaFile (**EMF**).|  
|**StartPage**|Première page du rapport à restituer. Lorsque ce paramètre a pour valeur **0** , cela signifie que toutes les pages sont restituées. La valeur par défaut est **1**.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
