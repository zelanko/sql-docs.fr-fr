---
title: Le Format du fichier de sortie XML (ssbdiagnose) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9b8f29b17e54c0abf406ee30ad542d960d4556ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142939"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Format du fichier de sortie XML (ssbdiagnose)
  La sortie de l’utilitaire **ssbdiagnose** est écrite dans un fichier XML lorsque vous l’exécutez avec le commutateur **-XML** . Le fichier de sortie XML répertorie les informations d'en-tête et les erreurs identifiées dans la configuration [!INCLUDE[ssSB](../../includes/sssb-md.md)] ou la conversation analysée. Vous pouvez écrire une application qui analyse ou effectue un rapport sur les erreurs répertoriées dans le fichier. Vous pouvez également consulter le fichier XML dans tout éditeur XML, comme le bloc-notes XML.  
  
 Un fichier de sortie de **ssbdiangose** contient un élément racine DiagnosticInformation avec deux types enfants :  
  
-   Un élément Banner contenant les informations d'en-tête.  
  
-   Un élément Issue pour chaque problème signalé par **ssbdiagnose**.  
  
## <a name="diagnosticinformation-root-element"></a>Élément racine DiagnosticInformation  
  
-   [DiagnosticInformation Élément &#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Élément Banner  
  
-   [Bannière élément &#40;ssbdiagnose&#41;](banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Élément Issue  
  
-   [Élément issue &#40;ssbdiagnose&#41;](issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire ssbdiagnose &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  