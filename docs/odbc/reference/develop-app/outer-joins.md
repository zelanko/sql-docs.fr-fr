---
title: Joints extérieurs Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequences [ODBC]
- escape sequences [ODBC], outer join
ms.assetid: be1a0203-5da9-4871-9566-4bd3fbc0895c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 81988d34dca38d5c041ff9f87e9674d7c97d76cc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282443"
---
# <a name="outer-joins"></a>Jointures externes
ODBC prend en charge la SQL-92 à gauche, à droite et la syntaxe extérieure complète. La séquence d’évacuation des jointures extérieures est  
  
 **oj** _à l’extérieur-join_**}**  
  
 où *l’intérieur extérieur* est  
  
 *référence de table* -**LEFT &#124; RIGHT &#124; FULL' OUTER JOIN** -*table-référence* *&#124;'extérieur-join*' **ON** _search-condition_  
  
 *table-référence* spécifie un nom de table, et *l’état de recherche* spécifie l’état de jointure entre les *références de table.*  
  
 Une demande de jointure externe doit apparaître après le mot clé **FROM** et avant la clause **WHERE** (si elle existe). Pour obtenir des informations complètes sur la syntaxe, voir [Outer Join Escape Sequence](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) à l’annexe C: SQL Grammar.  
  
 Par exemple, les relevés SQL suivants créent le même ensemble de résultats qui répertorie tous les clients et affiche qui a des commandes ouvertes. La première déclaration utilise la syntaxe de séquence d’évacuation. La deuxième déclaration utilise la syntaxe indigène pour Oracle et n’est pas interopérable.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Pour déterminer les types de jointures extérieures qu’une source de données et le soutien du conducteur, une application appelle **SQLGetInfo** avec le drapeau SQL_OJ_CAPABILITIES. Les types de jointures extérieures qui pourraient être pris en charge sont les jointures extérieures gauches, droites, pleines ou imbriquées; jointures extérieures dans lesquelles les noms de colonnes de la clause **ON** n’ont pas le même ordre que leurs noms de table respectifs dans la clause **OUTER JOIN;** joint intérieur en conjonction avec les jointures extérieures ; et les jointures extérieures à l’aide de tout opérateur de comparaison ODBC. Si le type d’information SQL_OJ_CAPABILITIES renvoie 0, aucune clause de jointure extérieure n’est prise en charge.
