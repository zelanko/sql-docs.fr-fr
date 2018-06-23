---
title: Droponlymode, élément (DTA) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6316124a589b09d8b8dab39f866b9ce4585fcb9e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139713"
---
# <a name="droponlymode-element-dta"></a>DropOnlyMode, élément (Assistant Paramétrage de base de données)
  Spécifie que l'Assistant Paramétrage du moteur de base de données doit supprimer uniquement les index, les vues indexées ou les partitions existantes pendant la session de paramétrage. Aucune nouvelle structure PDS n'est pas prise en compte lorsque cette option de paramétrage est spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Facultatif. Peut être utilisé qu’une seule fois pour chaque `TuningOptions` élément. Ne peut pas être utilisé si les éléments suivants sont spécifiés dans le `TuningOptions` élément :<br /><br /> [Featureset, élément &#40;DTA&#41;](featureset-element-dta.md)<br /><br /> [Partitioning, élément &#40;DTA&#41;](partitioning-element-dta.md)<br /><br /> [L’élément KeepExisting &#40;Assistant Paramétrage de base de données&#41;](keepexisting-element-dta.md) est défini sur **ALL**|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Tuningoptions, élément &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la `TuningOptions` section d’un fichier d’entrée Database Engine Tuning Advisor XML où le `DropOnlyMode` est spécifié. Dans cet exemple, la durée de paramétrage est limitée à 24 heures (1440 minutes) et tous les index cluster et non cluster existants sont pris en compte en vue de leur suppression :  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  