---
description: Sélectionnez à partir de la &lt; structure &gt; . PARFOIS
title: Sélectionnez à partir de la &lt; structure &gt; . CAS | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cf8afcdf84c5d33e91971c58dff5c1f93c68fd08
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726126"
---
# <a name="select-from-ltstructuregtcases"></a>Sélectionnez à partir de la &lt; structure &gt; . PARFOIS
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Retourne les cas utilisés pour créer la structure d'exploration de données.  
  
 Si l'extraction n'est pas activée sur la structure, l'instruction échoue. Par ailleurs, l'instruction échoue si l'utilisateur ne dispose pas d'autorisations d'extraction sur la structure d'exploration de données.  
  
 Dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , l’extraction sur les nouvelles structures d’exploration de données est activée par défaut. Pour vérifier si l’extraction est activée pour une structure particulière, vérifiez si la valeur de la propriété **CacheMode** est définie sur **KeepTrainingCases**.  
  
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
  
 *arborescence*  
 Nom de la structure.  
  
 *expression de condition*  
 Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Facultatif. Expression retournant une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Si l'extraction est activée à la fois sur le modèle et sur la structure, les membres d'un rôle qui dispose d'autorisations d'extraction sur la structure d'exploration de données et le modèle d'exploration de données peuvent retourner des colonnes de structure qui n'étaient pas incluses dans le modèle en utilisant la syntaxe suivante :  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Par conséquent, pour protéger des données sensibles ou des informations personnelles, vous devez construire votre vue de source de données pour masquer les informations personnelles et accorder l’autorisation **AllowDrillThrough** sur une structure d’exploration de données ou un modèle d’exploration de données uniquement lorsque cela est nécessaire.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants sont basés sur la structure d’exploration de données, le publipostage ciblé, qui est basé sur la [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] base de données et les modèles d’exploration de données associés. Pour plus d’informations, consultez le didacticiel sur l' [exploration de données de base](/previous-versions/sql/sql-server-2016/ms167167(v=sql.130)).  
  
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
 [SÉLECTIONNER &#40;&#41;DMX ](../dmx/select-dmx.md)   
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
