---
title: Validation et restauration des transactions | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299109"
---
# <a name="committing-and-rolling-back-transactions"></a>Validation et annulation des transactions
Pour valider ou restaurer une transaction en mode de validation manuelle, une application appelle **SQLEndTran**. Les pilotes pour les SGBD qui prennent en charge les transactions implémentent généralement cette fonction en exécutant une instruction **Commit** ou **Rollback** . Le gestionnaire de pilotes n’appelle pas **SQLEndTran** lorsque la connexion est en mode de validation automatique. elle retourne simplement SQL_SUCCESS, même si l’application tente de restaurer la transaction. Étant donné que les pilotes pour les SGBD qui ne prennent pas en charge les transactions sont toujours en mode de validation automatique, ils peuvent implémenter **SQLEndTran** pour retourner des SQL_SUCCESS sans effectuer aucune action ou ne pas implémenter le tout.  
  
> [!NOTE]  
>  Les applications ne doivent pas valider ou restaurer des transactions en exécutant des instructions **Commit** ou **Rollback** avec **SQLExecute** ou **SQLExecDirect**. Les effets de cette action ne sont pas définis. Les problèmes possibles incluent le pilote qui ne sait plus quand une transaction est active et ces instructions échouent sur des sources de données qui ne prennent pas en charge les transactions. Ces applications doivent appeler **SQLEndTran** à la place.  
  
 Si une application transmet le descripteur d’environnement à **SQLEndTran** mais ne transmet pas de handle de connexion, le gestionnaire de pilotes appelle de manière conceptuelle **SQLEndTran** avec le descripteur d’environnement pour chaque pilote qui a une ou plusieurs connexions actives dans l’environnement. Le pilote valide ensuite les transactions sur chaque connexion dans l’environnement. Toutefois, il est important de se rendre compte que ni le pilote ni le gestionnaire de pilotes n’effectuent une validation en deux phases sur les connexions dans l’environnement. Il s’agit simplement d’une commodité de programmation pour appeler simultanément **SQLEndTran** pour toutes les connexions dans l’environnement.  
  
 (Une *validation en deux phases* est généralement utilisée pour valider des transactions qui sont réparties sur plusieurs sources de données. Dans sa première phase, les sources de données sont interrogées pour déterminer si elles peuvent valider leur partie de la transaction. Dans la deuxième phase, la transaction est effectivement validée sur toutes les sources de données. Si des sources de données répondent à la première phase qu’elles ne peuvent pas valider la transaction, la deuxième phase n’a pas lieu.)
