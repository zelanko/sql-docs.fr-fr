---
title: Validation et la restauration des Transactions en | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- transactions [ODBC], committing
ms.assetid: 800f2c1a-6f79-4ed1-830b-aa1a62ff5165
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 534c6181a1634eb4963bc4f448939f335d821e5f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="committing-and-rolling-back-transactions"></a>Validation et annulation de Transactions
Pour valider ou restaurer une transaction en mode de validation manuelle, une application appelle **SQLEndTran**. Pilotes pour les SGBD qui prennent en charge les transactions généralement implémentent cette fonction en exécutant un **valider** ou **restauration** instruction. Le Gestionnaire de pilotes n’appelle pas **SQLEndTran** lorsque la connexion est en mode de validation automatique ; elle retourne simplement SQL_SUCCESS, même si l’application tente de restaurer la transaction. Étant donné que les pilotes pour les SGBD qui ne prennent pas en charge les transactions sont toujours en mode de validation automatique, ils peuvent implémenter **SQLEndTran** retourne SQL_SUCCESS sans rien faire ou l’implémente pas du tout.  
  
> [!NOTE]  
>  Applications ne doivent pas valider ou annuler les transactions en exécutant **validation** ou **restauration** instructions avec **SQLExecute** ou **SQLExecDirect**. Les effets de cette opération ne sont pas définis. Les problèmes possibles sont le pilote n’est plus savoir quand une transaction est active et ces instructions échouent sur les sources de données qui ne prennent pas en charge les transactions. Ces applications doivent appeler **SQLEndTran** à la place.  
  
 Si une application passe le handle d’environnement pour **SQLEndTran** mais ne pas passe un handle de connexion, le Gestionnaire de pilotes appelle conceptuellement **SQLEndTran** avec le handle d’environnement pour chaque pilote qui a une ou plusieurs connexions actives dans l’environnement. Le pilote puis valide les transactions sur chaque connexion dans l’environnement. Toutefois, il est important de savoir que le pilote, ni le Gestionnaire de pilotes effectue une validation en deux phases sur les connexions dans l’environnement. Il s’agit simplement une facilité de programmation d’appeler simultanément **SQLEndTran** pour toutes les connexions dans l’environnement.  
  
 (A *validation en deux phases* est généralement utilisé pour valider des transactions qui sont réparties sur plusieurs sources de données. Dans la première phase, les sources de données sont interrogées à s’ils peuvent valider au cours de la transaction. Dans la deuxième phase, la transaction est effectivement validée sur toutes les sources de données. Si toutes les sources de données de réponse dans la première phase qu’ils ne peuvent pas valider la transaction, la deuxième phase n’a pas lieu.)
