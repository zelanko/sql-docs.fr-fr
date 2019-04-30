---
title: Paramètres d’informations de périphérique pour l’image | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- images [Reporting Services], rendering
- device information settings [Reporting Services], IMAGE rendering
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5db9c929c736029c3731443af56d15f3615e45f1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63260869"
---
# <a name="image-device-information-settings"></a>Paramètres d'informations de périphérique pour l'image
  Le tableau suivant répertorie les paramètres des informations de périphérique qui permettent un rendu du rapport au format IMAGE.  
  
|Paramètre|Value|  
|-------------|-----------|  
|**Colonnes**|Nombre de colonnes à définir pour le rapport. Cette valeur remplace les paramètres d'origine du rapport.|  
|**ColumnSpacing**|Espacement entre les colonnes à définir pour le rapport. Cette valeur remplace les paramètres d'origine du rapport.|  
|`DpiX`|Résolution horizontale de l'image de sortie. La valeur par défaut est **96**. S’applique aux `BMP`, `GIF`, `PNG`, et `TIFF` formats de sortie.|  
|`DpiY`|Résolution verticale de l'image de sortie. La valeur par défaut est **96**. S’applique aux `BMP`, `GIF`, `PNG`, et `TIFF` formats de sortie.|  
|**EndPage**|Dernière page du rapport à restituer. La valeur par défaut correspond à la valeur définie pour `StartPage`.|  
|**MarginBottom**|Valeur de marge inférieure, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l'abréviation « in » (par exemple, `1in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginLeft**|Valeur de marge de gauche, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l'abréviation « in » (par exemple, `1in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginRight**|Valeur de marge de droite, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l'abréviation « in » (par exemple, `1in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginTop**|Valeur de marge supérieure, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l'abréviation « in » (par exemple, `1in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**OutputFormat**|L'un des formats de sortie [!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) pris en charge : `BMP`, `EMF`, `GIF`, `JPEG`, `PNG` ou `TIFF`.|  
|**PageHeight**|Hauteur de page, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l'abréviation « in » (par exemple, `11in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PageWidth**|Largeur de page, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l'abréviation « in » (par exemple, `8.5in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PrintDpiX**|Résolution horizontale de l'image de sortie. La valeur par défaut est `300`. S’applique à Enhanced MetaFile (`EMF`) format de sortie.|  
|**PrintDpiY**|Résolution verticale de l'image de sortie. La valeur par défaut est `300`. S’applique à Enhanced MetaFile (`EMF`) format de sortie.|  
|`StartPage`|Première page du rapport à restituer. Lorsque ce paramètre a pour valeur `0`, cela signifie que toutes les pages sont restituées. La valeur par défaut est `1`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d'extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
