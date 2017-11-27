---
title: "Sélectionnez @local_variable (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- variable_TSQL
- '@loca_variable'
- '@local'
- variable
- '@loca_variable_TSQL'
- '@local_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- variables [SQL Server], assigning
- SELECT statement [SQL Server], @local_variable
- '@local_variable'
- local variables [SQL Server]
ms.assetid: 8e1a9387-2c5d-4e51-a1fd-a2a95f026d6f
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 56303a563bce3def564fe3b92067eb6f4c6a2177
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="select-localvariable-transact-sql"></a>Sélectionnez @local_variable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Définit une variable locale à la valeur d’une expression.  
  
 Pour affecter les variables, nous vous recommandons d’utiliser [définir @local_variable ](../../t-sql/language-elements/set-local-variable-transact-sql.md) au lieu de SELECT @*local_variable*.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SELECT { @local_variable { = | += | -= | *= | /= | %= | &= | ^= | |= } expression } 
    [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
@*local_variable*  
 Variable déclarée à laquelle doit être assignée une valeur.  
  
{= | += | -= | \*= | /= | %= | &= | ^= | |= }   
Assignez la valeur située à droite à la variable située à gauche.  
  
Opérateur d'assignation composé :  
  |operator |action |   
  |-----|-----|  
  | = | Affecte l’expression qui suit, à la variable. |  
  | += | Ajouter et attribuer |   
  | -= | Soustraire et attribuer |  
  | \*= | Multiplier et attribuer |  
  | /= | Diviser et attribuer |  
  | %= | Modulo et attribuer |  
  | &= | AND au niveau du bit et attribuer |  
  | ^= | Opérations de bits XOR et attribuer |  
  | \|= | OR au niveau du bit et attribuer |  
  
 *expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md). Cela comprend une sous-requête scalaire.  
  
## <a name="remarks"></a>Notes  
 Sélectionnez @*local_variable* est généralement utilisé pour retourner une valeur unique dans la variable. Toutefois, lorsque *expression* est le nom d’une colonne, elle peut retourner plusieurs valeurs. Si l'instruction SELECT retourne plusieurs valeurs, la dernière valeur retournée est affectée à la variable.  
  
 Si l'instruction SELECT ne retourne aucune ligne, la variable conserve sa valeur actuelle. Si *expression* est une sous-requête scalaire qui ne retourne aucune valeur, la variable n’est définie sur NULL.  
  
 Une instruction SELECT peut initialiser plusieurs variables locales.  
  
> [!NOTE]  
>  Une instruction SELECT contenant une affectation de variable ne peut pas être utilisée pour effectuer également des opérations d'extraction habituelles dans les jeux de résultats.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-use-select-localvariable-to-return-a-single-value"></a>A. Utilisation de SELECT @local_variable pour retourner une valeur unique  
 Dans l'exemple suivant, la variable `@var1` reçoit la valeur `Generic Name`. La requête sur la table `Store` ne retourne aucune ligne car la valeur spécifiée pour `CustomerID` n'existe pas dans la table. La variable conserve la valeur `Generic Name`.  
  
```sql  
-- Uses AdventureWorks    
  
DECLARE @var1 varchar(30);         
SELECT @var1 = 'Generic Name';         
SELECT @var1 = Name         
FROM Sales.Store         
WHERE CustomerID = 1000 ;        
SELECT @var1 AS 'Company Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 Company Name  
 ------------------------------  
 Generic Name  
 ```  
  
### <a name="b-use-select-localvariable-to-return-null"></a>B. Utilisation de SELECT @local_variable pour retourner une valeur null  
 Dans l'exemple suivant, une sous-requête est utilisée pour affecter une valeur à `@var1`. Comme la valeur demandée pour `CustomerID` n'existe pas, la sous-requête ne retourne pas de valeur et la variable se voit affecter la valeur `NULL`.  
  
```sql  
-- Uses AdventureWorks  
  
DECLARE @var1 varchar(30)   
SELECT @var1 = 'Generic Name'   
SELECT @var1 = (SELECT Name   
FROM Sales.Store   
WHERE CustomerID = 1000)   
SELECT @var1 AS 'Company Name' ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Company Name  
----------------------------  
NULL  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Compound, opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  
