---
title: SELECT FROM &lt;structure&gt;. CAS | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT
- CASES
- FROM
dev_langs:
- DMX
helpviewer_keywords:
- SELECT FROM <structure> statements
ms.assetid: 36f50213-14dc-42da-b899-20240b781e1a
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8af8e861c74c92be83e8ed61893d9a02587aa9a3
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="select-from-ltstructuregtcases"></a>SELECT FROM &lt;structure&gt;. CAS
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les cas utilisés pour créer la structure d'exploration de données.  
  
 Si l'extraction n'est pas activée sur la structure, l'instruction échoue. Par ailleurs, l'instruction échoue si l'utilisateur ne dispose pas d'autorisations d'extraction sur la structure d'exploration de données.  
  
 Dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], l’extraction sur de nouvelles structures d’exploration de données est activée par défaut. Pour vérifier si l’extraction est activée pour une structure particulière, vérifiez si la valeur de la **CacheMode** est définie sur **KeepTrainingCases**.  
  
 Si la valeur de **CacheMode** est remplacée par **ClearAfterProcessing**, les cas de structure sont effacés du cache et vous ne pouvez pas utiliser l’extraction.  
  
> [!NOTE]  
>  Vous ne pouvez pas activer ou désactiver l'extraction sur la structure d'exploration de données à l'aide des extensions DMX (Data Mining Extensions).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [TOP n] <expression list> FROM <structure>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 Ce paramètre est facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste d'expressions séparées par des virgules.  
  
 Une expression peut inclure des identificateurs de colonne, des fonctions définies par l'utilisateur et des fonctions VBA.  
  
 *structure*  
 Nom de la structure.  
  
 *expression de condition*  
 Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Ce paramètre est facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Si l'extraction est activée à la fois sur le modèle et sur la structure, les membres d'un rôle qui dispose d'autorisations d'extraction sur la structure d'exploration de données et le modèle d'exploration de données peuvent retourner des colonnes de structure qui n'étaient pas incluses dans le modèle en utilisant la syntaxe suivante :  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Par conséquent, pour protéger les données sensibles ou personnelles, vous devez construire votre vue de source de données pour masquer les informations personnelles et accorder **AllowDrillthrough** sur une structure d’exploration de données ou d’un modèle d’exploration de données uniquement lorsque cela est nécessaire.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants sont basés sur la structure d’exploration de données Targeted Mailing, qui est basé sur le [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] de base de données et les modèles d’exploration de données associée. Pour plus d’informations, consultez [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
### <a name="example-1-drill-through-to-structure-cases"></a>Exemple 1 : Extraction dans des cas de structure  
 L'exemple suivant retourne une liste des 500 clients les plus anciens dans la structure d'exploration de données Targeted Mailing. La requête retourne toutes les colonnes dans le modèle d'exploration de données, mais restreint les lignes aux clients qui ont acheté un vélo et les classe par âge. Vous pouvez aussi modifier la liste d'expressions pour retourner uniquement les colonnes dont vous avez besoin.  
  
```  
SELECT TOP 500 *  
FROM [Targeted Mailing].Cases  
WHERE [Bike Buyer] = 1  
ORDER BY Age DESC;  
```  
  
### <a name="example-2-drillthrough-to-test-or-training-cases-only"></a>Exemple 2 : Extraction dans des cas de test ou d'apprentissage uniquement  
 L'exemple suivant retourne une liste des cas de structure pour Targeted Mailing qui sont réservés au test. Si la structure d'exploration de données ne contient pas de jeu de test de données d'exclusion, tous les cas sont traités par défaut comme des cas d'apprentissage et cette requête retourne 0 cas.  
  
```  
SELECT [Customer Key], Gender, Age  
FROM [Targeted Mailing].Cases  
WHERE IsTestCase();  
```  
  
 Pour retourner les cas d'apprentissage, utilisez à la place la fonction `IsTrainingCase()`.  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNEZ &#40; DMX &#41;](../dmx/select-dmx.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence des instructions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

