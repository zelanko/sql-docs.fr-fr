---
title: TRANSLATE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a72ef38b960e00a88c7d4e1e0038e32a897a46d9
ms.sourcegitcommit: 467b2c708651a3a2be2c45e36d0006a5bbe87b79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53980115"
---
# <a name="translate-transact-sql"></a>TRANSLATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Retourne la chaîne fournie comme premier argument une fois que des caractères spécifiés dans le deuxième argument sont traduits en un jeu de caractères de destination spécifié dans le troisième argument.

## <a name="syntax"></a>Syntaxe   
```
TRANSLATE ( inputString, characters, translations) 
```

## <a name="arguments"></a>Arguments   

 *inputString*   
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) de chaîne à rechercher. *inputString* peut être n’importe quel type de données caractère (nvarchar, varchar, nchar, char).

 *characters*   
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) de chaîne contenant des caractères à remplacer. *characters* peut être n’importe quel type de données caractère.

*translations*   
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) de chaîne contenant les caractères de remplacement. *translations* doit être du même type de données et de même longueur que *characters*.

## <a name="return-types"></a>Types de retour   
Retourne une expression de caractères du même type de données que `inputString`, où les caractères du deuxième argument sont remplacés par les caractères correspondants du troisième argument.

## <a name="remarks"></a>Notes    

`TRANSLATE` retourne une erreur si les expressions *characters* et *translations* ont des longueurs différentes. `TRANSLATE` retourne NULL si un des arguments est NULL.  

Le comportement de la fonction `TRANSLATE` est similaire à l’utilisation de plusieurs fonctions [REPLACE](../../t-sql/functions/replace-transact-sql.md). `TRANSLATE` ne remplace cependant pas un caractère plusieurs fois. Ceci diffère de fonctions `REPLACE` multiples, car chaque utilisation remplace tous les caractères appropriés. 


`TRANSLATE` est toujours conscient du classement SC.

## <a name="examples"></a>Exemples   

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. Remplacer les crochets et les accolades par des parenthèses    
La requête suivante remplace les crochets et les accolades dans la chaîne d’entrée par des parenthèses :
```
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
2*(3+4)/(7-2)
```

#### <a name="equivalent-calls-to-replace"></a>Appels équivalents à REPLACE

Dans l’instruction SELECT suivante, il existe un groupe de quatre appels imbriqués à la fonction REPLACE. Ce groupe est équivalent à l’appel unique de la fonction TRANSLATE dans l’instruction SELECT précédente :

```sql
SELECT
REPLACE
(
      REPLACE
      (
            REPLACE
            (
                  REPLACE
                  (
                        '2*[3+4]/{7-2}',
                        '[',
                        '('
                  ),
                  ']',
                  ')'
            ),
            '{',
            '('
      ),
      '}',
      ')'
);
```

###  <a name="b-convert-geojson-points-into-wkt"></a>b. Convertir les points GeoJSON en WKT    
GeoJSON est un format d’encodage de diverses structures de données géographiques. Avec la fonction `TRANSLATE`, les développeurs peuvent facilement convertir les points GeoJSON au format WKT et vice versa. La requête suivante remplace les crochets et les accolades dans l’entrée par des parenthèses :   
```sql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   


|Point  |Coordinates |  
---------|--------- |
(137.4  72.3) |[137.4,72.3] |


### <a name="c-use-the-translate-function"></a>C. Utiliser la fonction TRANSLATE

```sql
SELECT TRANSLATE('abcdef','abc','bcd') AS Translated,
       REPLACE(REPLACE(REPLACE('abcdef','a','b'),'b','c'),'c','d') AS Replaced;
```

Les résultats sont :

| Traduit | Remplacé |  
| ---------|--------- |
| bcddef | ddddef |


## <a name="see-also"></a> Voir aussi
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [Fonctions de chaîne (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   

