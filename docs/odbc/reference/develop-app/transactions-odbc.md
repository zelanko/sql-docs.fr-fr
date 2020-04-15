---
title: Transactions ODBC (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a40c34b2abeb346c7a718994ba2484bfc728e2b1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297954"
---
# <a name="transactions-odbc"></a>Transactions dans ODBC
Une *transaction* est une unité de travail qui se fait comme une seule opération atomique; c’est-à-dire que l’opération réussit ou échoue dans son ensemble. Par exemple, envisagez de transférer de l’argent d’un compte bancaire à un autre. Cela implique deux étapes: retirer l’argent du premier compte et le déposer dans le second. Il est important que les deux étapes réussissent; il n’est pas acceptable qu’une étape réussisse et que l’autre échoue. Une base de données qui prend en charge les transactions est en mesure de garantir cela.  
  
 Les transactions peuvent être effectuées en étant *commis ou* en *étant annulées.* Lorsqu’une transaction est engagée, les modifications apportées à cette transaction sont permanentes. Lorsqu’une transaction est annulée, les lignes touchées sont retournées à l’état où elles se trouvaient avant le début de la transaction. Pour prolonger l’exemple de transfert de compte, une application exécute une déclaration SQL pour débiter le premier compte et un relevé SQL différent pour créditer le deuxième compte. Si les deux énoncés aboutissent, l’application engage alors la transaction. Mais si l’une ou l’autre déclaration échoue pour une raison quelconque, l’application annule la transaction. Dans les deux cas, la demande garantit un état cohérent à la fin de la transaction.  
  
 Une seule transaction peut englober plusieurs opérations de base de données qui se produisent à des moments différents. Si d’autres transactions avaient un accès complet aux résultats intermédiaires, les transactions pourraient interférer les unes avec les autres. Supposons, par exemple, qu’une transaction insère une ligne, qu’une deuxième transaction indique cette ligne et que la première transaction est annulée. La deuxième transaction a maintenant des données pour une rangée qui n’existe pas.  
  
 Pour résoudre ce problème, il existe divers schémas pour isoler les transactions les uns des autres. *L’isolement des transactions* est généralement mis en œuvre par des lignes de verrouillage, ce qui empêche plus d’une transaction d’utiliser la même ligne en même temps. Dans certaines bases de données, le verrouillage d’une rangée peut également verrouiller d’autres rangées.  
  
 Avec l’isolement accru des transactions vient la *concurrence réduite,* ou la capacité de deux transactions d’utiliser les mêmes données en même temps. Pour plus d’informations, voir [Définir le niveau d’isolement des transactions](../../../odbc/reference/develop-app/setting-the-transaction-isolation-level.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Transactions dans ODBC](../../../odbc/reference/develop-app/transactions-in-odbc-odbc.md)  
  
-   [Isolation des transactions](../../../odbc/reference/develop-app/transaction-isolation.md)  
  
-   [Contrôle de la concordance](../../../odbc/reference/develop-app/concurrency-control.md)
