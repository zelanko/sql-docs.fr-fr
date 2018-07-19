---
title: SUPPRIMER LA STRUCTURE D’EXPLORATION DE DONNÉES (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b83de343e94c9263ba1ca6c6c8f09be90f3793b2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052317"
---
# <a name="drop-mining-structure-dmx"></a>DROP MINING STRUCTURE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Supprime la structure d'exploration de données spécifiée de la base de données. Tous les modèles d'exploration de données associés à cette structure sont également supprimés de la base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP MINING STRUCTURE <structure>  
```  
  
## <a name="arguments"></a>Arguments  
 *structure*  
 Identificateur de la structure  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime la structure d'exploration de données New Mailing (Nouveau publipostage) de la base de données.  
  
```  
DROP MINING STRUCTURE [New Mailing]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; les instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; les instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
