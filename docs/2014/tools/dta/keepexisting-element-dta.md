---
title: Keepexisting, élément (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 62f81fd7ebdd4cee35c09b685273bba2d14d135b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269875"
---
# <a name="keepexisting-element-dta"></a>KeepExisting, élément (Assistant Paramétrage de base de données)
  Spécifie les structures PDS (index, vues indexées ou partitions) que l'Assistant Paramétrage du moteur de base de données doit conserver lors de la génération de sa recommandation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|`string`, limite de longueur appliquée par le serveur.|  
|**Valeurs autorisées**|**NONE**<br /> Aucune structure existante.<br /><br /> **ALL**<br /> Toutes les structures existantes.<br /><br /> **ALIGNED**<br /> Toutes les structures alignées sur les partitions.<br /><br /> **CL_IDX**<br /> Tous les index cluster sur les tables.<br /><br /> **IDX**<br /> Tous les index cluster et non cluster sur les tables.<br /><br /> Utilisez une seule de ces valeurs avec cet élément.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Facultatif. Peut utiliser qu’une seule fois pour chaque `TuningOptions` élément.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[TuningOptions, élément &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Exemple de fichier d’entrée XML simple &#40;Assistant Paramétrage de base de données&#41;](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
