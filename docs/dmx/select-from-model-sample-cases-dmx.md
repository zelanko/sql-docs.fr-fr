---
description: Sélectionnez à partir du &lt; modèle &gt; . SAMPLE_CASES (DMX)
title: Sélectionnez à partir du &lt; modèle &gt; . SAMPLE_CASES (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: af927d9c998d245c31511c29450eafac31e1d54b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500870"
---
# <a name="select-from-ltmodelgtsample_cases-dmx"></a>Sélectionnez à partir du &lt; modèle &gt; . SAMPLE_CASES (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Retourne les exemples de cas qui sont représentatifs des cas utilisés pour l'apprentissage du modèle d'exploration de données.  
  
 Pour utiliser cette instruction, vous devez activer l'extraction lorsque vous créez le modèle d'exploration de données. Pour plus d’informations sur l’activation de l’extraction, consultez [créer un modèle d’exploration de données &#40;dmx&#41;](../dmx/create-mining-model-dmx.md), [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md)et [ALTER Mining structure &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.SAMPLE_CASES  
[WHERE <condition list>] ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste séparée par des virgules des identificateurs des colonnes associées.  
  
 *model*  
 Identificateur du modèle  
  
 *liste de conditions*  
 facultatif. Conditions pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Les exemples de cas peuvent être générés et ne pas réellement exister dans les données d'apprentissage. Le cas retourné est représentatif du nœud de contenu spécifié.  
  
 Bien que l' [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme Sequence Clustering soit le seul [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme qui prend en charge l’utilisation de SELECT FROM \<model> . SAMPLE_CASES, les algorithmes tiers peuvent également le prendre en charge.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les exemples de cas utilisés pour l'apprentissage du modèle d'exploration de données Target Mail (Courrier cible). L’utilisation de la fonction [IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md) dans la clause **Where** renvoie uniquement les cas associés au nœud « 000000003 ». La chaîne de nœud peut être trouvée dans la colonne NODE_UNIQUE_NAME de l'ensemble de lignes du schéma.  
  
```  
Select * from [Sequence Clustering].SAMPLE_Cases  
WHERE IsInNode('000000003')  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNER &#40;&#41;DMX ](../dmx/select-dmx.md)   
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
