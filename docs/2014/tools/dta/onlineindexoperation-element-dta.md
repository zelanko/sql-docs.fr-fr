---
title: Onlineindexoperation, élément (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9bb877ae48153d4fabae13170eb5f072218012d6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62657214"
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
|**Type de données et longueur**|`string`, aucune longueur maximale.|  
|**Valeurs autorisées**|**OFF**<br /> Aucune PDS ne peut être créée en ligne.<br /><br /> **ON**<br /> Toutes les PDS recommandées peuvent être créées en ligne.<br /><br /> **MIXED**<br /> L'Assistant Paramétrage du moteur de base de données tente de recommander des PDS pouvant être créées en ligne lorsque cela est possible.<br /><br /> Utilisez une de ces valeurs avec cet élément. Si les index sont créés en ligne, le mot clé **ONLINE = ON** est ajouté à sa définition d’objet.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Facultatif. Si utilisé, est utilisable uniquement une fois pour le `TuningOptions` élément.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Élément TuningOptions &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Exemple de fichier d’entrée XML simple &#40;Assistant Paramétrage de base de données&#41;](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
