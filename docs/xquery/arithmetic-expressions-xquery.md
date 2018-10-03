---
title: Les Expressions arithmétiques (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- expressions [XQuery], arithmetic
- arithmetic expressions
ms.assetid: 90d675bf-56da-459a-9771-8cd13920a9fc
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3d970209b71a842aa1c78b2f7dd0db980e0ce73e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642647"
---
# <a name="arithmetic-expressions-xquery"></a>Expressions arithmétiques (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Tous les opérateurs arithmétiques sont pris en charge, à l’exception de **idiv**. Les exemples suivants illustrent l'utilisation de base des opérateurs arithmétiques :  
  
```  
DECLARE @x xml  
SET @x=''  
SELECT @x.query('2 div 2')  
SELECT @x.query('2 * 2')  
```  
  
 Étant donné que **idiv** est ne pas pris en charge, une solution consiste à utiliser le **xs:integer()** constructeur :  
  
```  
DECLARE @x xml  
SET @x=''  
-- Following will not work  
-- SELECT @x.query('2 idiv 2')  
-- Workaround   
SELECT @x.query('xs:integer(2 div 3)')  
```  
  
 Le type issu d'un opérateur arithmétique est basé sur les types des valeurs d'entrée. Si les opérandes sont de types différents, l'un d'eux, voire les deux si nécessaire, est converti dans un type de base primitif courant en fonction de la hiérarchie des types. Pour plus d’informations sur la hiérarchie des types, consultez [règles de conversion de Type dans XQuery](../xquery/type-casting-rules-in-xquery.md).  
  
 La promotion du type numérique se produit si les deux opérations sont de types de base numériques différents. Par exemple, ajoutez un **xs : decimal** à un **xs : double** modifieriez tout d’abord la valeur décimale en double. L'ajout suivant aboutirait à une valeur double.  
  
 Valeurs atomiques non typées sont converties en type de base numérique de l’autre opérande, ou aux **xs : double** si l’autre opérande est également non typé.  
  
## <a name="implementation-limitations"></a>Limites de mise en œuvre  
 Les limitations suivantes s'appliquent :  
  
-   Arguments pour les opérateurs arithmétiques doivent être de type numérique ou **untypedAtomic**.  
  
-   Opérations sur **xs : Integer** valeurs génèrent une valeur de type **xs : decimal** au lieu de **xs : Integer**.  
  
  
