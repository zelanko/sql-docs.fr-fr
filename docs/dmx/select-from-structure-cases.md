---
title: Sélectionnez à &lt;partir&gt;de la structure. CAS | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 041d6ade2363b4a33528bd44438a2fcb440d61ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928293"
---
# <a name="select-from-ltstructuregtcases"></a>Sélectionnez à &lt;partir&gt;de la structure. PARFOIS
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne les cas utilisés pour créer la structure d'exploration de données.  
  
 Si l'extraction n'est pas activée sur la structure, l'instruction échoue. Par ailleurs, l'instruction échoue si l'utilisateur ne dispose pas d'autorisations d'extraction sur la structure d'exploration de données.  
  
 Dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], l’extraction sur les nouvelles structures d’exploration de données est activée par défaut. Pour vérifier si l’extraction est activée pour une structure particulière, vérifiez si la valeur de la propriété **CacheMode** est définie sur **KeepTrainingCases**.  
  
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
 facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste d'expressions séparées par des virgules.  
  
 Une expression peut inclure des identificateurs de colonne, des fonctions définies par l'utilisateur et des fonctions VBA.  
  
 *arborescence*  
 Nom de la structure.  
  
 *expression de condition*  
 Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *formule*  
 facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Si l'extraction est activée à la fois sur le modèle et sur la structure, les membres d'un rôle qui dispose d'autorisations d'extraction sur la structure d'exploration de données et le modèle d'exploration de données peuvent retourner des colonnes de structure qui n'étaient pas incluses dans le modèle en utilisant la syntaxe suivante :  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Par conséquent, pour protéger des données sensibles ou des informations personnelles, vous devez construire votre vue de source de données pour masquer les informations personnelles et accorder l’autorisation **AllowDrillThrough** sur une structure d’exploration de données ou un modèle d’exploration de données uniquement lorsque cela est nécessaire.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants sont basés sur la structure d’exploration de données, le publipostage ciblé, qui [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] est basé sur la base de données et les modèles d’exploration de données associés. Pour plus d’informations, consultez le didacticiel sur l' [exploration de données de base](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
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
 [SÉLECTIONNER &#40;&#41;DMX](../dmx/select-dmx.md)   
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
