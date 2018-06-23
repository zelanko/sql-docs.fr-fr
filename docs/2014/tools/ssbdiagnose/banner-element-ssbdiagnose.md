---
title: Banner (ssbdiagnose) d’élément | Documents Microsoft
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
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ccb62b49257c2f406bedb34e9bbf58c3bd40ffd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152733"
---
# <a name="banner-element-ssbdiagnose"></a>Élément Banner (ssbdiagnose)
  Identifie quel utilitaire a généré le fichier de sortie XML **ssbdiagnose** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a>Attributs des éléments  
  
|Attribute|Description|  
|---------------|-----------------|  
|`title`|Identifie l’utilitaire qui a généré le fichier de sortie XML **ssbdiagnose** .|  
|`product`|Identifie le produit qui a généré le fichier de sortie XML **ssbdiagnose** .|  
|`version`|Identifie quelle version de l'utilitaire a généré le fichier de sortie XML.|  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Se produit une fois par fichier de sortie XML **ssbdiagnose** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DiagnosticInformation Élément &#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Exemple d'élément Banner.  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire ssbdiagnose &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  