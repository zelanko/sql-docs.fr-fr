---
title: "Opérateurs de comparaison (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], testing
- operators [Transact-SQL], comparison
- testing expressions
- Boolean data type
- Boolean expressions
- comparing expressions
- comparison operators [SQL Server]
ms.assetid: b0cc68ef-3029-484c-a917-0c15dcbc230d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: cd8dcf23064d6caae62d10065c9aa3731823e99b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="comparison-operators-transact-sql"></a>Opérateurs de comparaison (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Les opérateurs de comparaison testent si deux expressions sont identiques. Opérateurs de comparaison peuvent être utilisés sur toutes les expressions, à l’exception des expressions de la **texte**, **ntext**, ou **image** des types de données. Le tableau suivant répertorie les opérateurs de comparaison [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
|Opérateur|Signification|  
|--------------|-------------|  
|[= (Égal à)](../../t-sql/language-elements/equals-transact-sql.md)|Égal à|  
|[> (Supérieur à)](../../t-sql/language-elements/greater-than-transact-sql.md)|Supérieur à|  
|[< (Inférieur à)](../../t-sql/language-elements/less-than-transact-sql.md)|Inférieur à|  
|[>= (Supérieur ou égal à)](../../t-sql/language-elements/greater-than-or-equal-to-transact-sql.md)|Supérieur ou égal à|  
|[<= (Inférieur ou égal à)](../../t-sql/language-elements/less-than-or-equal-to-transact-sql.md)|Inférieur ou égal à|  
|[<> (Différent de)](../../t-sql/language-elements/not-equal-to-transact-sql-traditional.md)|Différent de|  
|[\!= (Différent de)](../../t-sql/language-elements/not-equal-to-transact-sql-exclamation.md)|Différent de (hors norme ISO)|  
|[\!< (Non inférieur à)](../../t-sql/language-elements/not-less-than-transact-sql.md)|Non inférieur à (hors norme ISO)|  
|[\!> (Non supérieur à)](../../t-sql/language-elements/not-greater-than-transact-sql.md)|Non supérieur à (hors norme ISO)|  
  
## <a name="boolean-data-type"></a>Type de données Boolean  
 Le résultat d’un opérateur de comparaison a la **booléenne** type de données. et peut prendre trois valeurs : TRUE, FALSE et UNKNOWN. Les expressions qui retournent un **booléenne** type de données sont dites expressions booléennes.  
  
 Contrairement à d’autres [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des types de données, un **booléenne** type de données ne peut pas être spécifié comme type de données d’une variable ou une colonne de table et ne peut pas être retourné dans un jeu de résultats.  
  
 Lorsque SET ANSI_NULLS est activé (ON), un opérateur ayant une ou deux expressions de valeur NULL retourne UNKNOWN. Si SET ANSI_NULLS est désactivé (OFF), les mêmes règles s'appliquent, mais il reste à noter qu'un opérateur d'égalité (=) retourne la valeur TRUE si les deux expressions ont pour valeur NULL. Par exemple, NULL = NULL retourne TRUE si SET ANSI_NULLS est désactivé (OFF).  
  
 Expressions avec **booléenne** des types de données sont utilisées dans la clause WHERE pour filtrer les lignes qui répondent aux critères de recherche et dans les instructions de langage de contrôle de flux telles que IF et WHILE, par exemple :  
  
```  
-- Uses AdventureWorks  
  
DECLARE @MyProduct int;  
SET @MyProduct = 750;  
IF (@MyProduct <> 0)  
   SELECT ProductID, Name, ProductNumber  
   FROM Production.Product  
   WHERE ProductID = @MyProduct;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
