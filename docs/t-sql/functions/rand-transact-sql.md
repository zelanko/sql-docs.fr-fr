---
title: RAND (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RAND
- RAND_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RAND function
- values [SQL Server], random float
- random float value
ms.assetid: 363c84d6-b9fa-49ba-9a75-e44f27535ff6
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b1d358122487d3568167021ac3a296e1eb2d1974
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="rand-transact-sql"></a>RAND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Retourne un pseudo-aléatoire **float** comprise entre 0 et 1, exclusive.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RAND ( [ seed ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *valeur initiale*  
 Est un entier [expression](../../t-sql/language-elements/expressions-transact-sql.md) (**tinyint**, **smallint**, ou **int**) qui donne la valeur de départ. Si *seed* n’est pas spécifié, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] affecte une valeur de départ aléatoire. Pour une valeur de départ spécifiée, le résultat retourné est toujours le même.  
  
## <a name="return-types"></a>Types de retour  
 **float**  
  
## <a name="remarks"></a>Notes  
 Les appels répétitifs de RAND() avec la même valeur de départ retournent les mêmes résultats.  
  
 Pour une connexion, si RAND() est appelé avec une valeur de départ spécifiée, tous les appels ultérieurs de RAND() produisent des résultats en fonction de l'appel de départ RAND(). Ainsi, la requête suivante produit toujours la même séquence de numéros.  
  
```  
SELECT RAND(100), RAND(), RAND()   
```  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant produit quatre numéros aléatoires différents avec la fonction RAND.  
  
```  
DECLARE @counter smallint;  
SET @counter = 1;  
WHILE @counter < 5  
   BEGIN  
      SELECT RAND() Random_Number  
      SET @counter = @counter + 1  
   END;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions mathématiques &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  
