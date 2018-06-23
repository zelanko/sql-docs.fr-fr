---
title: Partitioning, élément (DTA) | Documents Microsoft
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
- Partitioning element
ms.assetid: 9bc5d1d5-27a7-4434-966f-c3935794af27
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 379e5dae0c70278b7c0b576190faffea84c8fa19
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051391"
---
# <a name="partitioning-element-dta"></a>Partitioning, élément (Assistant Paramétrage de base de données)
  Contient le schéma de partitionnement que vous aimeriez que l'Assistant Paramétrage du moteur de base de données utilise durant l'analyse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <Partitioning>...</Partitioning>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|`string`, aucune longueur maximale.|  
|**Valeurs autorisées**|**NONE**<br /> Aucun partitionnement.<br /><br /> **FULL**<br /> Partitionnement complet. (Améliore les performances.)<br /><br /> **ALIGNED**<br /> Partitionnement aligné uniquement. (Améliore la gestion.)<br /><br /> Utilisez une seule de ces valeurs avec cet élément.<br /><br /> La valeur**ALIGNED** signifie que dans la recommandation générée par l’Assistant Paramétrage du moteur de base de données chaque index proposé est partitionné de la même façon que la table sous-jacente pour laquelle l’index est défini. Les index non-cluster sur une vue indexée sont alignés avec la vue indexée.|  
|**Valeur par défaut**|**NONE**|  
|**Occurrence**|Obligatoire une fois pour l'élément `TuningOptions`, excepté si l'élément `DropOnlyMode` est utilisé. Si `DropOnlyMode` est utilisé, vous ne pouvez pas utiliser `Partitioning`. Ces éléments s'excluent mutuellement.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[Tuningoptions, élément &#40;DTA&#41;](tuningoptions-element-dta.md)|  
|**Éléments enfants**|Aucun.|  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de cet élément, consultez [Exemple de fichier d’entrée XML simple &#40;Assistant Paramétrage de base de données&#41;](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  