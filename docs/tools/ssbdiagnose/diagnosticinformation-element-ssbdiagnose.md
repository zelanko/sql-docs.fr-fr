---
title: Élément DiagnosticInformation
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 06d67e0a20067390c14837221725fd4b27c8c337
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75257792"
---
# <a name="diagnosticinformation-element-ssbdiagnose"></a>Élément DiagnosticInformation (ssbdiagnose)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

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
|**Aucun**|N/A|  
  
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
 Pour plus d'informations sur les espaces de noms XML, consultez l'article [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) dans la bibliothèque [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire ssbdiagnose &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
