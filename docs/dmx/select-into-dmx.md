---
title: SELECT INTO (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: bf2e0f2d57ce8bf1834813d4e39d06afc9724fd7
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83670088"
---
# <a name="select-into-dmx"></a>SELECT INTO (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Crée un modèle d'exploration de données, sur la base de la structure d'exploration de données d'un modèle existant. L’instruction **SELECT INTO** crée le nouveau modèle d’exploration de données en copiant le schéma et d’autres informations qui ne sont pas spécifiques à l’algorithme réel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT INTO <new model>   
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH[,] [FILTER(<expression>)]]  
FROM <existing model>  
```  
  
## <a name="arguments"></a>Arguments  
 *new model*  
 Nom unique du nouveau modèle en cours de création.  
  
 *utilisé*  
 Nom défini par le fournisseur d'un algorithme d'exploration de données  
  
 *liste de paramètres*  
 facultatif. Liste séparée par des virgules des paramètres définis par le fournisseur de l'algorithme.  
  
 *expression*  
 Expression dont le résultat est une condition de filtre valide sur les données d'apprentissage. Pour plus d’informations sur les expressions qui peuvent être utilisées comme filtres, consultez [filtres pour les modèles d’exploration de données &#40;Analysis Services d’exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining).  
  
 *modèle existant*  
 Nom du modèle existant à copier.  
  
## <a name="remarks"></a>Notes  
 Si l'apprentissage du modèle existant est effectué, le nouveau modèle est automatiquement traité lors de l'exécution de cette instruction. Dans le cas contraire, le nouveau modèle reste non traité.  
  
 L’instruction **SELECT INTO** fonctionne uniquement si la structure du modèle existant est compatible avec l’algorithme du nouveau modèle. Par conséquent, cette instruction s'avère très utile pour créer et tester rapidement des modèles basés sur le même algorithme. Si vous modifiez le type d'algorithme, le nouvel algorithme doit prendre en charge le type de données de chaque colonne du modèle existant, sinon une erreur peut se produire lors du traitement du modèle.  
  
 La clause **with Drillthrough** active l’extraction sur le nouveau modèle d’exploration de données. L'extraction ne peut être activée que lors de la création du modèle.  
  
## <a name="example-1-altering-the-parameters-of-the-model"></a>Exemple 1 : modification des paramètres du modèle  
 L’exemple suivant crée un modèle d’exploration de données basé sur un modèle d’exploration de données existant, que `TM_Clustering` vous créez dans le didacticiel sur l' [exploration de données de base](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Le paramètre CLUSTER_COUNT est modifié de telle sorte que cinq clusters au maximum existent dans ce nouveau modèle. En revanche, le modèle existant utilise la valeur par défaut 10.  
  
```  
SELECT * INTO [New_Clustering]  
USING [Microsoft_Clustering] (CLUSTER_COUNT = 5)   
FROM [TM Clustering]  
```  
  
## <a name="example-2-adding-a-filter-to-the-model"></a>Exemple 2 : ajout d'un filtre au modèle  
 L'exemple suivant crée un modèle d'exploration de données basé sur un modèle existant et ajoute un filtre. Le filtre restreint les données d'apprentissage uniquement aux clients qui habitent dans une région donnée.  
  
```  
SELECT * INTO [Clustering Europe Region]  
USING [Microsoft_Clustering] WITH FILTER(Region='Europe')  
FROM [TM Clustering]  
```  
  
> [!NOTE]  
>  Les filtres appliqués à la table de cas peuvent être modifiés à l'aide de l'instruction SELECT INTO, tel qu'indiqué dans cet exemple ; toutefois, si le modèle d'origine contient un filtre sur une table imbriquée, ce filtre ne peut pas être modifié ou supprimé en utilisant cette syntaxe, mais il est copié tel quel à partir du modèle d'origine. Pour créer un modèle avec un autre filtre sur une table imbriquée, utilisez la syntaxe ALTER STRUCTURE...ADD MODEL.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
