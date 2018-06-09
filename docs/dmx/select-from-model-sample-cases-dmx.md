---
title: SELECT FROM &lt;modèle&gt;. SAMPLE_CASES (DMX) | Documents Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f4443f05fbee790f5f1d266f451e1105b9c00197
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841522"
---
# <a name="select-from-ltmodelgtsamplecases-dmx"></a>SELECT FROM &lt;modèle&gt;. SAMPLE_CASES (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne les exemples de cas qui sont représentatifs des cas utilisés pour l'apprentissage du modèle d'exploration de données.  
  
 Pour utiliser cette instruction, vous devez activer l'extraction lorsque vous créez le modèle d'exploration de données. Pour plus d’informations sur l’activation de l’extraction, consultez [CREATE MINING MODEL &#40;DMX&#41;](../dmx/create-mining-model-dmx.md), [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md), et [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.SAMPLE_CASES  
[WHERE <condition list>] ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 Facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste séparée par des virgules des identificateurs des colonnes associées.  
  
 *model*  
 Identificateur du modèle  
  
 *liste des conditions*  
 Facultatif. Conditions pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Les exemples de cas peuvent être générés et ne pas réellement exister dans les données d'apprentissage. Le cas retourné est représentatif du nœud de contenu spécifié.  
  
 Bien que le [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme Sequence Clustering est le seul [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme prenant en charge à l’aide de SELECT FROM \<modèle >. SAMPLE_CASES, les algorithmes tiers peuvent également en charge.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les exemples de cas utilisés pour l'apprentissage du modèle d'exploration de données Target Mail (Courrier cible). À l’aide de la [IsInNode &#40;DMX&#41; ](../dmx/isinnode-dmx.md) de fonction dans le **où** clause retourne uniquement les cas qui sont associées au nœud « 000000003 ». La chaîne de nœud peut être trouvée dans la colonne NODE_UNIQUE_NAME de l'ensemble de lignes du schéma.  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNEZ &AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [Data Mining Extensions &#40;DMX&#41; instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
