---
title: STRING_ESCAPE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 02/25/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STRING_ESCAPE
- STRING_ESCAPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_ESCAPE function
ms.assetid: 2163bc7a-3816-4304-9c40-8954804f5465
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 41f969e292eff76c9a836ccd3177519d88e355ac
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stringescape-transact-sql"></a>STRING_ESCAPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Échappe les caractères spéciaux dans les textes et renvoie le texte avec des caractères d’échappement. **STRING_ESCAPE** est une fonction déterministe.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STRING_ESCAPE( text , type )  
```  
  
## <a name="arguments"></a>Arguments  
 *text*  
 Est un **nvarchar**[expression](../../t-sql/language-elements/expressions-transact-sql.md) expression représentant l’objet qui devrait être échappé.  
  
 *type*  
 Règles d’échappement qui seront appliqués. La valeur prise en charge actuellement est `'json'`.  
  
## <a name="return-types"></a>Types de retour  
 **nvarchar (max)** texte avec séquence d’échappement spéciaux et les caractères de contrôle. Actuellement **STRING_ESCAPE** uniquement échapper des caractères spéciaux JSON indiqués dans les tableaux suivants.  
  
|Caractère spécial|Séquence codée|  
|-----------------------|----------------------|  
|guillemets (")|\\"|  
|barre oblique inversée (\\)|\\\|  
|barre oblique (/)|\\/|  
|Retour arrière|\b|  
|Saut de page|\f|  
|Nouvelle ligne|\n|  
|Retour chariot|\r|  
|Tabulation horizontale|\t|  
  
|Caractère de contrôle|Séquence codée|  
|-----------------------|----------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|...|...|  
|CHAR(31)|\u001f|  
  
## <a name="remarks"></a>Notes  
  
## <a name="examples"></a>Exemples  
  
### <a name="a--escape-text-according-to-the-json-formatting-rules"></a>A.  Séquence d’échappement de texte selon la mise en forme des règles JSON  
 La requête suivante échappe les caractères spéciaux, à l’aide de règles de JSON et renvoie le texte avec séquence d’échappement.  
  
```  
SELECT STRING_ESCAPE('\   /  
\\    "     ', 'json') AS escapedText;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
escapedText  
-------------------------------------------------------------  
\\\t\/\n\\\\\t\"\t
```  
  
### <a name="b-format-json-object"></a>B. Format de l’objet JSON  
 La requête suivante crée un texte JSON à partir de variables de chaîne et de nombre et échappe les caractères spéciaux JSON dans des variables.  
  
```  
SET @json = FORMATMESSAGE('{ "id": %d,"name": "%s", "surname": "%s" }',   
    17, STRING_ESCAPE(@name,'json'), STRING_ESCAPE(@surname,'json') );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [SOUS-chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/substring-transact-sql.md)  
  
  

