---
title: Featureset, élément (DTA) | Microsoft Docs
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
- FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fb596ca38310bce4b9be6f1061952ebc2756fc73
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226509"
---
# <a name="featureset-element-dta"></a>FeatureSet, élément (Assistant Paramétrage de base de données)
  Contient les structures PDS (index ou vues indexées) que vous aimeriez que l'Assistant Paramétrage du moteur de base de données utilise durant l'analyse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <FeatureSet>...</FeatureSet>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|`string`, aucune longueur maximale.|  
|**Valeurs autorisées**|**IDX_IV**<br /> Index et vues indexées.<br /><br /> **IDX**<br /> Index uniquement.<br /><br /> **IV**<br /> Vues indexées uniquement.<br /><br /> **NCL_IDX**<br /> Index non-cluster uniquement.<br /><br /> Utilisez une de ces valeurs avec cet élément.|  
|**Valeur par défaut**|**IDX**|  
|**Occurrence**|Obligatoire une fois pour chaque élément `TuningOptions`, excepté si l'élément `DropOnlyMode` est utilisé. Si `DropOnlyMode` est utilisé, vous ne pouvez pas utiliser `FeatureSet`. Ces éléments s'excluent mutuellement.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[TuningOptions, élément &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Exemple de fichier d’entrée XML simple &#40;Assistant Paramétrage de base de données&#41;](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
