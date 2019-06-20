---
title: Transactions ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], about transactions
- transactions [ODBC]
ms.assetid: b4ca861a-c164-4e87-8672-d5de15e3823c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6ce5decd2744c0ce9d753e355321a40d00fd620
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305813"
---
# <a name="transactions-odbc"></a>Transactions dans ODBC
Un *transaction* est une unité de travail qui s’effectue comme une seule opération atomique ; autrement dit, l’opération réussit ou échoue dans sa globalité. Par exemple, considérez le transfert d’argent d’un compte bancaire vers un autre. Cela implique deux étapes : le retrait de l’argent à partir du premier compte et il dépôt dans la seconde. Il est important que les deux étapes réussissent ; Il n’est pas acceptable pour une seule étape réussisse et l’autre échec. Une base de données qui prend en charge des transactions est en mesure de garantir cela.  
  
 Les transactions peuvent être effectuées par être *validée* ou en cours *restaurée*. Lorsqu’une transaction est validée, les modifications apportées dans la mesure transaction deviennent permanentes. Lorsqu’une transaction est restaurée, les lignes affectées sont retournés à l’état de qu'origine avant le début de la transaction. Pour étendre l’exemple de transfert de compte, une application exécute une instruction SQL pour le premier compte de débit et une instruction SQL différentes pour le deuxième compte de crédit. Si les deux instructions réussissent, l’application valide ensuite la transaction. Mais si l’instruction échoue pour une raison quelconque, l’application restaure la transaction. Dans les deux cas, l’application garantit un état cohérent à la fin de la transaction.  
  
 Une seule transaction peut englober plusieurs opérations de base de données qui se produisent à des moments différents. Si d’autres transactions avaient accès complet pour les résultats intermédiaires, les transactions peuvent interférer avec l’autre. Par exemple, supposons qu’une seule transaction insère une ligne, une deuxième transaction lit cette ligne et la première transaction est restaurée. La deuxième transaction maintenant a des données pour une ligne qui n’existe pas.  
  
 Pour résoudre ce problème, il existe divers schémas d’isoler les transactions entre eux. *Isolation des transactions* est généralement implémentée par le verrouillage de lignes, ce qui empêche les autres transactions à partir de l’aide de la même ligne en même temps. Dans certaines bases de données, le verrouillage d’une ligne peut verrouiller également les autres lignes.  
  
 Accrue des transactions isolation s’accompagne de réduction *concurrence,* ou la possibilité de deux transactions utilisent les mêmes données en même temps. Pour plus d’informations, consultez [définissant le niveau d’Isolation de Transaction](../../../odbc/reference/develop-app/setting-the-transaction-isolation-level.md).  
  
 Cette section contient les rubriques suivantes.  
  
-   [Transactions dans ODBC](../../../odbc/reference/develop-app/transactions-in-odbc-odbc.md)  
  
-   [Isolation des transactions](../../../odbc/reference/develop-app/transaction-isolation.md)  
  
-   [Contrôle de l’accès concurrentiel](../../../odbc/reference/develop-app/concurrency-control.md)
