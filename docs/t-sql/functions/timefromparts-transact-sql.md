---
title: TIMEFROMPARTS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TIMEFROMPARTS_TSQL
- TIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- TIMEFROMPARTS function
ms.assetid: 786c65a1-2b3f-4e4b-82b6-4940d62f3801
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 43e6b8f2d234e0b2dd11299c56f1c6b9d0e06518
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="timefromparts-transact-sql"></a>TIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Retourne un **temps** valeur pour l’heure spécifiée et avec la précision spécifiée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
TIMEFROMPARTS ( hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>Arguments  
 *heure*  
 Expression entière spécifiant des heures.  
  
 *minute*  
 Expression entière spécifiant des minutes.  
  
 *secondes*  
 Expression entière spécifiant des secondes.  
  
 *fractions*  
 Expression entière spécifiant des fractions.  
  
 *precision*  
 Littéral entier spécifiant la précision de la **temps** valeur à retourner.  
  
## <a name="return-types"></a>Types de retour  
 **heure (** *précision* **)**  
  
## <a name="remarks"></a>Notes  
 TIMEROMPARTS retourne une valeur temporelle complètement initialisée. Si les arguments ne sont pas valides, une erreur est générée. Si l'un des paramètres est NULL, la valeur NULL est retournée. Toutefois, si le *précision* argument est null, une erreur est générée.  
  
 Le *fractions* argument varie selon le *précision* argument. Par exemple, si *précision* est 7, chaque fraction représente 100 nanosecondes ; si *précision* est 3, alors chaque fraction représente une milliseconde. Si la valeur de *précision* est zéro, la valeur de *fractions* doit également être égal à zéro ; sinon, une erreur est générée.  
  
 Cette fonction peut être exécutée à distance sur les serveurs [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures. Elle ne peut pas être exécutée à distance sur des serveurs exécutant une version antérieure à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Exemple simple sans fractions de seconde  
  
```  
SELECT TIMEFROMPARTS ( 23, 59, 59, 0, 0 ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------------------  
23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. Exemple avec fractions de seconde  
 L’exemple suivant illustre l’utilisation de la *fractions* et *précision* paramètres :  
  
1.  Lorsque *fractions* a la valeur 5 et *précision* a la valeur 1, puis la valeur de *fractions* représente 5 à 10 de seconde.  
  
2.  Lorsque *fractions* a la valeur 50 et *précision* a la valeur 2, puis la valeur de *fractions* représente 50/100 de seconde.  
  
3.  Lorsque *fractions* a la valeur 500 et *précision* a la valeur 3, puis la valeur de *fractions* représente 500/1000 de seconde.  
  
```tsql  
SELECT TIMEFROMPARTS ( 14, 23, 44, 5, 1 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 50, 2 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 500, 3 );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------  
14:23:44.5  
  
(1 row(s) affected)  
  
----------------  
14:23:44.50  
  
(1 row(s) affected)  
  
----------------  
14:23:44.500  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example-without-fractions-of-a-second"></a>C. Exemple simple sans fractions de seconde  
  
```  
SELECT TIMEFROMPARTS ( 23, 59, 59, 0, 0 ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------------------  
23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="d-example-with-fractions-of-a-second"></a>D. Exemple avec fractions de seconde  
 L’exemple suivant illustre l’utilisation de la *fractions* et *précision* paramètres :  
  
1.  Lorsque *fractions* a la valeur 5 et *précision* a la valeur 1, puis la valeur de *fractions* représente 5 à 10 de seconde.  
  
2.  Lorsque *fractions* a la valeur 50 et *précision* a la valeur 2, puis la valeur de *fractions* représente 50/100 de seconde.  
  
3.  Lorsque *fractions* a la valeur 500 et *précision* a la valeur 3, puis la valeur de *fractions* représente 500/1000 de seconde.  
  
```tsql  
SELECT TIMEFROMPARTS ( 14, 23, 44, 5, 1 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 50, 2 );  
SELECT TIMEFROMPARTS ( 14, 23, 44, 500, 3 );  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------  
14:23:44.5  
  
(1 row(s) affected)  
  
----------------  
14:23:44.50  
  
(1 row(s) affected)  
  
----------------  
14:23:44.500  
  
(1 row(s) affected)  
```  
  
  


