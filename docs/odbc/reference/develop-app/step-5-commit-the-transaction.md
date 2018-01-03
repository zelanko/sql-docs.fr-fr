---
title: "Étape 5 : Valider la Transaction | Documents Microsoft"
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
- application process [ODBC], committing transactions
- committing transactions [ODBC]
- transaction commit [ODBC]
ms.assetid: 311685e2-f7b5-4ddc-8020-59380cd2f035
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8494c26badd04a1c009f8f23c60559ed695ea3d2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="step-5-commit-the-transaction"></a>Étape 5 : Valider la Transaction
L’étape suivante consiste à valider la transaction, comme indiqué dans l’illustration suivante.  
  
 ![Montre comment valider une transaction](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 La cinquième étape consiste à appeler **SQLEndTran** pour valider ou restaurer la transaction. L’application exécute cette étape uniquement si elle la valeur du mode de validation de transaction validation manuelle ; Si le mode de validation de transaction est validation automatique, qui est la valeur par défaut, la transaction est automatiquement validée lorsque l’instruction est exécutée. Pour plus d’informations, consultez [Transactions](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Pour exécuter une instruction dans une nouvelle transaction, l’application retourne à l’étape 3. Pour vous déconnecter de la source de données, l’application passe à l’étape 6.
