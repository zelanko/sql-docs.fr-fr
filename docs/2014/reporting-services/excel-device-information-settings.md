---
title: Paramètres d’informations de périphérique Excel | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5d1ec9b650592be41c8ae2f7043649c91ea78442
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63164577"
---
# <a name="excel-device-information-settings"></a>Paramètres d'informations de périphérique Excel
  Le tableau suivant répertorie les paramètres des informations de périphérique qui permettent un rendu au format [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .  
  
|Paramètre|Value|  
|-------------|-----------|  
|**OmitDocumentMap**|Indique s'il faut omettre l'explorateur de documents pour les rapports qui le prennent en charge. La valeur par défaut est `false`.|  
|**OmitFormulas**|Indique s'il faut omettre des formules du rapport rendu. La valeur par défaut est `false`.|  
|`SimplePageHeade`rs|Indique si l'en-tête de page du rapport est rendu dans l'en-tête de page Excel. La valeur `false` indique que l'en-tête de page est rendu dans la première ligne de la feuille de calcul. La valeur par défaut est `false`.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d'extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
