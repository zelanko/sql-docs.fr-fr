---
title: Paramètres d’informations de périphérique Excel | Microsoft Docs
description: Découvrez les différents paramètres d’informations de périphérique concernant le rendu au format Microsoft Excel.
ms.date: 01/23/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c4d84c98923a3cee94f64fed863e621821bd7a39
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245128"
---
# <a name="excel-device-information-settings"></a>Paramètres d'informations de périphérique Excel
  Le tableau suivant répertorie les paramètres d'informations de périphérique qui permettent un rendu au format [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .  
  
|Paramètre|Valeur|  
|-------------|-----------|  
|**OmitDocumentMap**|Indique s'il faut omettre l'explorateur de documents pour les rapports qui le prennent en charge. La valeur par défaut est **false**.|  
|**OmitFormulas**|Indique s'il faut omettre des formules du rapport rendu. La valeur par défaut est **false**.|  
|**SimplePageHeaders**|Indique si l'en-tête de page du rapport est rendu dans l'en-tête de page Excel. La valeur **false** indique que l’en-tête de page est rendu dans la première ligne de la feuille de calcul. La valeur par défaut est **false**.|  
|**DynamicImageDpi**|Résolution d’images dynamiques comme des graphiques, des jauges et des cartes. La valeur par défaut est **96**. (Disponible dans le serveur de rapports Power BI (Janvier 2020) et versions ultérieures)|  

  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
