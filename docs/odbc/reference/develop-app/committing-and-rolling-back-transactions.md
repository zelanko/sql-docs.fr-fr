---
title: Engagement et retour en arrière transactions (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- transactions [ODBC], committing
ms.assetid: 800f2c1a-6f79-4ed1-830b-aa1a62ff5165
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c272d60242d31622452c4dcb0f6a16c4838768f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299109"
---
# <a name="committing-and-rolling-back-transactions"></a>Validation et annulation des transactions
Pour valider ou annuler une transaction en mode engagement manuel, une application appelle **SQLEndTran**. Les conducteurs de DBMS qui prennent en charge les transactions implémentent généralement cette fonction en exécutant une déclaration **COMMIT** ou **ROLLBACK.** Le gestionnaire de conducteur n’appelle pas **SQLEndTran** lorsque la connexion est en mode auto-commit; il renvoie simplement SQL_SUCCESS, même si l’application tente de annuler la transaction. Étant donné que les conducteurs de DBMS qui ne prennent pas en charge les transactions sont toujours en mode auto-commit, ils peuvent soit implémenter **SQLEndTran** pour retourner SQL_SUCCESS sans rien faire ou ne pas le mettre en œuvre du tout.  
  
> [!NOTE]  
>  Les demandes ne doivent pas valider ou annuler les transactions en exécutant des déclarations **COMMIT** ou **ROLLBACK** avec **SQLExecute** ou **SQLExecDirect**. Les effets de ce fait sont indéfinis. Les problèmes possibles incluent que le conducteur ne sait plus quand une transaction est active et ces déclarations qui échouent contre les sources de données qui ne prennent pas en charge les transactions. Ces applications devraient appeler **SQLEndTran** à la place.  
  
 Si une application passe la poignée de l’environnement à **SQLEndTran** mais ne passe pas une poignée de connexion, le gestionnaire de conducteur appelle conceptuellement **SQLEndTran** avec la poignée d’environnement pour chaque conducteur qui a une ou plusieurs connexions actives dans l’environnement. Le conducteur engage ensuite les transactions sur chaque connexion dans l’environnement. Cependant, il est important de se rendre compte que ni le conducteur ni le gestionnaire de conducteur n’effectue un engagement en deux phases sur les connexions dans l’environnement; il s’agit simplement d’une commodité de programmation pour appeler simultanément **SQLEndTran** pour toutes les connexions dans l’environnement.  
  
 (Un *engagement en deux phases* est généralement utilisé pour valider des transactions réparties sur plusieurs sources de données. Dans sa première phase, les sources de données sont interrogées pour savoir si elles peuvent valider leur part de la transaction. Dans la deuxième phase, la transaction est en fait engagée sur toutes les sources de données. Si des sources de données répondent dans la première phase qu’elles ne peuvent pas commettre la transaction, la deuxième phase ne se produit pas.)
