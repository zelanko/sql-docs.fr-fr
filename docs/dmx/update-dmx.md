---
title: MISE À JOUR (DMX) | Documents Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4049c6052a4aabcfe7207086db1db19961354eb0
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842192"
---
# <a name="update-dmx"></a>UPDATE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Modifications du **NODE_CAPTION** colonne dans le modèle d’exploration de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
UPDATE <model>.CONTENT  
SET NODE_CAPTION='new caption'  
[WHERE <condition expression>]  
```  
  
## <a name="arguments"></a>Arguments  
 *model*  
 Identificateur du modèle  
  
 *nouvelle légende*  
 Chaîne qui contient le nouveau nom pour le **NODE_CAPTION** colonne.  
  
 *Expression de condition*  
 Facultatif. Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
## <a name="examples"></a>Exemples  
 Dans l’exemple suivant, la **mise à jour** instruction modifie le nom par défaut, `Cluster 1`, pour le cluster `001` à un nom plus descriptif, `Likely Customers`.  
  
```  
UPDATE [TM Clustering].CONTENT  
SET NODE_CAPTION= 'Likely Customers'  
WHERE NODE_UNIQUE_NAME = '001'  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
