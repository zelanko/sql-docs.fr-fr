---
title: "Onlineindexoperation, élément (DTA) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d83fdbe16e2a461f2b30376f3f1e4178a01bf364
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="onlineindexoperation-element-dta"></a>OnlineIndexOperation, élément (Assistant Paramétrage de base de données)
  Spécifie si les index, les vues indexées ou les partitions recommandées par l'Assistant Paramétrage du moteur de base de données peuvent être créés en ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <OnlineIndexOperation>...</OnlineIndexOperation>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|**string**, aucune longueur maximale.|  
|**Valeurs autorisées**|**OFF**<br /> Aucune PDS ne peut être créée en ligne.<br /><br /> **ON**<br /> Toutes les PDS recommandées peuvent être créées en ligne.<br /><br /> **MIXED**<br /> L'Assistant Paramétrage du moteur de base de données tente de recommander des PDS pouvant être créées en ligne lorsque cela est possible.<br /><br /> Utilisez une de ces valeurs avec cet élément. Si les index sont créés en ligne, le mot clé **ONLINE = ON** est ajouté à sa définition d’objet.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Ce paramètre est facultatif. Ne peut être utilisé qu’une seule fois pour l’élément **TuningOptions** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Tuningoptions, élément &#40; DTA &#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Exemple de fichier d’entrée XML simple &#40;Assistant Paramétrage de base de données&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

