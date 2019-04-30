---
title: Validation et annulation des Transactions | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 194a90482946814995ca1963f7c8fc4bce48d223
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63126362"
---
# <a name="committing-and-rolling-back-transactions"></a>Validation et annulation des transactions
Pour valider ou restaurer une transaction en mode de validation manuelle, une application appelle **SQLEndTran**. Pilotes pour les SGBD qui prennent en charge les transactions généralement implémentent cette fonction en exécutant un **valider** ou **ROLLBACK** instruction. Le Gestionnaire de pilotes n’appelle pas **SQLEndTran** lorsque la connexion est en mode de validation automatique ; elle retourne simplement SQL_SUCCESS, même si l’application tente de restaurer la transaction. Étant donné que les pilotes pour les SGBD qui ne prennent pas en charge les transactions sont toujours en mode de validation automatique, ils peuvent implémenter **SQLEndTran** retourne SQL_SUCCESS sans rien faire ou l’implémente pas du tout.  
  
> [!NOTE]  
>  Les applications ne doivent pas valider ou restaurer les transactions en exécutant **validation** ou **ROLLBACK** instructions avec **SQLExecute** ou **SQLExecDirect**. Les effets de cette opération ne sont pas définis. Problèmes possibles incluent le pilote n’est plus savoir quand une transaction est active et ces instructions échouent sur les sources de données qui ne prennent pas en charge les transactions. Ces applications doivent appeler **SQLEndTran** à la place.  
  
 Si une application passe le handle d’environnement à **SQLEndTran** mais ne passez pas un handle de connexion, le Gestionnaire de pilotes sur le plan conceptuel appelle **SQLEndTran** avec le handle d’environnement pour chaque pilote qui a un ou plusieurs connexions actives dans l’environnement. Le pilote puis valide les transactions sur chaque connexion dans l’environnement. Toutefois, il est important de savoir que le pilote, ni le Gestionnaire de pilotes effectue une validation en deux phases sur les connexions dans l’environnement ; Il s’agit simplement une facilité de programmation d’appeler simultanément **SQLEndTran** pour toutes les connexions dans l’environnement.  
  
 (Un *validation en deux phases* est généralement utilisée pour valider des transactions qui sont réparties sur plusieurs sources de données. Dans sa première phase, les sources de données sont interrogés que s’ils peuvent valider leur partie de la transaction. Dans la deuxième phase, la transaction est effectivement validée sur toutes les sources de données. Si toutes les sources de données de réponse dans la première phase qu’ils ne peuvent pas valider la transaction, la deuxième phase ne se produit pas.)
