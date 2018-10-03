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
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6737a32eb7597f8115a7ee6797bcf1aedbd006b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220779"
---
# <a name="image-device-information-settings"></a>Paramètres d'informations de périphérique pour l'image
  Le tableau suivant répertorie les paramètres des informations de périphérique qui permettent un rendu du rapport au format IMAGE.  
  
|Paramètre|Valeur|  
|-------------|-----------|  
|**Colonnes**|Nombre de colonnes à définir pour le rapport. Cette valeur remplace les paramètres d'origine du rapport.|  
|**ColumnSpacing**|Espacement entre les colonnes à définir pour le rapport. Cette valeur remplace les paramètres d'origine du rapport.|  
|`DpiX`|Résolution horizontale de l'image de sortie. La valeur par défaut est **96**. S’applique aux `BMP`, `GIF`, `PNG`, et `TIFF` formats de sortie.|  
|`DpiY`|Résolution verticale de l'image de sortie. La valeur par défaut est **96**. S’applique aux `BMP`, `GIF`, `PNG`, et `TIFF` formats de sortie.|  
|**EndPage**|Dernière page du rapport à restituer. La valeur par défaut correspond à la valeur définie pour `StartPage`.|  
|**MarginBottom**|Valeur de marge inférieure, exprimée en pouces, à définir pour le rapport. Vous devez inclure une valeur entière ou décimale suivie de « in » (par exemple, `1in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginLeft**|Valeur de marge de gauche, exprimée en pouces, à définir pour le rapport. Vous devez inclure une valeur entière ou décimale suivie de « in » (par exemple, `1in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginRight**|Valeur de marge de droite, exprimée en pouces, à définir pour le rapport. Vous devez inclure une valeur entière ou décimale suivie de « in » (par exemple, `1in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginTop**|Valeur de marge supérieure, exprimée en pouces, à définir pour le rapport. Vous devez inclure une valeur entière ou décimale suivie de « in » (par exemple, `1in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**OutputFormat**|Parmi les [!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) pris en charge les formats de sortie : `BMP`, `EMF`, `GIF`, `JPEG`, `PNG`, ou `TIFF`.|  
|**PageHeight**|Hauteur de page, exprimée en pouces, à définir pour le rapport. Vous devez inclure une valeur entière ou décimale suivie de « in » (par exemple, `11in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PageWidth**|Largeur de page, exprimée en pouces, à définir pour le rapport. Vous devez inclure une valeur entière ou décimale suivie de « in » (par exemple, `8.5in`). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PrintDpiX**|Résolution horizontale de l'image de sortie. La valeur par défaut est `300`. S’applique à Enhanced MetaFile (`EMF`) format de sortie.|  
|**PrintDpiY**|Résolution verticale de l'image de sortie. La valeur par défaut est `300`. S’applique à Enhanced MetaFile (`EMF`) format de sortie.|  
|`StartPage`|Première page du rapport à restituer. Lorsque ce paramètre a pour valeur `0`, cela signifie que toutes les pages sont restituées. La valeur par défaut est `1`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Transmission de paramètres d’informations de périphérique aux Extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
