---
title: Jointures externes | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequences [ODBC]
- escape sequences [ODBC], outer join
ms.assetid: be1a0203-5da9-4871-9566-4bd3fbc0895c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23f7489b9ca0e5d03b4fa132ef6ccd63bede876d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="outer-joins"></a>Jointures externes
ODBC prend en charge le SQL-92 de gauche, syntaxe de jointure externe complète et à droite. Est de la séquence d’échappement pour les jointures externes  
  
 **{JO** *externe-jointure ***}**  
  
 où *jointure externe* est  
  
 *référence de table* {**gauche &#124; droite &#124; complète} jointure externe** {*référence de table* &#124; *jointure externe*} **ON**  *condition de recherche*  
  
 *référence de table* spécifie un nom de table, et *condition de recherche* spécifie la condition de jointure entre la *références de table*.  
  
 Une requête de jointure externe doit apparaître après les **FROM** (mot clé) et avant le **où** clause (le cas échéant). Pour plus d’informations sur la syntaxe complète, consultez [séquence d’échappement de jointure externe](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) dans l’annexe c : SQL grammaire.  
  
 Par exemple, les instructions SQL suivantes créent le même jeu de résultats qui répertorie tous les clients et indique qui a des commandes en cours. La première instruction utilise la syntaxe de la séquence d’échappement. La deuxième instruction utilise la syntaxe native pour Oracle et n’est pas interopérable.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Pour déterminer les types de jointures externes utilisant une source de données et le pilote prend en charge, une application appelle **SQLGetInfo** avec la SQL_OJ_CAPABILITIES indicateur. Les types de jointures externes peuvent être pris en charge sont gauche, droite, complète ou des jointures externes ; imbriquées jointures externes dans laquelle la colonne des noms dans le **ON** clause n’ont pas le même ordre que leurs noms de table correspondante dans le **OUTER JOIN** clause ; les jointures internes conjointement avec les jointures externes et des jointures externes à l’aide de n’importe quel opérateur de comparaison ODBC. Si le type d’informations SQL_OJ_CAPABILITIES renvoie la valeur 0, aucune clause de jointure externe n’est prise en charge.
