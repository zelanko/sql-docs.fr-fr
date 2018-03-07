---
title: "DÉCOMPRESSER (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 11/30/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECOMPRESS
- DECOMPRESS_TSQL
helpviewer_keywords:
- DECOMPRESS function
ms.assetid: 738d56be-3870-4774-b112-3dce27becc11
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2988959b7ec3f9eccad74b752e7643f1e6675590
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="decompress-transact-sql"></a>DÉCOMPRESSER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Décompresser une expression d’entrée à l’aide d’algorithme GZIP. Résultat de la compression est un tableau d’octets (type varbinary (max)).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DECOMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Est un **varbinary (***n***)**, **varbinary (max)**, ou **binaire (***n***)**. Pour plus d’informations, consultez [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="return-types"></a>Types de retour  
 Retourne le type de données **varbinary (max)** type. L’argument d’entrée est décompressé à l’aide de l’algorithme ZIP. L’utilisateur doit explicitement convertir résultat en un type de cible si nécessaire.  
  
## <a name="remarks"></a>Notes  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-decompress-data-at-query-time"></a>A. Décompresser les données au moment de la requête  
 L’exemple suivant montre comment afficher les compresse les données à partir d’une table :  
  
```  
SELECT _id, name, surname, datemodified,  
             CAST(DECOMPRESS(info) AS NVARCHAR(MAX)) AS info  
FROM player;  
```  
  
### <a name="b-display-compressed-data-using-computed-column"></a>B. Afficher les données compressées à l’aide de la colonne calculée  
 L’exemple suivant montre comment créer une table pour stocker des données décompressées :  
  
```  
CREATE TABLE (  
    _id int primary key identity,  
    name nvarchar(max),  
    surname nvarchar(max),  
    info varbinary(max),  
    info_json as CAST(decompress(info) as nvarchar(max))  
);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [COMPRESS &#40; Transact-SQL &#41;](../../t-sql/functions/compress-transact-sql.md)  
  
  
