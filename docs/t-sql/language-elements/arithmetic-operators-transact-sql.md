---
title: Opérateurs arithmétiques (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], arithmetic
- arithmetic operators
- math operations [Transact-SQL]
ms.assetid: a41b92a5-1061-4e4d-bb3b-a180b73c88fa
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 94d617f0da60b73ecfc7a0dcdd4530a3a36f3ca7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67927369"
---
# <a name="arithmetic-operators-transact-sql"></a>Opérateurs arithmétiques (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Les opérateurs arithmétiques exécutent des opérations mathématiques sur deux expressions d’un ou plusieurs types de données, à partir de la catégorie de type de données numérique. Pour plus d’informations sur les catégories de types de données, consultez [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Opérateur|Signification|  
|--------------|-------------|  
|[+ (Ajout)](../../t-sql/language-elements/add-transact-sql.md)|Addition|  
|[- (Soustraction)](../../t-sql/language-elements/subtract-transact-sql.md)|Soustraction|  
|[* (Multiplication)](../../t-sql/language-elements/multiply-transact-sql.md)|Multiplication|  
|[/ (Diviser)](../../t-sql/language-elements/divide-transact-sql.md)|Division|  
|[% (Modulo)](../../t-sql/language-elements/modulo-transact-sql.md)|Retourne le reste entier d'une division. Par exemple, 12 % 5 = 2 parce que le reste de 12 divisé par 5 est 2.|  
  
Les opérateurs plus (+) et moins (-) peuvent également s’utiliser pour des opérations arithmétiques sur des valeurs **datetime** et **smalldatetime**.  
  
Pour plus d’informations sur la précision et l’échelle du résultat d’une opération arithmétique, voir [Précision, échelle et longueur &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Fonctions mathématiques &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
[Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
