---
title: DATETIMEOFFSETFROMPARTS (Transact-SQL) | Documents Microsoft
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
- DATETIMEOFFSETFROMPARTS_TSQL
- DATETIMEOFFSETFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEOFFSETFROMPARTS function
ms.assetid: 463da1f4-b4b6-45a3-9a95-ea1f99575542
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 665607c3b6ea9411d90137fba416d96d3d46a4c1
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="datetimeoffsetfromparts-transact-sql"></a>DATETIMEOFFSETFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Retourne un **datetimeoffset** valeur pour la date et heure spécifiées et avec la précision et le décalage spécifiés.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATETIMEOFFSETFROMPARTS ( year, month, day, hour, minute, seconds, fractions, hour_offset, minute_offset, precision )  
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
  
*minute*  
Expression entière spécifiant des minutes.
  
*secondes*  
Expression entière spécifiant des secondes.
  
*fractions*  
Expression entière spécifiant des fractions.
  
*hour_offset*  
Expression entière spécifiant la partie heure du décalage de fuseau horaire.
  
*minute_offset*  
Expression entière spécifiant la partie minute du décalage de fuseau horaire.
  
*precision*  
Littéral entier spécifiant la précision de la **datetimeoffset** valeur à retourner.
  
## <a name="return-types"></a>Types de retour
**DateTimeOffset (** *précision* **)**
  
## <a name="remarks"></a>Notes  
**DATETIMEOFFSETFROMPARTS** retourne complètement initialisée **datetimeoffset** type de données. Les arguments de décalage sont utilisés pour représenter le décalage de fuseau horaire. Si les arguments de décalage sont omis, il est supposé que le décalage de fuseau horaire est 0h00, autrement dit il n'y a aucun décalage de fuseau horaire. Si les arguments de décalage sont spécifiés, les deux arguments doivent être présents et tous deux doivent être positifs ou négatifs. Si *minute_offset* est spécifié sans *hour_offset*, une erreur est générée. Si d'autres arguments ne sont pas valides, une erreur est générée. Si les arguments obligatoires sont null, une valeur null est retournée. Toutefois, si le *précision* argument est null, une erreur est générée.
  
Le *fractions* argument varie selon le *précision* argument. Par exemple, si *précision* est 7, chaque fraction représente 100 nanosecondes ; si *précision* est 3, alors chaque fraction représente une milliseconde. Si la valeur de *précision* est zéro, la valeur de *fractions* doit également être égal à zéro ; sinon, une erreur est générée.
  
Cette fonction peut être exécutée à distance sur des serveurs [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et versions ultérieures. Elle ne peut pas être exécutée à distance sur des serveurs dont la version est antérieure à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Exemples  
  
### <a name="a-simple-example-without-fractions-of-a-second"></a>A. Exemple simple sans fractions de seconde  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2010, 12, 31, 14, 23, 23, 0, 12, 0, 7 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------------------------  
2010-12-07 00:00:00.0000000 +00:00  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. Exemple avec fractions de seconde  
L’exemple suivant illustre l’utilisation de la *fractions* et *précision* paramètres :
1.   Lorsque *fractions* a la valeur 5 et *précision* a la valeur 1, puis la valeur de *fractions* représente 5 à 10 de seconde.  
1.   Lorsque *fractions* a la valeur 50 et *précision* a la valeur 2, puis la valeur de *fractions* représente 50/100 de seconde.  
1.   Lorsque *fractions* a la valeur 500 et *précision* a la valeur 3, puis la valeur de *fractions* représente 500/1000 de seconde.  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 5, 12, 30, 1 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 50, 12, 30, 2 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 500, 12, 30, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------------------  
2011-08-15 14:30:00.5 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.50 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.500 +12:30  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
[FUSEAU horaire &AMP;#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  



