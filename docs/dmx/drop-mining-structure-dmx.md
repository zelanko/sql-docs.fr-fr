---
title: DROP MINING STRUCTURE (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d5c94ec01ff5f11d2b7f663f09de0a7c1527f343
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68074081"
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
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
