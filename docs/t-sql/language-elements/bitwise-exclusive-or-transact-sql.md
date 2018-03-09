---
title: "^ (Opérateur de bits OR Exclusive) (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ^_TSQL
- Bitwise Exclusive OR
- Exclusive
- ^
- bitwise
- OR
dev_langs:
- TSQL
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- OR operator
- exclusive OR mathematical operations
- bitwise exclusive OR (^)
ms.assetid: f38f0ad4-46d0-40ea-9851-0f928fda5293
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b5833bd94dd28f6c09b2f1c05d4a59a8a137ddad
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="-bitwise-exclusive-or-transact-sql"></a>^ (OR exclusif au niveau du bit) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Effectue une opération OR exclusive au niveau du bit entre deux valeurs entières.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression ^ expression  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md) de l’un des types de données de la catégorie de type de données entier, ou le **bits**, ou **binaire** ou **varbinary** des types de données. *expression* est traité comme un nombre binaire pour l’opération au niveau du bit.  
  
> [!NOTE]  
>  Seul *expression* peut être du type **binaire** ou **varbinary** type de données dans une opération au niveau du bit.  
  
## <a name="result-types"></a>Types des résultats  
 **int** si les valeurs d’entrée sont **int**.  
  
 **smallint** si les valeurs d’entrée sont **smallint**.  
  
 **tinyint** si les valeurs d’entrée sont **tinyint**.  
  
## <a name="remarks"></a>Notes  
 Le  **^**  opérateur au niveau du bit exécute un opérateur logique OR exclusif au niveau du bit entre les deux expressions, évaluant chaque bit pour les deux expressions correspondant. Dans le résultat, les bits prennent la valeur 1 si l'un ou l'autre (mais pas les deux) des bits correspondants (pour la position en cours d'évaluation) dans les deux expressions d'entrées ont une valeur de 1 Si les deux bits ont pour valeur 0 ou 1, le bit du résultat prend la valeur 0.  
  
 Si les expressions de gauche et droite ont des types de données entiers différents (par exemple, sur la gauche *expression* est **smallint** et du droit *expression* est **int**), l’argument du type de données plus petit est converti au type de données plus volumineux. Dans ce cas, le **smallint *** expression* est converti en un **int**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une table à l’aide de la **int** données de type pour stocker les valeurs d’origine et insère deux valeurs dans une ligne.  
  
```  
CREATE TABLE bitwise  
(   
a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 La requête suivante effectue l'opération OR exclusif au niveau du bit sur les colonnes `a_int_value` et `b_int_value`.  
  
```  
SELECT a_int_value ^ b_int_value  
FROM bitwise;  
GO  
```  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
-----------   
225           
  
(1 row(s) affected)  
```  
  
 La représentation binaire de 170 (`a_int_value` ou `A`) est `0000 0000 1010 1010`. La représentation binaire de 75 (`b_int_value` ou `B`) est `0000 0000 0100 1011`. L'exécution de l'opération OR exclusif au niveau du bit sur ces deux valeurs donne le résultat binaire `0000 0000 1110 0001`, soit 225 en notation décimale.  
  
```  
(A ^ B)     
         0000 0000 1010 1010  
         0000 0000 0100 1011  
         -------------------  
         0000 0000 1110 0001  
```  
  

  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Opérateurs de bits &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [^ = &#40; Opérateur de bits OR exclusif affectation &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)   
 [Compound, opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


