---
description: Exists (DMX)
title: Exists (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1f45a4a1d0e709c6b8eb9bb7217d268420f31d07
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726230"
---
# <a name="exists-dmx"></a>Exists (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Retourne la **valeur true** si la sous-requête spécifiée retourne au moins une ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EXISTS(<subquery>)  
```  
  
## <a name="arguments"></a>Arguments  
 *subquery*  
 Une instruction SELECT de la forme SELECT * FROM \<column name> [where \<predicate list> ].  
  
## <a name="result-type"></a>Type de résultat  
 Retourne la **valeur true** si le jeu de résultats retourné par la sous-requête contient au moins une ligne ; Sinon, retourne **false**.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser le mot clé NOT avant EXISTS ; par exemple, `WHERE NOT EXISTS (<subquery>)`.  
  
 La liste des colonnes que vous ajoutez à l'argument de sous-requête d'EXISTS est inappropriée ; la fonction vérifie uniquement l'existence d'une ligne qui remplit la condition.  
  
## <a name="examples"></a>Exemples  
 Vous pouvez utiliser EXISTS et NOT EXISTS pour vérifier des conditions dans une table imbriquée. Cela est utile lors de la création d'un filtre qui contrôle les données utilisées pour l'apprentissage ou le test d'un modèle d'exploration de données. Pour plus d’informations, consultez [Filtres pour les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining).  
  
 L’exemple suivant est basé sur la `[Association]` structure et le modèle d’exploration de données que vous avez créés dans le didacticiel sur l' [exploration de données de base](/previous-versions/sql/sql-server-2016/ms167167(v=sql.130)). La requête retourne uniquement les cas où le client a acheté au moins un produit Patch Kit.  
  
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
 [Fonctions &#40;&#41;DMX ](../dmx/functions-dmx.md)   
 [Syntaxe de filtre de modèle et exemples &#40;Analysis Services - Exploration de données&#41;](/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining)  
  
