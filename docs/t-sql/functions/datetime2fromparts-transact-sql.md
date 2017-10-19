---
title: DATETIME2FROMPARTS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATETIME2FROMPARTS_TSQL
- DATETIME2FROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIME2FROMPARTS function
ms.assetid: 632b757d-d2d1-43a5-b870-792a779ae204
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: f54170fc9f17ff7eb69f5de8cfdf865fd31bd4d8
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="datetime2fromparts-transact-sql"></a>DATETIME2FROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Retourne un **datetime2** valeur pour la date et heure spécifiées et avec la précision spécifiée.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATETIME2FROMPARTS ( year, month, day, hour, minute, seconds, fractions, precision )  
```  
  
## <a name="arguments"></a>Arguments  
*année*  
Expression entière spécifiant une année.
  
*mois*  
Expression entière spécifiant un mois.
  
*jour*  
Expression entière spécifiant un jour.
  
 *heure*  
Expression entière spécifiant des heures.
  
*minute* expression entière spécifiant des minutes.
  
*secondes*  
Expression entière spécifiant des secondes.
  
*fractions*  
Expression entière spécifiant des fractions.
  
*precision*  
Littéral entier spécifiant la précision de la **datetime2** valeur à retourner.
  
## <a name="return-types"></a>Types de retour
**datetime2 (** *précision* **)**
  
## <a name="remarks"></a>Notes  
**DATETIME2FROMPARTS** retourne complètement initialisée **datetime2** valeur. Si les arguments ne sont pas valides, une erreur est générée. Si les arguments obligatoires sont NULL, la valeur NULL est retournée. Toutefois, si le *précision* argument est null, une erreur est générée.
  
Le *fractions* argument varie selon le *précision* argument. Par exemple, si *précision* est 7, chaque fraction représente 100 nanosecondes ; si *précision* est 3, alors chaque fraction représente une milliseconde. Si la valeur de *précision* est zéro, la valeur de *fractions* doit également être égal à zéro ; sinon, une erreur est générée.
  
Cette fonction peut être exécutée à distance sur des serveurs [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et versions ultérieures. Elle ne peut pas être exécutée à distance sur des serveurs dont la version est antérieure à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Exemples  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Exemple simple sans fractions de seconde  
  
```sql
SELECT DATETIME2FROMPARTS ( 2010, 12, 31, 23, 59, 59, 0, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. Exemple avec fractions de seconde  
L’exemple suivant illustre l’utilisation de la *fractions* et *précision* paramètres :
  
1.  Lorsque *fractions* a la valeur 5 et *précision* a la valeur 1, puis la valeur de *fractions* représente 5 à 10 de seconde.  
  
2.  Lorsque *fractions* a la valeur 50 et *précision* a la valeur 2, puis la valeur de *fractions* représente 50/100 de seconde.  
  
3.  Lorsque *fractions* a la valeur 500 et *précision* a la valeur 3, puis la valeur de *fractions* représente 500/1000 de seconde.  
  
```sql
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 5, 1 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 50, 2 );  
SELECT DATETIME2FROMPARTS ( 2011, 8, 15, 14, 23, 44, 500, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------  
2011-08-15 14:23:44.5  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.50  
  
(1 row(s) affected)  
  
----------------------  
2011-08-15 14:23:44.500  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[datetime2 &#40;Transact-SQL&#41;](../../t-sql/data-types/datetime2-transact-sql.md)
  
  


