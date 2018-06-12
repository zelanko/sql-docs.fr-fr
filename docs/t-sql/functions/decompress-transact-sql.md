---
title: DECOMPRESS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/30/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DECOMPRESS
- DECOMPRESS_TSQL
helpviewer_keywords:
- DECOMPRESS function
ms.assetid: 738d56be-3870-4774-b112-3dce27becc11
caps.latest.revision: 8
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2b6412856e373c3b1ad5ac838f9b15486d451a2b
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779195"
---
# <a name="decompress-transact-sql"></a>DECOMPRESS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Cette fonction décompresse une valeur d’expression d’entrée à l’aide de l’algorithme GZIP. `DECOMPRESS` retourne un tableau d’octets (type VARBINARY(MAX)).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DECOMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
Valeur **varbinary(***n***)**, **varbinary(max)** ou **binary(***n***)**. Pour plus d’informations, consultez [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Types de retour  
Valeur ayant le type de données **varbinary(max)**. `DECOMPRESS` utilise l’algorithme ZIP pour décompresser l’argument d’entrée. Si nécessaire, l’utilisateur doit explicitement caster le résultat en type de cible.  
  
## <a name="remarks"></a>Notes   
  
## <a name="examples"></a>Exemples  
  
### <a name="a-decompress-data-at-query-time"></a>A. Décompresser les données au moment de la requête  
Cet exemple montre comment retourner des données de table compressées :  
  
```  
SELECT _id, name, surname, datemodified,  
             CAST(DECOMPRESS(info) AS NVARCHAR(MAX)) AS info  
FROM player;  
```  
  
### <a name="b-display-compressed-data-using-computed-column"></a>B. Afficher les données compressées à l’aide d’une colonne calculée  
Cet exemple montre comment créer une table de stockage des données décompressées :  
  
```  
CREATE TABLE example_table (  
    _id int primary key identity,  
    name nvarchar(max),  
    surname nvarchar(max),  
    info varbinary(max),  
    info_json as CAST(decompress(info) as nvarchar(max))  
);  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [COMPRESS &#40;Transact-SQL&#41;](../../t-sql/functions/compress-transact-sql.md)  
  
  
