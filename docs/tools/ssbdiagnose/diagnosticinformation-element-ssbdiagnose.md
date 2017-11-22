---
title: "DiagnosticInformation Élément (ssbdiagnose) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d0eb4067dff120d996550b4ef5fb07ffb41e179
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="diagnosticinformation-element-ssbdiagnose"></a>Élément DiagnosticInformation (ssbdiagnose)
  L’élément **DiagnosticInformation** contient tous les éléments qui signalent les informations de diagnostic trouvées par l’utilitaire. **DiagnosticInformation** est l’élément racine d’un fichier de sortie XML **ssbdiagnostic** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## <a name="element-attributes"></a>Attributs des éléments  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Aucune**|Néant|  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Une fois par fichier de sortie XML **ssbdiagnose** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|Aucun.|  
|**Éléments enfants**|[Élément Banner &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)<br /><br /> [Élément Issue &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)|  
  
## <a name="remarks"></a>Notes  
 Pour plus d'informations sur les espaces de noms XML, consultez l'article [Namespaces in an XML Document](http://go.microsoft.com/fwlink/?LinkId=7341) dans la bibliothèque [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire ssbdiagnose &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
