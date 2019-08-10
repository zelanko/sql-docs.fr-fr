---
title: ALTER MINING STRUCTURE (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5535428d89a0d14b60e3ac79d281f63b4c69bfb5
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68889865"
---
# <a name="alter-mining-structure-dmx"></a>ALTER MINING STRUCTURE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Crée un modèle d'exploration de données sur la base d'une structure d'exploration de données existante.  Lorsque vous utilisez l’instruction **ALTER Mining structure** pour créer un nouveau modèle d’exploration de données, la structure doit déjà exister. En revanche, lorsque vous utilisez l’instruction [Create Mining Model &#40;DMX&#41;](../dmx/create-mining-model-dmx.md), vous créez un modèle et générez automatiquement sa structure d’exploration de données sous-jacente en même temps.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER MINING STRUCTURE <structure>  
ADD MINING MODEL <model>  
(  
    <column definition list>  
  [(<nested column definition list>) [WITH FILTER (<nested filter criteria>)]]  
)  
USING <algorithm> [(<parameter list>)]   
[WITH DRILLTHROUGH]  
[,FILTER(<filter criteria>)]  
```  
  
## <a name="arguments"></a>Arguments  
 *structure*  
 Nom de la structure d'exploration de données à laquelle le modèle d'exploration de données sera ajouté.  
  
 *model*  
 Nom unique du modèle d'exploration de données.  
  
 *liste de définitions de colonnes*  
 Liste des définitions de colonnes séparées par des virgules.  
  
 *liste de définitions de colonnes imbriquées*  
 Liste séparée par des virgules de colonnes d'une table imbriquée (le cas échéant).  
  
 *critères de filtre imbriqués*  
 Expression de filtre appliquée aux colonnes dans une table imbriquée.  
  
 *algorithm*  
 Nom d'un algorithme d'exploration de données, tel que défini par le fournisseur.  
  
> [!NOTE]  
>  Une liste des algorithmes pris en charge par le fournisseur actuel peut être récupérée à l’aide de l' [ensemble de lignes DMSCHEMA_MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset). Pour afficher les algorithmes pris en charge dans l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]actuelle de, consultez [propriétés d’exploration de données](https://docs.microsoft.com/analysis-services/server-properties/data-mining-properties).  
  
 *liste de paramètres*  
 facultatif. Liste séparée par des virgules des paramètres définis par le fournisseur de l'algorithme.  
  
 *critères de filtre*  
 Expression de filtre appliquée aux colonnes dans la table de cas.  
  
## <a name="remarks"></a>Notes  
 Si la structure d'exploration de données contient des clés composites, le modèle d'exploration de données doit comporter toutes les colonnes clés définies dans la structure.  
  
 Si le modèle ne requiert pas de colonne prédictible, par exemple les modèles qui sont générés à l'aide de l'algorithme de gestion de clusters [!INCLUDE[msCoName](../includes/msconame-md.md)] et de l'algorithme MSC ([!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering), il n'est pas nécessaire d'inclure une définition de colonne dans l'instruction. Tous les attributs figurant dans le modèle obtenu seront considérés comme des entrées.  
  
 Dans la clause **with** qui s’applique à la table de cas, vous pouvez spécifier des options pour le filtrage et l’extraction:  
  
-   Ajoutez le mot clé **Filter** et une condition de filtre. Le filtre s'applique aux cas dans le modèle d'exploration de données.  
  
-   Ajoutez le mot clé **Drillthrough** pour permettre aux utilisateurs du modèle d’exploration de données d’accéder aux données de cas à partir des résultats du modèle. Dans les extensions DMX (Data Mining Extensions), l'extraction ne peut être activée que lors de la création du modèle.  
  
 Pour utiliser à la fois le filtrage et l’extraction de cas, vous associez les mots clés dans une clause **with** unique à l’aide de la syntaxe indiquée dans l’exemple suivant:  
  
 `WITH DRILLTHROUGH, FILTER(Gender = 'Male')`  
  
## <a name="column-definition-list"></a>Liste des définitions de colonnes  
 Vous définissez la structure d'un modèle en spécifiant une liste de définitions de colonnes qui comprend les informations suivantes pour chaque colonne :  
  
-   Nom (obligatoire)  
  
-   Alias (facultatif)  
  
-   Indicateurs de modélisation  
  
-   Demande de prédiction, qui indique à l’algorithme si la colonne contient une valeur prévisible, indiquée par la clause **Predict** ou **PREDICT_ONLY**  
  
 Utilisez la syntaxe suivante pour la liste de définitions de colonnes pour définir une seule colonne :  
  
```  
<structure column name>  [AS <model column name>]  [<modeling flags>]    [<prediction>]  
```  
  
### <a name="column-name-and-alias"></a>Nom de colonne et alias  
 Le nom de colonne que vous utilisez dans la liste de définitions de colonnes doit être identique à celui utilisé dans la structure d'exploration de données. Toutefois, vous pouvez éventuellement définir un alias pour représenter la colonne de structure dans le modèle d'exploration de données. Vous pouvez également créer plusieurs définitions de colonne pour la même colonne de structure et attribuer un alias et une utilisation de prédiction différents à chaque copie de la colonne. Par défaut, le nom de la colonne de structure est utilisé si vous ne définissez pas d'alias. Pour plus d’informations, consultez [créer un alias pour une colonne de modèle](https://docs.microsoft.com/analysis-services/data-mining/create-an-alias-for-a-model-column).  
  
 Pour les colonnes de table imbriquée, vous spécifiez le nom de la table imbriquée, vous spécifiez le type de données **table**, puis vous fournissez la liste des colonnes imbriquées à inclure dans le modèle, placées entre parenthèses.  
  
 Vous pouvez définir une expression de filtre appliquée à la table imbriquée en apposant une expression de critères de filtre après la définition de la colonne de table imbriquée.  
  
### <a name="modeling-flags"></a>Indicateurs de modélisation  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend en charge les indicateurs de modélisation suivants pour une utilisation dans les colonnes de modèle d'exploration de données :  
  
> [!NOTE]  
>  L'indicateur de modélisation NOT_NULL s'applique à la colonne de structure d'exploration de données. Pour plus d’informations, consultez [CREATE MINING STRUCTURE &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md).  
  
|||  
|-|-|  
|Terme|Définition|  
|**REGRESSOR**|Indique que l'algorithme peut utiliser la colonne spécifiée dans la formule de régression des algorithmes de régression.|  
|**MODEL_EXISTENCE_ONLY**|Indique que les valeurs de la colonne d'attribut sont moins importantes que la présence de l'attribut.|  
  
 Vous pouvez définir plusieurs indicateurs de modélisation pour une colonne. Pour plus d’informations sur l’utilisation des indicateurs de modélisation, consultez [ &#40;indicateurs&#41;de modélisation DMX](../dmx/modeling-flags-dmx.md).  
  
### <a name="prediction-clause"></a>Clause de prédiction  
 La clause de prédiction décrit de quelle manière la colonne de prédiction est utilisée. Le tableau suivant répertorie les clauses possibles.  
  
|||  
|-|-|  
|**PREDICT**|Cette colonne peut être prédite par le modèle, et ses valeurs peuvent être utilisées comme entrée pour prédire la valeur d'autres colonnes prédictibles.|  
|**PREDICT_ONLY**|Cette colonne peut être prédite par le modèle, mais ses valeurs ne peuvent pas être utilisées dans des cas d'entrée pour prédire la valeur d'autres colonnes prédictibles.|  
  
## <a name="filter-criteria-expressions"></a>Expressions de critères de filtre  
 Vous pouvez définir un filtre qui restreint les cas utilisés dans le modèle d'exploration de données. Le filtre peut être appliqué aux colonnes dans la table de cas ou aux lignes dans la table imbriquée, ou bien aux deux à la fois.  
  
 Les expressions de critères de filtre sont des prédicats DMX simplifiées, semblables à une clause WHERE. Les expressions de filtre se limitent à des formules qui utilisent des opérateurs mathématiques de base, des scalaires et des noms de colonne. L'opérateur EXISTS fait figure d'exception, car il prend la valeur True si au moins une ligne est retournée pour la sous-requête. Les prédicats peuvent être combinés à l’aide des opérateurs logiques communs: AND, OR et NOT.  
  
 Pour plus d’informations sur les filtres utilisés avec les modèles d’exploration de [données &#40;, consultez filtres pour&#41;les modèles d’exploration de données Analysis Services-exploration de données](https://docs.microsoft.com/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining).  
  
> [!NOTE]  
>  Les colonnes dans un filtre doivent être des colonnes de structure d'exploration de données. Vous ne pouvez pas créer de filtre sur une colonne de modèle ou une colonne en tant qu'alias.  
  
 Pour plus d’informations sur les opérateurs DMX et la syntaxe, consultez [colonnes du modèle d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).  
  
## <a name="parameter-definition-list"></a>Liste des définitions des paramètres  
 Vous pouvez ajuster les performances et la fonctionnalité d'un modèle en ajoutant des paramètres d'algorithme à la liste des paramètres. Les paramètres que vous pouvez utiliser dépendent de l'algorithme que vous spécifiez dans la clause USING. Pour obtenir la liste des paramètres associés à chaque algorithme, consultez [algorithmes d’exploration &#40;de données Analysis Services-&#41;exploration de données](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining).  
  
 La syntaxe de la liste des paramètres est la suivante :  
  
```  
[<parameter> = <value>, <parameter> = <value>,...]  
```  
  
## <a name="example-1-add-a-model-to-a-structure"></a>Exemple 1 : Ajouter un modèle à une structure  
 L’exemple suivant ajoute un modèle d’exploration de données Naive Bayes à la nouvelle structure d’exploration de données de **publipostage** et limite le nombre maximal d’États d’attribut à 50.  
  
```  
ALTER MINING STRUCTURE [New Mailing]  
ADD MINING MODEL [Naive Bayes]  
(  
    CustomerKey,   
    Gender,  
    [Number Cars Owned],  
    [Bike Buyer] PREDICT  
)  
USING Microsoft_Naive_Bayes (MAXIMUM_STATES = 50)  
```  
  
## <a name="example-2-add-a-filtered-model-to-a-structure"></a>Exemple 2 : Ajouter un modèle filtré à une structure  
 L’exemple suivant ajoute un modèle d’exploration `Naive Bayes Women`de données,, à la nouvelle structure d’exploration de données de **publipostage** . Le nouveau modèle a la même structure de base que le modèle d'exploration de données ajouté dans l'exemple 1, à la différence près que ce modèle restreint les cas de la structure d'exploration de données aux clients qui sont des femmes de plus de 50 ans.  
  
```  
ALTER MINING STRUCTURE [New Mailing]  
ADD MINING MODEL [Naive Bayes Women]  
(  
    CustomerKey,   
    Gender,  
    [Number Cars Owned],  
    [Bike Buyer] PREDICT  
)  
USING Microsoft_Naive_Bayes  
WITH FILTER([Gender] = 'F' AND [Age] >50)  
```  
  
## <a name="example-3-add-a-filtered-model-to-a-structure-with-a-nested-table"></a>Exemple 3: Ajouter un modèle filtré à une structure avec une table imbriquée  
 L'exemple suivant ajoute un modèle d'exploration de données à une version modifiée de la structure d'exploration de données du panier d'achat. La structure d’exploration de données utilisée dans l’exemple a été modifiée pour ajouter une colonne **Region** , qui contient les attributs de la région Customer et une colonne **Group revenu** , qui classe les revenus des clients en utilisant les valeurs **High**, **modéré** ou **faible**.  
  
 La structure d'exploration de données inclut également une table imbriquée qui répertorie les articles que le client a achetés.  
  
 Étant donné que la structure d'exploration de données contient une table imbriquée, vous pouvez définir un filtre sur la table de cas, la table imbriquée ou les deux. Cet exemple combine un filtre de cas et un filtre de lignes imbriqué pour restreindre les cas aux clients européens fortunés qui ont acheté l'un des modèles de pneu route.  
  
```  
ALTER MINING STRUCTURE [Market Basket with Region and Income]  
ADD MINING MODEL [Decision Trees]  
(  
    CustomerKey,   
    Region,  
    [Income Group],  
    [Product] PREDICT (Model)   
WITH FILTER (EXISTS (SELECT * FROM [v Assoc Seq Line Items] WHERE   
 [Model] = 'HL Road Tire' OR  
 [Model] = 'LL Road Tire' OR  
 [Model] = 'ML Road Tire' )  
)  
) WITH FILTER ([Income Group] = 'High' AND [Region] = 'Europe')  
USING Microsoft_Decision Trees  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition &#40;de&#41; données DMX dans Data Mining Extensions](../dmx/dmx-statements-data-definition.md)   
 [Instructions de manipulation &#40;de&#41; données DMX des extensions d’exploration de données](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
