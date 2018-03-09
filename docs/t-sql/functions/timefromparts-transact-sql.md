---
title: TIMEFROMPARTS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5e046e203e7ebd5243cdfc6f10948dfd353b2dd3
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="timefromparts-transact-sql"></a>TIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

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
  
```sql  
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
  

