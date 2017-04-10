---
title: "Format du fichier de sortie XML (ssbdiagnose) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "format du fichier de sortie XML [ssbdiagnose]"
  - "ssbdiagnose"
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# Format du fichier de sortie XML (ssbdiagnose)
  La sortie de l’utilitaire **ssbdiagnose** est écrite dans un fichier XML lorsque vous l’exécutez avec le commutateur **-XML**. Le fichier de sortie XML répertorie les informations d'en-tête et les erreurs identifiées dans la configuration [!INCLUDE[ssSB](../../includes/sssb-md.md)] ou la conversation analysée. Vous pouvez écrire une application qui analyse ou effectue un rapport sur les erreurs répertoriées dans le fichier. Vous pouvez également consulter le fichier XML dans tout éditeur XML, comme le bloc-notes XML.  
  
 Un fichier de sortie de **ssbdiangose** contient un élément racine DiagnosticInformation avec deux types enfants :  
  
-   Un élément Banner contenant les informations d'en-tête.  
  
-   Un élément Issue pour chaque problème signalé par **ssbdiagnose**.  
  
## Élément racine DiagnosticInformation  
  
-   [Élément DiagnosticInformation &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)  
  
## Élément Banner  
  
-   [Élément Banner &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)  
  
## Élément Issue  
  
-   [Élément Issue &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)  
  
## Voir aussi  
 [Utilitaire ssbdiagnose &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  