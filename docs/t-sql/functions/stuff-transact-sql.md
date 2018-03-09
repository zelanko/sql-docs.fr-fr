---
title: STUFF (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 11/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STUFF
- STUFF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting characters
- STUFF function
- length characters
- removing characters
- replacing characters
- characters [SQL Server], replacing
- inserting data
ms.assetid: abb0afa9-44f6-42a2-a871-5f471dfb222b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 10edb8b1b1e3008321bc03e2e65419dca8956f86
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="stuff-transact-sql"></a>STUFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  La fonction STUFF permet d'insérer une chaîne dans une autre chaîne. Elle efface d'abord le nombre de caractères spécifié dans la première chaîne à partir de la position de début. Ensuite, elle insère la seconde chaîne dans la première à partir de la position de début.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STUFF ( character_expression , start , length , replaceWith_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *character_expression*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) des données de caractères. *character_expression* peut être une constante, une variable ou une colonne de données binaire ou caractère.  
  
 *start*  
 Entier précisant la position de départ de la suppression et de l'insertion. Si *Démarrer* est un nombre négatif ou égal à zéro, une chaîne null est retournée. Si *Démarrer* est plus longue que la première *character_expression*, une chaîne null est retournée. *Démarrer* peut être de type **bigint**.  
  
 *length*  
 Entier spécifiant le nombre de caractères à supprimer. Si *longueur* est négatif, une chaîne null est retournée. Si *longueur* est plus longue que la première *character_expression*, suppression s’effectue jusqu’au dernier caractère de la dernière *character_expression*.  Si *longueur* est égal à zéro, d’insertion se produit avant le premier caractère dans la chaîne. *longueur* peut être de type **bigint**.

 *replaceWith_expression*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) des données de caractères. *character_expression* peut être une constante, une variable ou une colonne de données binaire ou caractère. Cette expression remplace *longueur* caractères de *character_expression* commençant à *Démarrer*. Fournissant `NULL` comme le *replaceWith_expression*, supprime les caractères sans insérer quoi que ce soit.   
  
## <a name="return-types"></a>Types de retour  
 Données de type caractère si *character_expression* est un des types de données caractères pris en charge. Retourne des données binaires si *character_expression* est un des types de données binaires pris en charge.  
  
## <a name="remarks"></a>Notes  
 Si la valeur de la position de début ou de la longueur est négative, ou bien si la valeur de la position de début est supérieure à la longueur de la première chaîne, une chaîne NULL est retournée. Si la position de départ est 0, une valeur NULL est retournée. Si la longueur à effacer est supérieure à celle de la première chaîne, tous les caractères de la première chaîne sont effacés à partir du caractère du début.  

Une erreur se produit si la valeur résultante est plus grande que le maximum pris en charge par le type retourné.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caractères supplémentaires (paires de substitution)  
 Lors de l’utilisation de classements SC, les deux *character_expression* et *replaceWith_expression* peuvent inclure des paires de substitution. Le paramètre de longueur compte chaque caractère de substitution *character_expression* comme un caractère unique.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, la procédure retourne une chaîne de caractères créée en supprimant trois caractères de la première chaîne (`abcdef`) à partir de la position `2` (c'est-à-dire au niveau du `b`) et en insérant la seconde chaîne au point de suppression.  
  
```  
SELECT STUFF('abcdef', 2, 3, 'ijklmn');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------   
aijklmnef   
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
