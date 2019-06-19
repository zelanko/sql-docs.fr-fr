---
title: Barre oblique inverse (continuation de ligne) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/09/2017
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
manager: craigg
ms.openlocfilehash: 4b03094aa0d75b2491e2635506c9a7b6563dacba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65981685"
---
# <a name="backslash-line-continuation-transact-sql"></a>Barre oblique inverse (continuation de ligne) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

`\` scinde une constante de chaîne longue, un caractère ou un binaire en deux ou plusieurs lignes pour une meilleure lisibilité.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<first section of string> \  
<continued section of string>  
```  
  
## <a name="arguments"></a>Arguments  
 \<first section of string>  
 Début d'une chaîne.  
  
 \<continued section of string>  
 Suite d'une chaîne.  
  
## <a name="remarks"></a>Notes   
 Cette commande retourne les premières sections et les sections suivantes de la chaîne sous la forme d'une chaîne, sans la barre oblique inverse.  

## <a name="examples"></a>Exemples  

### <a name="a-splitting-a-character-string"></a>A. Fractionnement d’une chaîne de caractères  

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

## <a name="see-also"></a> Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Opérateurs &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [&#40;Division&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/divide-transact-sql.md)   
 [&#40;Affectation après division&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [Opérateurs composés &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  
