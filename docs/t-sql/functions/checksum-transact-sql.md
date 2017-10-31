---
title: "Somme de contrôle (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKSUM_TSQL
- CHECKSUM
dev_langs:
- TSQL
helpviewer_keywords:
- hash indexes
- CHECKSUM function
- checksum values
ms.assetid: e26d3339-845c-49c2-9d89-243376874c13
caps.latest.revision: 44
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0379260c517f546bf00c5e757f6a3069f574f102
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="checksum-transact-sql"></a>CHECKSUM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

Retourne la valeur de somme de contrôle calculée à partir de la ligne d'une table ou à partir d'une liste d'expressions. CHECKSUM est destiné à être utilisé dans la création d'index de hachage.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CHECKSUM ( * | expression [ ,...n ] )  
```  
  
## <a name="arguments"></a>Arguments  
\*  
Spécifie que le calcul concerne toutes les colonnes de la table. CHECKSUM retourne une erreur si une colonne est d'un type de données non comparable. Types de données incomparables sont **texte**, **ntext**, **image**, XML, et **curseur**et également **sql_variant** avec l’un des types énumérés en tant que son type de base.
  
*expression*  
Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de n’importe quel type, à l’exception d’un type de données non comparable.
  
## <a name="return-types"></a>Types de retour
 **int**  
  
## <a name="remarks"></a>Notes  
CHECKSUM calcule une valeur de hachage, appelée somme de contrôle, sur sa liste d'arguments. La valeur de hachage est destinée à être utilisée dans la création d'index de hachage. Si les arguments de CHECKSUM sont des colonnes et qu'un index est créé sur la valeur CHECKSUM calculée, le résultat est un index de hachage qui peut être utilisé dans des recherches d'égalité sur les colonnes.
  
CHECKSUM a les propriétés d'une fonction de hachage : lorsque CHECKSUM est appliqué à deux listes d'expressions, la même valeur est retournée si les éléments correspondants dans les deux listes sont du même type et ont une valeur égale lorsqu'ils sont comparés à l'aide de l'opérateur d'égalité (=). Pour cette définition, les valeurs NULL d'un type spécifié sont considérées comme ayant une valeur de comparaison égale. Si l'une des valeurs de la liste d'expressions change, en général, la somme de contrôle de la liste change également. Il existe toutefois une faible probabilité pour que la somme de contrôle ne change pas. Pour cette raison, nous déconseillons d'utiliser CHECKSUM pour vérifier si des valeurs ont changé, à moins que votre application accepte de manquer parfois une modification. Envisagez d’utiliser [HashBytes](../../t-sql/functions/hashbytes-transact-sql.md) à la place. Lorsqu'un algorithme de hachage MD5 est spécifié, la probabilité que HashBytes retourne le même résultat pour deux entrées différentes est beaucoup plus faible que pour CHECKSUM.
  
L'ordre des expressions affecte la valeur du résultat de CHECKSUM. L'ordre des colonnes utilisé avec CHECKSUM (*) est celui spécifié dans la définition de la table ou de la vue, y compris les colonnes calculées.
  
La valeur de CHECKSUM dépend du classement. La même valeur stockée avec un autre classement retourne une valeur CHECKSUM différente.
  
## <a name="examples"></a>Exemples  
Les exemples suivants illustrent l'utilisation de `CHECKSUM` pour créer des index de hachage. L'index de hachage est créé en ajoutant une colonne de somme de contrôle calculée à la table à indexer, puis en générant un index sur la colonne de la somme de contrôle.
  
```sql
-- Create a checksum index.  
SET ARITHABORT ON;  
USE AdventureWorks2012;   
GO  
ALTER TABLE Production.Product  
ADD cs_Pname AS CHECKSUM(Name);  
GO  
CREATE INDEX Pname_index ON Production.Product (cs_Pname);  
GO  
```  
  
L'index de la somme de contrôle peut être utilisé comme un index de hachage, notamment pour améliorer la vitesse d'indexation lorsque la colonne à indexer est une colonne contenant des chaînes de caractères longues. L'index de la somme de contrôle peut être utilisé dans les recherches d'égalité.
  
```sql
/*Use the index in a SELECT query. Add a second search   
condition to catch stray cases where checksums match,   
but the values are not the same.*/  
SELECT *   
FROM Production.Product  
WHERE CHECKSUM(N'Bearing Ball') = cs_Pname  
AND Name = N'Bearing Ball';  
GO  
```  
  
La création de l'index dans une colonne calculée matérialise la colonne de la somme de contrôle, et toutes les modifications apportées à la valeur `ProductName` sont propagées à cette colonne. Un index peut aussi être créé directement sur la colonne indexée. Toutefois, lorsque les valeurs de clé sont longues, un index normal n'est probablement pas aussi performant qu'un index de somme de contrôle.
  
## <a name="see-also"></a>Voir aussi
[CHECKSUM_AGG &#40; Transact-SQL &#41;](../../t-sql/functions/checksum-agg-transact-sql.md)  
[HASHBYTES &#40; Transact-SQL &#41;](../../t-sql/functions/hashbytes-transact-sql.md)  
[BINARY_CHECKSUM &#40; Transact-SQL &#41;](../../t-sql/functions/binary-checksum-transact-sql.md)
  
  

