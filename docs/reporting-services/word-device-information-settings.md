---
title: "Param&#232;tres d&#39;informations de p&#233;riph&#233;rique Word | Microsoft Docs"
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
  - "Word [Reporting Services]"
  - "paramètres d’informations sur l’appareil [Reporting Services], Word"
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
caps.latest.revision: 7
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 7
---
# Param&#232;tres d&#39;informations de p&#233;riph&#233;rique Word
  Le tableau suivant répertorie les paramètres d'informations de périphérique qui permettent un rendu au format [!INCLUDE[ofprword](../includes/ofprword-md.md)] .  
  
|Paramètre|Valeur|  
|-------------|-----------|  
|**Ajustement automatique**|**Faux**. L’ajustement automatique a la valeur **false** sur tous les tableaux Word.<br /><br /> **Vrai**. L’ajustement automatique a la valeur **true** sur chaque tableau Word.<br /><br /> **Jamais**. Les valeurs d'ajustement automatique ne sont pas définies sur les tableaux Word et le comportement par défaut de Word est rétabli.<br /><br /> **Par défaut**. L'ajustement automatique est défini sur les tableaux qui sont plus étroits que la zone de dessin physique (largeur de page physique, marges exclues) par page logique.|  
|**ExpandToggles**|Indique si tous les éléments pouvant être activés ou désactivés doivent être rendus dans leur état complètement développé. La valeur par défaut est **false**.|  
|**FixedPageWidth**|Indique si la largeur de page écrite dans le fichier DOC peut croître pour accommoder la largeur de la page la plus grande dans le corps du rapport. La valeur par défaut est **false**.|  
|**OmitHyperlinks**|Indique s'il faut omettre l'action de lien hypertexte sur tous les éléments dans lesquels elle est définie. La valeur par défaut est **false**|  
|**OmitDrillthroughs**|Indique s'il faut omettre l'action d'extraction sur tous les éléments dans lesquels elle est définie. La valeur par défaut est **false**.|  
  
## Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d'extension de rendu dans RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  