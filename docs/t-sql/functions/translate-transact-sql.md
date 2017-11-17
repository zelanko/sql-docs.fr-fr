---
title: TRADUIRE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
caps.latest.revision: 5
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 583c414206a0acc79d1abdfff34728c38711a855
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="translate-transact-sql"></a>TRADUIRE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Retourne la chaîne fournie comme premier argument une fois que des caractères spécifiés dans le deuxième argument sont traduites en un jeu de destination de caractères.

## <a name="syntax"></a>Syntaxe   
```
TRANSLATE ( inputString, characters, translations) 
```

## <a name="arguments"></a>Arguments   

inputString   
Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de n’importe quel type de caractère (nvarchar, varchar, nchar, char).

caractères   
Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de n’importe quel type de caractère contenant des caractères qui doivent être remplacés.

traductions   
Est un caractère [expression](../../t-sql/language-elements/expressions-transact-sql.md) correspondant au deuxième argument de type et de longueur.

## <a name="return-types"></a>Types de retour   
Retourne une expression de caractères du même type que `inputString` où les caractères du deuxième argument sont remplacés par les caractères correspondants à partir du troisième argument.

## <a name="remarks"></a>Notes   

`TRANSLATE`fonction retournera une erreur si des caractères et des traductions ont des longueurs différentes. `TRANSLATE`fonction doit retourner l’entrée inchangée si les valeurs null sont fournies en tant que caractères ou des arguments de remplacement. Le comportement de la `TRANSLATE` fonction doit être identique à la [remplacer](../../t-sql/functions/replace-transact-sql.md) (fonction).   

Le comportement de la `TRANSLATE` fonction est équivalente à l’utilisation de plusieurs `REPLACE` fonctions.

`TRANSLATE`est toujours classement SC prenant en charge.

## <a name="examples"></a>Exemples   

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. Remplacez le carré et des accolades régulière entre accolades    
La requête suivante remplace le carré et des accolades dans la chaîne d’entrée entre parenthèses :
```
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
2*(3+4)/(7-2)
```

>  [!NOTE]
>  Le `TRANSLATE` fonction dans cet exemple est équivalent à mais beaucoup plus simple que l’instruction suivante en utilisant `REPLACE`:`SELECT REPLACE(REPLACE(REPLACE(REPLACE('2*[3+4]/{7-2}','[','('), ']', ')'), '{', '('), '}', ')');` 


###  <a name="b-convert-geojson-points-into-wkt"></a>B. Convertir les points GeoJSON WKT    
GeoJSON est un format d’encodage de diverses structures de données géographiques. Avec la `TRANSLATE` (fonction), les développeurs peuvent facilement convertir les points GeoJSON au format WKT et vice versa. La requête suivante remplace le carré et des accolades dans l’entrée régulière entre accolades :   
```tsql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   


|Point  |Coordonnées |  
---------|--------- |
(137.4  72.3) |[137.4,72.3] |


## <a name="see-also"></a>Voir aussi

[Fonctions de chaîne (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   
[REPLACE (Transact-SQL)](../../t-sql/functions/replace-transact-sql.md)   


