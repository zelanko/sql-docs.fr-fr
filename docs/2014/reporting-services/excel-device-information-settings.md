---
title: Paramètres d’informations de périphérique Excel | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
caps.latest.revision: 40
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 518033807ca52001a09a01136225f3a7594af7d2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143663"
---
# <a name="excel-device-information-settings"></a>Paramètres d'informations de périphérique Excel
  Le tableau suivant répertorie les paramètres des informations de périphérique qui permettent un rendu au format [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .  
  
|Paramètre|Valeur|  
|-------------|-----------|  
|**OmitDocumentMap**|Indique s'il faut omettre l'explorateur de documents pour les rapports qui le prennent en charge. La valeur par défaut est `false`.|  
|**OmitFormulas**|Indique s'il faut omettre des formules du rapport rendu. La valeur par défaut est `false`.|  
|`SimplePageHeade`RS|Indique si l'en-tête de page du rapport est rendu dans l'en-tête de page Excel. La valeur `false` indique que l’en-tête de page est rendu dans la première ligne de la feuille de calcul. La valeur par défaut est `false`.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passage de paramètres d’informations de périphérique aux Extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  