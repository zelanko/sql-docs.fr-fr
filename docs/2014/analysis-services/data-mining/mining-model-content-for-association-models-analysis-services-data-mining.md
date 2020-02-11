---
title: Contenu du modèle d’exploration de données pour les modèles d’Association (Analysis Services-exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- mining model content, association models
- rules [Data Mining]
- associations [Analysis Services]
ms.assetid: d5849bcb-4b8f-4f71-9761-7dc5bb465224
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9a1e525d7b42d058343e41ea154f0687fb969839
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66083689"
---
# <a name="mining-model-content-for-association-models-analysis-services---data-mining"></a>Contenu du modèle d'exploration de données pour les modèles d'association (Analysis Services - Exploration de données)
  Cette rubrique décrit le contenu du modèle d’exploration qui est spécifique aux modèles utilisant l’algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules). Pour une explication de la terminologie générale et statistique en rapport avec le contenu du modèle d’exploration de données pour tous les types de modèles, consultez [Contenu du modèle d’exploration &#40;Analysis Services - Exploration de données&#41;](mining-model-content-analysis-services-data-mining.md).  
  
## <a name="understanding-the-structure-of-an-association-model"></a>Fonctionnement de la structure d'un modèle d'association  
 La structure d'un modèle d'association est simple. Chaque modèle possède un nœud parent unique qui représente le modèle et ses métadonnées, et chaque nœud parent possède une liste plate de jeux d'éléments et de règles. Les jeux d'éléments et les règles ne sont pas organisés dans des arbres. Comme le montre le diagramme suivant, les jeux d'éléments précèdent les règles.  
  
 ![structure de contenu de modèle pour des modèles d'association](../media/modelcontentstructure-assoc.gif "structure de contenu de modèle pour des modèles d'association")  
  
 Chaque jeu d'éléments est contenu dans son propre nœud (NODE_TYPE = 7). Le *nœud* : inclut la définition du jeu d’éléments, le nombre de cas contenant ce jeu d’éléments, ainsi que d’autres informations.  
  
 Chaque règle est également contenue dans son propre nœud (NODE_TYPE = 8). Une *règle* : décrit une séquence générale indiquant comment les éléments sont associés. Une règle s'apparente à une instruction IF-THEN. La partie gauche de la règle indique une condition existante ou un jeu de conditions. Quant à la partie droite de la règle, elle indique l'élément de votre jeu de données qui est généralement associé aux conditions de la partie gauche.  
  
 **Remarque** Si vous souhaitez extraire les règles ou les jeux d’éléments, vous pouvez utiliser une requête pour retourner uniquement les types de nœuds de votre choix. Pour plus d’informations, consultez [Exemples de requête de modèle d’association](association-model-query-examples.md).  
  
## <a name="model-content-for-an-association-model"></a>Contenu du modèle pour un modèle d'association  
 Cette section fournit des informations et des exemples pour les colonnes du contenu du modèle d'exploration de données qui s'appliquent aux modèles d'association.  
  
 Pour plus d’informations sur les colonnes à caractère général dans l’ensemble de lignes du schéma, comme MODEL_CATALOG et MODEL_NAME, consultez [Contenu du modèle d’exploration &#40;Analysis Services – Exploration de données&#41;](mining-model-content-analysis-services-data-mining.md).  
  
 MODEL_CATALOG  
 Nom de la base de données où le modèle est stocké.  
  
 MODEL_NAME  
 Nom du modèle.  
  
 ATTRIBUTE_NAME  
 Noms des attributs qui correspondent à ce nœud.  
  
 NODE_NAME  
 Nom du nœud. Pour un modèle d'association, cette colonne contient la même valeur que NODE_UNIQUE_NAME.  
  
 NODE_UNIQUE_NAME  
 Nom unique du nœud.  
  
 NODE_TYPE  
 Un modèle d'association génère uniquement en sortie les types de nœuds suivants :  
  
|ID du type de nœud|Type|  
|------------------|----------|  
|1 (Modèle)|Nœud racine ou parent.|  
|7 (Jeu d'éléments)|Jeu d'éléments ou collection de paires attribut/valeur. Exemples :<br /><br /> `Product 1 = Existing, Product 2 = Existing`<br /><br /> or<br /><br /> `Gender = Male`.|  
|8 (Règle)|Règle définissant la façon dont les éléments sont liés les uns aux autres.<br /><br /> Exemple :<br /><br /> `Product 1 = Existing, Product 2 = Existing -> Product 3 = Existing`.|  
  
 NODE_CAPTION  
 Étiquette ou légende associée au nœud.  
  
 **Nœud jeu d’éléments** Liste d’éléments séparés par des virgules.  
  
 **Nœud de règle** Contient les côtés gauche et droit de la règle.  
  
 CHILDREN_CARDINALITY  
 Indique le nombre d'enfants du nœud actuel.  
  
 **Nœud parent** Indique le nombre total de jeux d’éléments et de règles.  
  
> [!NOTE]  
>  Pour obtenir la répartition du nombre de jeux d'éléments et de règles, consultez NODE_DESCRIPTION pour le nœud racine du modèle.  
  
 **Nœud jeu d’éléments ou Rule** Toujours 0.  
  
 PARENT_UNIQUE_NAME  
 Nom unique du parent du nœud.  
  
 **Nœud parent** Toujours NULL.  
  
 **Nœud jeu d’éléments ou Rule** Toujours 0.  
  
 NODE_DESCRIPTION  
 Description conviviale du contenu du nœud.  
  
 **Nœud parent** Comprend une liste séparée par des virgules des informations suivantes sur le modèle :  
  
|Élément|Description|  
|----------|-----------------|  
|ITEMSET_COUNT|Nombre de jeux d'éléments dans le modèle.|  
|RULE_COUNT|Nombre de règles dans le modèle.|  
|MIN_SUPPORT|Prise en charge minimale trouvée pour un jeu d'éléments unique.<br /><br /> **Remarque** Cette valeur peut être différente de la valeur que vous définissez pour le paramètre *_SUPPORT minimal* .|  
|MAX_SUPPORT|Prise en charge maximale trouvée pour un jeu d'éléments unique.<br /><br /> **Remarque** Cette valeur peut être différente de la valeur que vous définissez pour le paramètre *MAXIMUM_SUPPORT* .|  
|MIN_ITEMSET_SIZE|Taille du plus petit jeu d'éléments, représentée par un nombre d'éléments.<br /><br /> La valeur 0 indique que l'état `Missing` a été traité en tant qu'élément indépendant.<br /><br /> **Remarque** La valeur par défaut du paramètre *MINIMUM_ITEMSET_SIZE* est 1.|  
|MAX_ITEMSET_SIZE|Indique la taille du plus grand jeu d'éléments trouvé.<br /><br /> **Remarque** Cette valeur est concédée par la valeur que vous définissez pour le paramètre *MAX_ITEMSET_SIZE* lorsque vous avez créé le modèle. Cette valeur ne peut jamais dépasser cette valeur ; toutefois, elle peut être inférieure à celle-ci. La valeur par défaut est 3.|  
|MIN_PROBABILITY|Probabilité minimale détectée pour un jeu d'éléments ou une règle unique dans le modèle.<br /><br /> Exemple : 0.400390625<br /><br /> **Remarque** Pour jeux d’éléments, cette valeur est toujours supérieure à la valeur que vous définissez pour le paramètre *MINIMUM_PROBABILITY* lorsque vous avez créé le modèle.|  
|MAX_PROBABILITY|Probabilité maximale détectée pour un jeu d'éléments ou une règle unique dans le modèle.<br /><br /> Exemple : 1<br /><br /> **Remarque** Il n’existe aucun paramètre pour limiter la probabilité maximale de jeux d’éléments. Si vous voulez éliminer des éléments qui sont trop fréquents, utilisez à la place le paramètre *MAXIMUM_SUPPORT* .|  
|MIN_LIFT|Quantité minimale de finesse fournie par le modèle pour un jeu d'éléments.<br /><br /> Exemple : 0,14309369632511<br /><br /> Remarque : le fait de connaître la finesse minimale peut vous aider à déterminer si la finesse est significative pour un jeu d’éléments.|  
|MAX_LIFT|Quantité maximale de finesse fournie par le modèle pour un jeu d'éléments.<br /><br /> Exemple: 1,95758227647523 **Remarque** : Le fait de connaître la finesse maximale peut vous aider à déterminer si la finesse est significative pour un jeu d’éléments.|  
  
 **Nœud jeu d’éléments** Les nœuds jeu d’éléments contiennent une liste des éléments, affichés sous la forme d’une chaîne de texte séparée par des virgules.  
  
 Exemple :  
  
 `Touring Tire = Existing, Water Bottle = Existing`  
  
 Cela signifie que les pneus pour vélo de tourisme et les bidons d'eau ont été achetés ensemble.  
  
 **Nœud de règle** Les nœuds de règle contiennent une partie gauche et une partie droite de la règle, séparées par une flèche.  
  
 Exemple : `Touring Tire = Existing, Water Bottle = Existing -> Cycling cap = Existing`  
  
 Cela signifie que si quelqu'un a acheté un pneu pour vélo de tourisme et un bidon d'eau, il était aussi susceptible d'acheter une casquette de cyclisme.  
  
 NODE_RULE  
 Fragment XML qui décrit la règle ou le jeu d'éléments incorporé dans le nœud.  
  
 **Nœud parent** Occult.  
  
 **Nœud jeu d’éléments** Occult.  
  
 **Nœud de règle** Le fragment XML contient des informations supplémentaires utiles sur la règle, telles que la prise en charge, la confiance et le nombre d’éléments, ainsi que l’ID du nœud qui représente la partie gauche de la règle.  
  
 MARGINAL_RULE  
 : vide.  
  
 NODE_PROBABILITY  
 Une probabilité ou un score de confiance associé au jeu d'éléments ou à la règle.  
  
 **Nœud parent** Toujours 0.  
  
 **Nœud jeu d’éléments** Probabilité du jeu d’éléments.  
  
 **Nœud de règle** Valeur de confiance pour la règle.  
  
 MARGINAL_PROBABILITY  
 Identique à NODE_PROBABILITY.  
  
 NODE_DISTRIBUTION  
 La table contient des informations très différentes, selon que le nœud est un jeu d'éléments ou une règle.  
  
 **Nœud parent** Occult.  
  
 **Nœud jeu d’éléments** Répertorie chaque élément dans le jeu d’éléments avec une valeur de probabilité et de prise en charge. Par exemple, si le jeu d'éléments contient deux produits, le nom de chaque produit est répertorié avec le nombre des cas qui incluent chaque produit.  
  
 **Nœud de règle** Contient deux lignes. La première ligne montre l'attribut de la partie droite de la règle, c'est-à-dire l'élément prédit, avec un score de confiance.  
  
 La deuxième ligne est unique aux modèles d'association ; elle contient un pointeur vers le jeu d'éléments dans la partie droite de la règle. Le pointeur est représenté dans la colonne ATTRIBUTE_VALUE comme l'ID du jeu d'éléments qui contient uniquement l'élément de la partie droite.  
  
 Par exemple, si la règle est `If {A,B} Then {C}`, la table contient le nom de l'élément `{C}`et l'ID du nœud qui contient le jeu d'éléments pour l'élément C.  
  
 Ce pointeur est utile car vous pouvez déterminer à partir du nœud de jeu d'éléments combien de cas en tout incluent le produit de la partie droite. Les cas soumis à la règle `If {A,B} Then {C}` sont un sous-ensemble des cas répertoriés dans le jeu d'éléments de `{C}`.  
  
 NODE_SUPPORT  
 Nombre de cas qui prennent en charge ce nœud.  
  
 **Nœud parent** Nombre de cas dans le modèle.  
  
 **Nœud jeu d’éléments** Nombre de cas qui contient tous les éléments dans le jeu d’éléments.  
  
 **Nœud de règle** Nombre de cas contenant tous les éléments inclus dans la règle.  
  
 MSOLAP_MODEL_COLUMN  
 Contient des informations différentes selon que le nœud est un jeu d'éléments ou une règle.  
  
 **Nœud parent** Occult.  
  
 **Nœud jeu d’éléments** Occult.  
  
 **Nœud de règle** ID du jeu d’éléments qui contient les éléments de la partie gauche de la règle. Par exemple, si la règle est `If {A,B} Then {C}`, cette colonne contient l’ID du jeu d’éléments contenant seulement `{A,B}`.  
  
 MSOLAP_NODE_SCORE  
 **Nœud parent** Occult.  
  
 **Nœud jeu d’éléments** Score d’importance pour le jeu d’éléments.  
  
 **Nœud de règle** Score d’importance pour la règle.  
  
> [!NOTE]  
>  L'importance est calculée différemment pour les jeux d'éléments et les règles. Pour plus d’informations, consultez [Références techniques relatives à l’algorithme Microsoft Association](microsoft-association-algorithm-technical-reference.md).  
  
 MSOLAP_NODE_SHORT_CAPTION  
 : vide.  
  
## <a name="see-also"></a>Voir aussi  
 [Contenu du modèle d’exploration de données &#40;Analysis Services d’exploration de données&#41;](mining-model-content-analysis-services-data-mining.md)   
 [Algorithme d’association Microsoft](microsoft-association-algorithm.md)   
 [Exemples de requêtes de modèle d'association](association-model-query-examples.md)  
  
  
