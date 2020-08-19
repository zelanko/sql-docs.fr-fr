---
description: Barre oblique inverse (continuation de ligne) (Transact-SQL)
title: Barre oblique inverse (continuation de ligne) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/25/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '\_TSQL'
- '\'
dev_langs:
- TSQL
helpviewer_keywords:
- backwhack
- backslash
- escape character
- hack character
- '\ (backslash)'
- backslant
- bash
- reverse slant
- slosh
- reversed virgule
- line continuation character
- reverse solidus
ms.assetid: c97fbb20-3d12-4d0b-9b52-62a229bc83c0
author: rothja
ms.author: jroth
ms.openlocfilehash: 2437daed52cb8b4a79431465f8a27e5464185e23
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459281"
---
# <a name="backslash-line-continuation-transact-sql"></a>Barre oblique inverse (continuation de ligne) (Transact-SQL)

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

`\` scinde une constante de chaîne longue, un caractère ou un binaire en deux ou plusieurs lignes pour une meilleure lisibilité.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<first section of string> \  
<continued section of string>  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 \<first section of string>  
 Début d'une chaîne.  
  
 \<continued section of string>  
 Suite d'une chaîne.  
  
## <a name="remarks"></a>Notes  
Cette commande retourne les premières sections et les sections suivantes de la chaîne sous la forme d'une chaîne, sans la barre oblique inverse. La nouvelle ligne après la barre oblique inverse doit être un caractère de saut de ligne (U+000A) ou une combinaison de retour chariot (U+000D) et de saut de ligne (U+000A) dans cet ordre. 

## <a name="examples"></a>Exemples  

### <a name="a-splitting-a-character-string"></a>R. Fractionnement d’une chaîne de caractères  

L’exemple suivant utilise une barre oblique inverse et un retour chariot pour fractionner une chaîne de caractères en deux lignes.  
  
```  
SELECT 'abc\  
def' AS [ColumnResult];  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 abcdef
 ```    

### <a name="b-splitting-a-binary-string"></a>B. Fractionnement d’une chaîne binaire  

L’exemple suivant utilise une barre oblique inverse et un retour chariot pour fractionner une chaîne binaire en deux lignes.  

```  
SELECT 0xabc\
def AS [ColumnResult];  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 0xABCDEF
 ```    

## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Opérateurs &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [&#40;Division&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/divide-transact-sql.md)   
 [&#40;Affectation après division&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [Opérateurs composés &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  
