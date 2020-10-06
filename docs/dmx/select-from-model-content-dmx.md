---
description: Sélectionnez à partir du &lt; modèle &gt; . CONTENU (DMX)
title: Sélectionnez à partir du &lt; modèle &gt; . CONTENU (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: df70a8726e9abc56d677c48ba8f3f995814866d4
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727640"
---
# <a name="select-from-ltmodelgtcontent-dmx"></a>Sélectionnez à partir du &lt; modèle &gt; . CONTENU (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Retourne l'ensemble de lignes du schéma de modèle d'exploration de données pour le modèle d'exploration de données spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 Facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste de colonnes séparées par des virgules, dérivées de l'ensemble de lignes du schéma Content.  
  
 *model*  
 Identificateur du modèle  
  
 *expression de condition*  
 Facultatif. Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Facultatif. Expression retournant une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 **Select from** _\<model>_ **. **L’instruction content retourne le contenu qui est spécifique à chaque algorithme. Imaginons par exemple que vous souhaitez utiliser les descriptions de toutes les règles d'un modèle de règles d'association dans une application personnalisée. Vous pouvez utiliser une **sélection à partir de \<model> . Instruction CONTENT** pour retourner des valeurs dans la colonne NODE_RULE du modèle.  
  
 Le tableau suivant répertorie les colonnes incluses dans le contenu du modèle d'exploration de données.  
  
> [!NOTE]  
>  Les algorithmes peuvent interpréter les colonnes différemment afin de représenter le contenu de manière appropriée. Pour obtenir une description du contenu du modèle d’exploration de données pour chaque algorithme et des conseils sur l’interprétation et l’interrogation du contenu du modèle d’exploration de données pour chaque type de modèle, consultez [Mining Model content &#40;Analysis Services-data mining&#41;](/analysis-services/data-mining/mining-model-content-analysis-services-data-mining).  
  
|Colonne de l'ensemble de lignes CONTENT|Description|  
|---------------------------|-----------------|  
|MODEL_CATALOG|Nom de catalogue. Valeur NULL si le fournisseur ne prend pas en charge les catalogues.|  
|MODEL_SCHEMA|Nom de schéma non qualifié. Valeur NULL si le fournisseur ne prend pas en charge les schémas.|  
|MODEL_NAME|Nom de modèle. Cette colonne ne peut pas contenir de valeur NULL.|  
|ATTRIBUTE_NAME|Nom de l'attribut qui correspond au nœud.|  
|NODE_NAME|Nom du nœud.|  
|NODE_UNIQUE_NAME|Nom unique du nœud dans le modèle.|  
|NODE_TYPE|Entier qui représente le type du nœud. .|  
|NODE_GUID|GUID du nœud. Valeur NULL en l'absence de GUID.|  
|NODE_CAPTION|Étiquette ou légende associée au nœud. Principalement utilisée à des fins d'affichage. En l'absence de légende, NODE_NAME est retourné.|  
|CHILDREN_CARDINALITY|Nombre d'enfants de ce nœud.|  
|PARENT_UNIQUE_NAME|Nom unique du parent du nœud.|  
|NODE_DESCRIPTION|Description du nœud.|  
|NODE_RULE|Fragment XML qui représente la règle incorporée dans le nœud. Le format de la chaîne XML est basé sur la norme PMML.|  
|MARGINAL_RULE|Fragment XML qui décrit le chemin d'accès du parent vers le nœud.|  
|NODE_PROBABILITY|Probabilité du chemin d'accès qui se termine dans le nœud.|  
|MARGINAL_PROBABILITY|Probabilité d'accès au nœud à partir du nœud parent.|  
|NODE_DISTRIBUTION|Table qui contient des statistiques décrivant la distribution des valeurs dans le nœud.|  
|NODE_SUPPORT|Nombre de cas de support de ce nœud.|  
  
## <a name="examples"></a>Exemples  
 Le code suivant retourne l'ID du nœud parent pour le modèle d'arbre de décision qui a été ajouté à la structure d'exploration de données de publipostage ciblé.  
  
```  
SELECT MODEL_NAME, NODE_NAME FROM [TM Decision Tree].CONTENT  
WHERE NODE_TYPE = 1  
```  
  
 Résultats attendus :  
  
|MODEL_NAME|NODE_NAME|  
|-----------------|----------------|  
|TM_DecisionTree|0|  
  
 La requête suivante utilise la fonction **IsDescendant** pour retourner les enfants immédiats du nœud qui a été retourné dans la requête précédente.  
  
> [!NOTE]  
>  Étant donné que la valeur de l’NODE_NAME est une chaîne, vous ne pouvez pas utiliser une instruction Sub-SELECT pour retourner le NODE_ID en tant qu’argument à la fonction **IsDescendant** .  
  
```  
SELECT NODE_NAME, NODETYPE, NODE_CAPTION   
FROM [TM Decision Tree].CONTENT  
WHERE ISDESCENDANT('0')  
```  
  
 Résultats attendus :  
  
 S'agissant d'un modèle d'arbre de décision, les descendants du nœud parent du modèle incluent un nœud de statistiques marginales unique, un nœud qui représente l'attribut prédictible et plusieurs nœuds qui contiennent des attributs d'entrée et des valeurs. Pour plus d’informations, consultez [Contenu du modèle d’exploration de données pour les modèles d’arbre de décision &#40;Analysis Services – Exploration de données&#41;](/analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining).  
  
## <a name="using-the-flattened-keyword"></a>Utilisation du mot clé FLATTENED  
 Le contenu du modèle d'exploration de données contient fréquemment des informations intéressantes sur le modèle dans les colonnes de table imbriquée. Le mot clé FLATTENED vous permet de récupérer les données d'une colonne de table imbriquée sans utiliser de fournisseur qui prend en charge les ensembles de lignes hiérarchiques.  
  
 La requête suivante retourne un nœud unique, le nœud de statistiques marginales (NODE_TYPE = 26) d'un modèle Naive Bayes. Cependant, ce nœud contient une table imbriquée dans la colonne NODE_DISTRIBUTION. En conséquence, la colonne de table imbriquée est aplatie et une ligne est retournée pour chaque ligne de la table imbriquée. La valeur de la colonne scalaire MODEL_NAME est répétée pour chaque ligne de la table imbriquée.  
  
 Notez par ailleurs que si vous spécifiez uniquement le nom de la colonne de table imbriquée, une nouvelle colonne est retournée pour chaque colonne de la table. Par défaut, le nom de la table imbriquée est ajouté en préfixe au nom de chaque colonne de table.  
  
```  
SELECT FLATTENED MODEL_NAME, NODE_DISTRIBUTION  
FROM [TM_NaiveBayes].CONTENT  
WHERE NODE_TYPE = 26  
```  
  
 Résultats de l'exemple :  
  
|MODEL_NAME|NODE_DISTRIBUTION.ATTRIBUTE_NAME|NODE_DISTRIBUTION.ATTRIBUTE_VALUE|NODE_DISTRIBUTION.SUPPORT|NODE_DISTRIBUTION.PROBABILITY|NODE_DISTRIBUTION.VARIANCE|NODE_DISTRIBUTION.VALUETYPE|  
|-----------------|----------------------------------------|-----------------------------------------|--------------------------------|------------------------------------|---------------------------------|----------------------------------|  
|TM_NaiveBayes|Bike Buyer|Manquant|0|0|0|1|  
|TM_NaiveBayes|Bike Buyer|0|6556|0.506685215240745|0||  
|TM_NaiveBayes|Bike Buyer|1|6383|0.493314784759255|0||  
  
 L'exemple suivant montre comment retourner uniquement certaines des colonnes de la table imbriquée en utilisant une instruction sub-select. Vous pouvez simplifier l'affichage en utilisant un alias pour le nom de la table imbriquée, tel qu'indiqué.  
  
```  
SELECT MODEL_NAME,   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT] AS t  
FROM NODE_DISTRIBUTION)   
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 26  
```  
  
 Résultats de l'exemple :  
  
|MODEL_NAME|T.ATTRIBUTE_NAME|t.ATTRIBUTE_VALUE|t.SUPPORT|  
|-----------------|-----------------------|------------------------|---------------|  
|TM_NaiveBayes|Bike Buyer|Manquant|0|  
|TM_NaiveBayes|Bike Buyer|0|6556|  
|TM_NaiveBayes|Bike Buyer|1|6383|  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNER &#40;&#41;DMX ](../dmx/select-dmx.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
