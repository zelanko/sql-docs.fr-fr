---
title: SÉLECTIONNER (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8bf766c6f0a7fd757b280b0f950a43cfdc025929
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928425"
---
# <a name="select-dmx"></a>SELECT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  L’instruction **Select** dans les extensions DMX (Data Mining Extensions) est utilisée pour les tâches suivantes dans l’exploration de données :  
  
-   Exploration du contenu d'un modèle d'exploration de données existant  
  
-   Création de prévisions à partir d'un modèle d'exploration de données existant  
  
-   Création d'une copie d'un modèle d'exploration de données existant  
  
-   Navigation dans la structure d'exploration de données  
  
 Bien que la syntaxe complète de cette instruction soit complexe, les principales clauses utilisées pour naviguer dans un modèle et sa structure sous-jacente peuvent être résumées comme suit :  
  
```  
SELECT [FLATTENED] [TOP <n>] <select list>  
FROM <model/structure>[.aspect]  
[WHERE <condition expression>]  
[ORDER BY <expression>[DESC|ASC]]  
```  
  
## <a name="flattened"></a>FLATTENED  
 Certains clients d'exploration de données n'acceptent pas les jeux de résultats en format hiérarchique provenant d'un fournisseur d'exploration de données. Ces clients n'ont peut-être pas la possibilité de gérer les hiérarchies ou ils doivent stocker les résultats dans une table dénormalisée unique. Pour convertir les données provenant de tables imbriquées en tables à plat, vous devez exiger que les résultats de requête soient aplatis.  
  
 Pour aplatir les résultats de la requête, utilisez la syntaxe **Select** avec l’option **aplatie** , comme illustré dans l’exemple suivant :  
  
```  
SELECT FLATTENED <select list> FROM ...  
```  
  
## <a name="top-n-and-order-by"></a>N \<premiers> et trier par  
 Vous pouvez classer les résultats d’une requête à l’aide d’une expression, puis retourner un sous-ensemble des résultats à l’aide d’une combinaison des clauses **order by** et **Top** . Ceci s'avère utile dans les scénarios du type publipostage ciblé dans lesquels vous souhaitez uniquement envoyer les résultats aux personnes les plus probables. Vous pouvez classer les résultats d’une requête de prédiction de publipostage cible par la probabilité de prédiction, puis retourner uniquement \<les n premiers résultats>.  
  
## <a name="select-list"></a>Select list  
 La * \<liste de sélection>* peut inclure des références de colonnes scalaires, des fonctions de prédiction et des expressions. Les options disponibles dépendent de l'algorithme et des contextes suivants :  
  
-   si vous interrogez une structure ou un modèle d'exploration de données ;  
  
-   si vous interrogez du contenu ou des cas ;  
  
-   si les données sources correspondent à une table relationnelle ou un cube ;  
  
-   si vous effectuez des prédictions.  
  
 Dans de nombreux cas, vous pouvez utiliser des alias ou créer des expressions simples basées sur les éléments de la liste de sélection. Par exemple, l'exemple suivant illustre une expression simple sur les colonnes du modèle :  
  
```  
SELECT [CustomerID], [Last Name] + ', ' + [FirstName] AS FullName  
FROM <model>.CASES  
```  
  
 L'exemple suivant crée un alias pour une colonne qui contient les résultats d'une fonction de prédiction :  
  
```  
SELECT Predict([Column1], 'Value') as Column1Prediction  
FROM MyModel  
JOIN <source data query>  
```  
  
## <a name="where"></a>WHERE  
 Vous pouvez limiter les cas retournés par la requête à l’aide d’une clause **Where** . La clause **Where** spécifie que les références de colonne dans l’expression **Where** doivent avoir la même sémantique que les références de colonne dans la * \<liste de sélection>* de l’instruction **Select** , et ne peuvent retourner qu’une expression booléenne. La syntaxe de la clause **Where** est la suivante :  
  
```  
WHERE < condition expression >  
```  
  
 La liste de sélection et la clause **Where** d’une instruction **Select** doivent respecter les règles suivantes :  
  
-   La liste de sélection doit contenir une expression qui ne retourne pas de résultat booléen. Vous pouvez modifier l'expression, mais celle-ci doit retourner des résultats non booléens.  
  
-   La clause **Where** doit contenir une expression qui retourne un résultat booléen. Vous pouvez modifier la clause, mais celle-ci doit retourner un résultat booléen.  
  
## <a name="predictions"></a>Prévisions  
 Vous pouvez utiliser deux types de syntaxe pour la création des prévisions :  
  
-   [Sélectionnez un modèle de &#60;&#62; &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
-   [Sélectionnez un modèle de &#60;&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)  
  
 Le premier type de prévision permet de créer des prévisions complexes, en temps réel ou par traitement.  
  
 Le deuxième type de prévision crée une jointure de prévision vide sur une colonne prédictible dans un modèle d'exploration de données, et retourne l'état le plus probable de la colonne. Les résultats de cette requête dépendent intégralement du contenu du modèle d'exploration de données.  
  
 Vous pouvez insérer une instruction SELECT dans la requête source d’une instruction SELECT FROM PREDICTION JOIN à l’aide de la syntaxe suivante.  
  
```  
SELECT FROM PREDICTION JOIN (<SELECT statement>) AS t, WHERE <SELECT statement>  
```  
  
 Pour plus d’informations sur la création de requêtes de prédiction, consultez [structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md).  
  
## <a name="clause-syntax"></a>Syntaxe des clauses  
 En raison de la complexité de l’exploration avec l’instruction **Select** , les éléments et les arguments syntaxiques détaillés sont décrits par clause. Pour plus d'informations sur chaque clause, cliquez sur une rubrique dans la liste suivante :  
  
 [SELECT DISTINCT FROM &#60;modèle &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
 [Sélectionnez &#60;&#62; de modèle. &#40;DE CONTENU DMX&#41;](../dmx/select-from-model-content-dmx.md)  
  
 [Sélectionnez &#60;&#62; de modèle. CAS &#40;&#41;DMX](../dmx/select-from-model-cases-dmx.md)  
  
 [Sélectionnez &#60;&#62; de modèle.&#41;SAMPLE_CASES &#40;DMX](../dmx/select-from-model-sample-cases-dmx.md)  
  
 [Sélectionnez &#60;&#62; de modèle.&#41;DIMENSION_CONTENT &#40;DMX](../dmx/select-from-model-dimension-content-dmx.md)  
  
 [Sélectionnez un modèle de &#60;&#62; &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
 [Sélectionnez un modèle de &#60;&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)  
  
 [Sélectionnez &#60;&#62; de structure. PARFOIS](../dmx/select-from-structure-cases.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)  
  
  
