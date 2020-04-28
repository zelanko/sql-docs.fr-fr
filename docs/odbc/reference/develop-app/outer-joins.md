---
title: Jointures externes | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81282443"
---
# <a name="outer-joins"></a>Jointures externes
ODBC prend en charge la syntaxe de jointure externe gauche, droite et complète SQL-92. La séquence d’échappement pour les jointures externes est  
  
 **{JO** _Outer-jointure_**}**  
  
 où la *jointure externe* est  
  
 *table-Reference* {**LEFT &#124; Right &#124; complet} jointure externe** {*référence de table* &#124; *externe-jointure*} **sur** la _condition de recherche_  
  
 *table-Reference* spécifie un nom de table, et *condition de recherche* spécifie la condition de jointure entre les *références de table*.  
  
 Une demande de jointure externe doit apparaître après le mot clé **from** et avant la clause **Where** (le cas échéant). Pour obtenir des informations complètes sur la syntaxe, consultez [séquence d’échappement de jointure externe](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) dans l’annexe C : grammaire SQL.  
  
 Par exemple, les instructions SQL suivantes créent le même jeu de résultats qui répertorie tous les clients et présente les commandes ouvertes. La première instruction utilise la syntaxe de séquence d’échappement. La deuxième instruction utilise la syntaxe native pour Oracle et n’est pas interopérable.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Pour déterminer les types de jointures externes pris en charge par une source de données et un pilote, une application appelle **SQLGetInfo** avec l’indicateur SQL_OJ_CAPABILITIES. Les types de jointures externes qui peuvent être prises en charge sont les jointures externes gauche, droite, complète ou imbriquée ; les jointures externes dans lesquelles les noms de colonnes dans la clause on n’ont pas le même ordre que leurs noms de tables respectifs dans la clause **de** **jointure externe** ; jointures internes conjointement avec les jointures externes ; et les jointures externes à l’aide d’un opérateur de comparaison ODBC. Si le type d’informations SQL_OJ_CAPABILITIES retourne 0, aucune clause de jointure externe n’est prise en charge.
