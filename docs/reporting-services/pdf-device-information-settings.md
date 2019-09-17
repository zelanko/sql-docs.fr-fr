---
title: Paramètres d’informations de périphérique PDF | Microsoft Docs
ms.date: 03/16/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], PDF rendering
- PDF [Reporting Services]
ms.assetid: 9a4aabe5-dbdc-4884-b999-1200983fee47
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5442980dd2f67cf72e301a82ae3730f90a173116
ms.sourcegitcommit: 75fe364317a518fcf31381ce6b7bb72ff6b2b93f
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70911328"
---
# <a name="pdf-device-information-settings"></a>Paramètres d'informations de périphérique PDF
  Le tableau suivant répertorie les paramètres d'informations de périphérique qui permettent un rendu des rapports au format PDF.  
  
|Paramètre|Valeur|  
|-------------|-----------|  
| **AccessiblePDF** | Indique s’il faut restituer un PDF accessible/marqué, plus volumineux, mais plus facile à lire et à parcourir par les lecteurs d’écran et autres technologies d’assistance. La valeur par défaut est **false**. [Disponible dans Power BI Report Server (mars 2018) et versions ultérieures] |
|**Colonnes**|Nombre de colonnes à définir pour le rapport. Cette valeur remplace les paramètres d'origine du rapport.|  
|**ColumnSpacing**|Espacement entre les colonnes à définir pour le rapport. Cette valeur remplace les paramètres d'origine du rapport.|  
|**DpiX**|Résolution du périphérique de sortie sur l'axe x.|  
|**DpiY**|Résolution du périphérique de sortie sur l'axe y.|  
|**EmbedFonts**|Indique s’il faut incorporer des polices dans le fichier PDF, dont la taille est supérieure, mais les polices de rapport sont restituées correctement pour tous les clients. La valeur **None** désactive l’incorporation des polices.|  
|**EndPage**|Dernière page du rapport à restituer. La valeur par défaut correspond à la valeur définie pour **StartPage**.|  
|**HumanReadablePDF**|Indique s’il faut restituer un fichier PDF décompressé, plus volumineux, mais plus facile à lire par l’utilisateur dans un éditeur de texte brut. La valeur par défaut est **false**.|  
|**MarginBottom**|Valeur de marge inférieure, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, 1in). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginLeft**|Valeur de marge de gauche, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, 1in). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginRight**|Valeur de marge de droite, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, 1in). Cette valeur remplace les paramètres d'origine du rapport.|  
|**MarginTop**|Valeur de marge supérieure, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, 1in). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PageHeight**|Hauteur de page, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l’abréviation « in » (par exemple, 11in). Cette valeur remplace les paramètres d'origine du rapport.|  
|**PageWidth**|Largeur de page, exprimée en pouces, à définir pour le rapport. Vous devez saisir un entier ou un nombre à virgule, puis l'abréviation « in » (par exemple, 8.5in). Cette valeur remplace les paramètres d'origine du rapport.|  
|**StartPage**|Première page du rapport à restituer. Lorsque ce paramètre a pour valeur **0** , cela signifie que toutes les pages sont restituées. La valeur par défaut est **1**.|  
  
## <a name="see-also"></a> Voir aussi  
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d'extension de rendu dans RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
