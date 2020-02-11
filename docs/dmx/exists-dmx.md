---
title: Exists (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0197417dfef604f3cb90b5fa032dae892de272c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68889048"
---
# <a name="exists-dmx"></a>Exists (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne la **valeur true** si la sous-requête spécifiée retourne au moins une ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EXISTS(<subquery>)  
```  
  
## <a name="arguments"></a>Arguments  
 *subquery*  
 Une instruction SELECT de la forme SELECT * FROM \<column Name> [where \<Predicate List>].  
  
## <a name="result-type"></a>Type de résultat  
 Retourne la **valeur true** si le jeu de résultats retourné par la sous-requête contient au moins une ligne ; Sinon, retourne **false**.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser le mot clé NOT avant EXISTS ; par exemple, `WHERE NOT EXISTS (<subquery>)`.  
  
 La liste des colonnes que vous ajoutez à l'argument de sous-requête d'EXISTS est inappropriée ; la fonction vérifie uniquement l'existence d'une ligne qui remplit la condition.  
  
## <a name="examples"></a>Exemples  
 Vous pouvez utiliser EXISTS et NOT EXISTS pour vérifier des conditions dans une table imbriquée. Cela est utile lors de la création d'un filtre qui contrôle les données utilisées pour l'apprentissage ou le test d'un modèle d'exploration de données. Pour plus d’informations, consultez [Filtres pour les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining).  
  
 L’exemple suivant est basé sur la `[Association]` structure et le modèle d’exploration de données que vous avez créés dans le didacticiel sur l' [exploration de données de base](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). La requête retourne uniquement les cas où le client a acheté au moins un produit Patch Kit.  
  
```  
SELECT * FROM [Association].CASES  
WHERE EXISTS  
(  
SELECT * FROM [v Assoc Seq Line Numbers]  
WHERE [[Model] = 'Patch kit'  
)  
```  
  
 Une autre façon d’afficher les mêmes données que celles retournées par cette requête consiste à ouvrir le modèle dans la visionneuse d’associations, à cliquer avec le bouton droit sur le **Kit de correctifs jeu d’éléments = existing**, à sélectionner l’option d' **extraction** , puis à sélectionner **uniquement les cas de modèles**.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;&#41;DMX](../dmx/functions-dmx.md)   
 [Syntaxe de filtre de modèle et exemples &#40;Analysis Services d’exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining)  
  
  
