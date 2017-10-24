---
title: (Barre oblique inverse) (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- '\_TSQL'
- '\'
dev_langs:
- TSQL
helpviewer_keywords:
- backwhack
- backslash
- excape character
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
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 011025d20b6341b9fa43b25f6c14c91a135a6ffa
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-utilities-statements---backslash"></a>Instructions d’utilitaires SQL Server - barre oblique inverse
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Fournit des commandes qui ne sont pas [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions, mais sont reconnues par le **sqlcmd** et **osql** utilitaires et [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] éditeur de Code. Ces commandes facilitent la lisibilité et l'exécution de lots et de scripts.  
  
\ interrompt une longue chaîne constante dans deux ou plusieurs lignes pour une meilleure lisibilité.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<first section of string> \  
<continued section of string>  
```  
  
## <a name="arguments"></a>Arguments  
 \<première section de chaîne >  
 Début d'une chaîne.  
  
 \<suite de la section de chaîne >  
 Suite d'une chaîne.  
  
## <a name="remarks"></a>Notes  
 Cette commande retourne les premières sections et les sections suivantes de la chaîne sous la forme d'une chaîne, sans la barre oblique inverse.  
  
 La barre oblique inverse n'est pas une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. Il s’agit d’une commande qui est reconnue par le **sqlcmd** et **osql** utilitaires et [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] éditeur de Code.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise une barre oblique inverse et un retour chariot pour fractionner la chaîne en deux lignes.  
  
```  
SELECT 'abc\  
def' AS ColumnResult;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 abcdef
 ```    
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [&#40; division &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/divide-transact-sql.md)   
 [&#40; diviser égal &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [Compound, opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  

