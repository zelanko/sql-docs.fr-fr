---
title: SELECT (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: def96304f13f57095679056e6eab0a004b5c47d9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62658756"
---
# <a name="select-dmx"></a>SELECT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Le **sélectionnez** instruction dans les Extensions DMX (Data Mining) est utilisée pour les tâches suivantes dans l’exploration de données :  
  
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
  
 Pour aplatir les résultats de requête, utilisez le **sélectionnez** syntaxe avec la **FLATTENED** option, comme illustré dans l’exemple suivant :  
  
```  
SELECT FLATTENED <select list> FROM ...  
```  
  
## <a name="top-n-and-order-by"></a>HAUT \<n > et ORDER BY  
 Vous pouvez trier les résultats d’une requête à l’aide d’une expression et que vous pouvez ensuite revenir un sous-ensemble des résultats en utilisant une combinaison de la **ORDER BY** et **haut** clauses. Ceci s'avère utile dans les scénarios du type publipostage ciblé dans lesquels vous souhaitez uniquement envoyer les résultats aux personnes les plus probables. Vous pouvez classer les résultats d’une cible de requête de prédiction de publipostage par la probabilité de prédiction et puis retourner uniquement la partie supérieure \<n > résultats.  
  
## <a name="select-list"></a>Select list  
 Le  *\<liste de sélection >* peut inclure des références de colonnes scalaires, des fonctions de prédiction et des expressions. Les options disponibles dépendent de l'algorithme et des contextes suivants :  
  
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
 Vous pouvez limiter les cas qui sont retournés par la requête en utilisant un **où** clause. Le **où** clause spécifie que la colonne fait référence dans le **où** expression doit avoir la même sémantique que les références de colonne dans la  *\<liste de sélection >* de la **sélectionnez** instruction et peut uniquement retourner une expression booléenne. La syntaxe pour le **où** clause se présente comme suit  
  
```  
WHERE < condition expression >  
```  
  
 La liste de sélection et **où** clause d’une **sélectionnez** instruction doit respecter les règles suivantes :  
  
-   La liste de sélection doit contenir une expression qui ne retourne pas de résultat booléen. Vous pouvez modifier l'expression, mais celle-ci doit retourner des résultats non booléens.  
  
-   Le **où** clause doit contenir une expression qui retourne un résultat booléen. Vous pouvez modifier la clause, mais celle-ci doit retourner un résultat booléen.  
  
## <a name="predictions"></a>Prévisions  
 Vous pouvez utiliser deux types de syntaxe pour la création des prévisions :  
  
-   [SELECT FROM &#60;modèle&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
-   [SELECT FROM &#60;modèle&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)  
  
 Le premier type de prévision permet de créer des prévisions complexes, en temps réel ou par traitement.  
  
 Le deuxième type de prévision crée une jointure de prévision vide sur une colonne prédictible dans un modèle d'exploration de données, et retourne l'état le plus probable de la colonne. Les résultats de cette requête dépendent intégralement du contenu du modèle d'exploration de données.  
  
 Vous pouvez insérer une instruction select dans la requête source d’une instruction SELECT FROM PREDICTION JOIN à l’aide de la syntaxe suivante.  
  
```  
SELECT FROM PREDICTION JOIN (<SELECT statement>) AS t, WHERE <SELECT statement>  
```  
  
 Pour plus d’informations sur la création de requêtes de prédiction, consultez [Structure et l’utilisation de requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md).  
  
## <a name="clause-syntax"></a>Syntaxe des clauses  
 En raison de la complexité de la navigation avec le **sélectionnez** instruction, les éléments de syntaxe détaillée et les arguments sont décrits par la clause. Pour plus d'informations sur chaque clause, cliquez sur une rubrique dans la liste suivante :  
  
 [SELECT DISTINCT FROM &#60;modèle &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
 [SELECT FROM &#60;modèle&#62;. CONTENU &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)  
  
 [SELECT FROM &#60;modèle&#62;. CAS &#40;DMX&#41;](../dmx/select-from-model-cases-dmx.md)  
  
 [SELECT FROM &#60;modèle&#62;. SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
 [SELECT FROM &#60;modèle&#62;. DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
 [SELECT FROM &#60;modèle&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)  
  
 [SELECT FROM &#60;modèle&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)  
  
 [SELECT FROM &#60;structure&#62;. CAS](../dmx/select-from-structure-cases.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; les instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; les instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40;DMX&#41; les instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)  
  
  
