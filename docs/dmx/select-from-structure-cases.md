---
title: SELECT FROM &lt;structure&gt;. CAS | Documents Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f473cb42230aec0b5e40fb59fe10b2f34013ba2f
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842102"
---
# <a name="select-from-ltstructuregtcases"></a>SELECT FROM &lt;structure&gt;. CAS
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 Facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste d'expressions séparées par des virgules.  
  
 Une expression peut inclure des identificateurs de colonne, des fonctions définies par l'utilisateur et des fonctions VBA.  
  
 *structure*  
 Nom de la structure.  
  
 *Expression de condition*  
 Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Facultatif. Expression qui retourne une valeur scalaire.  
  
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
 [SÉLECTIONNEZ &AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [Data Mining Extensions &#40;DMX&#41; instructions de définition de données](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;DMX&#41; instructions de Manipulation de données](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
