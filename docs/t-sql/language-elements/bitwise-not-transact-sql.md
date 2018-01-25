---
title: ~ (NOT au niveau du bit) (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ~_TSQL
- bitwise
- NOT
- ~
- Bitwise NOT
dev_langs: TSQL
helpviewer_keywords:
- NOT keyword
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: 02da8016-f6c0-41ae-8d59-33eaa02bfc95
caps.latest.revision: "42"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bc129a0a62c393cb8aee03edca3e0c2b567f9488
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="-bitwise-not-transact-sql"></a>~ (NOT exclusif au niveau du bit) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Exécute une opération logique NOT au niveau du bit sur une valeur entière.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
~ expression  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md) de l’un des types de données de la catégorie de type de données entier, le **bits**, ou **binaire** ou **varbinary** des types de données. *expression* est traité comme un nombre binaire pour l’opération au niveau du bit.  
  
> [!NOTE]  
>  Seul *expression* peut être du type **binaire** ou **varbinary** type de données dans une opération au niveau du bit.  
  
## <a name="result-types"></a>Types des résultats  
 **int** si les valeurs d’entrée sont **int**.  
  
 **smallint** si les valeurs d’entrée sont **smallint**.  
  
 **tinyint** si les valeurs d’entrée sont **tinyint**.  
  
 **bit** si les valeurs d’entrée sont **bits**.  
  
## <a name="remarks"></a>Notes  
 Le  **~**  opérateur au niveau du bit exécute un NOT logique au niveau du bit pour le *expression*, en évaluant chaque bit. Si *expression* a la valeur 0, dans le jeu de résultats, les bits sont définis sur 1 ; sinon, le bit du résultat est mis à la valeur 0. En d'autres termes, les uns sont changés en zéros et les zéros sont changés en uns.  
  
> [!IMPORTANT]  
>  Quelle que soit l'opération au niveau du bit que vous effectuez, la longueur d'enregistrement de l'expression sur laquelle porte l'opération est importante. Il est recommandé d'utiliser le même nombre d'octets lors du stockage des valeurs. Par exemple, stocker la valeur décimale 5 en un **tinyint**, **smallint**, ou **int** produit une valeur stockée avec différents nombres d’octets : **tinyint** stocke des données à l’aide de 1 octet ; **smallint** stocke des données à l’aide de 2 octets, et **int** stocke des données à l’aide de 4 octets. Par conséquent, effectuant une opération au niveau du bit sur une **int** valeur décimale peut produire des résultats différents de ceux à l’aide d’une conversion directe de binaire ou en hexadécimale, en particulier lorsque le  **~**  (NOT au niveau du bit) opérateur est utilisé. L'opération NOT au niveau du bit peut se produire sur une variable plus courte. Dans ce cas, lorsque la variable plus courte est convertie en un type de données plus long, les bits des 8 bits de gauche risquent d'avoir une valeur imprévue. Nous vous recommandons de convertir d'abord la variable de type de données courte dans le type de données plus long, et d'exécuter ensuite l'opération NOT sur le résultat.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une table à l’aide de la **int** type pour stocker les valeurs de données et insère les deux valeurs dans une ligne.  
  
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
  
 La requête suivante exécute l'opération NOT au niveau du bit sur les colonnes `a_int_value` et `b_int_value`.  
  
```  
SELECT ~ a_int_value, ~ b_int_value  
FROM bitwise;  
```  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
--- ---   
-171  -76   
  
(1 row(s) affected)  
```  
  
 La représentation binaire de 170 (`a_int_value` ou `A`) est `0000 0000 1010 1010`. L'exécution de l'opération NOT au niveau du bit sur cette valeur produit le résultat binaire `1111 1111 0101 0101`, qui est la valeur décimale -171. La représentation binaire pour 75 est `0000 0000 0100 1011`. L'exécution de l'opération NOT au niveau du bit produit `1111 1111 1011 0100`, qui est -76 en notation décimale.  
  
```  
 (~A)     
         0000 0000 1010 1010  
         -------------------  
         1111 1111 0101 0101  
(~B)     
         0000 0000 0100 1011  
         -------------------  
         1111 1111 1011 0100  
```  
  
 
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Opérateurs de bits &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  


