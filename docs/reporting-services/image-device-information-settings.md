---
title: "Param&#232;tres d&#39;informations de p&#233;riph&#233;rique pour l&#39;image | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "images [Reporting Services], rendu"
  - "paramètres d’informations sur l’appareil [Reporting Services], rendu d’image"
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
caps.latest.revision: 39
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 39
---
# Param&#232;tres d&#39;informations de p&#233;riph&#233;rique pour l&#39;image
  Le tableau suivant répertorie les paramètres des informations de périphérique qui permettent un rendu du rapport au format IMAGE.  
  
|Paramètre|Valeur|  
|-------------|-----------|  
|**Columns**|Nombre de colonnes à définir pour le rapport. Cette valeur remplace les paramètres d'origine du rapport.|  
|**ColumnSpacing**|Espacement entre les colonnes à définir pour le rapport. Cette valeur remplace les paramètres d'origine du rapport.|  
|**DpiX**|Résolution horizontale de l'image de sortie. La valeur par défaut est **96**. S'applique aux formats de sortie **BMP**, **GIF**, **PNG**et **TIFF** .|  
|**DpiY**|Résolution verticale de l'image de sortie. La valeur par défaut est **96**. S'applique aux formats de sortie **BMP**, **GIF**, **PNG**et **TIFF** .|  
|**EndPage**|Dernière page du rapport à restituer. La valeur par défaut correspond à la valeur définie pour **StartPage**.|  
|**MarginBottom**|Valeur de marge inférieure, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **1in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginLeft**|Valeur de marge de gauche, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **1in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginRight**|Valeur de marge de droite, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **1in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginTop**|Valeur de marge supérieure, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **1in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**OutputFormat**|Un des formats de sortie [!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) pris en charge : **BMP**, **EMF**, **GIF**, **JPEG**, **PNG** ou **TIFF**.|  
|**PageHeight**|Hauteur de page, exprimée en pouces, à définir pour le rapport. Vous devez inclure un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **11in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PageWidth**|Largeur de page, exprimée en pouces, à définir pour le rapport. Vous devez inclure un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, **8.5in**). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PrintDpiX**|Résolution horizontale de l'image de sortie. La valeur par défaut est **300**. S’applique au format de sortie Enhanced MetaFile (**EMF**).|  
|**PrintDpiY**|Résolution verticale de l'image de sortie. La valeur par défaut est **300**. S’applique au format de sortie Enhanced MetaFile (**EMF**).|  
|**StartPage**|Première page du rapport à restituer. Lorsque ce paramètre a pour valeur **0** , cela signifie que toutes les pages sont restituées. La valeur par défaut est **1**.|  
  
## Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d'extension de rendu dans RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  