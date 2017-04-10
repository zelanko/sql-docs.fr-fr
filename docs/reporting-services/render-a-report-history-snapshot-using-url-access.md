---
title: "Rendre un instantan&#233; d&#39;historique de rapport &#224; l&#39;aide de l&#39;acc&#232;s URL | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "accès à l’URL [Reporting Services], historique de rapport"
  - "instantanés d'historique [Reporting Services]"
  - "données historiques [Reporting Services]"
  - "captures instantanées [Reporting Services], accès à l’URL"
  - "captures instantanées [Reporting Services], rendu de l’historique de rapport"
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
caps.latest.revision: 32
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 32
---
# Rendre un instantan&#233; d&#39;historique de rapport &#224; l&#39;aide de l&#39;acc&#232;s URL
  Vous pouvez effectuer le rendu d’un rapport reposant sur une capture instantanée d’historique de rapport en indiquant le paramètre *rs:Snapshot* et en définissant sa valeur sur un ID de capture instantanée valide. La valeur de ce paramètre doit être spécifiée au format AAAA-MM-JJTHH:MM:SS, conformément à la norme ISO 8601.  
  
 Si vous omettez ce paramètre, le rapport est rendu selon le paramétrage des options d'exécution de rapports et de gestion du cache du serveur de rapports. Pour plus d’informations sur l’exécution des rapports, consultez [Définir les propriétés de traitement d’un rapport](../reporting-services/report-server/set-report-processing-properties.md).  
  
##  Exemple  
 L'exemple suivant montre une URL qui extrait un instantané d'historique de rapport :  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## Voir aussi  
 [Accès URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Référence de paramètre d'accès URL](../reporting-services/url-access-parameter-reference.md)  
  
  