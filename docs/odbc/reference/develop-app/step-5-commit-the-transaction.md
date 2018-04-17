---
title: 'Étape 5 : Valider la Transaction | Documents Microsoft'
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
ms.topic: article
helpviewer_keywords:
- application process [ODBC], committing transactions
- committing transactions [ODBC]
- transaction commit [ODBC]
ms.assetid: 311685e2-f7b5-4ddc-8020-59380cd2f035
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6102699cfae11fa94ee434ec0b3364f0f83dce17
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="step-5-commit-the-transaction"></a>Étape 5 : Valider la Transaction
L’étape suivante consiste à valider la transaction, comme indiqué dans l’illustration suivante.  
  
 ![Montre comment valider une transaction](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 La cinquième étape consiste à appeler **SQLEndTran** pour valider ou restaurer la transaction. L’application exécute cette étape uniquement si elle la valeur du mode de validation de transaction validation manuelle ; Si le mode de validation de transaction est validation automatique, qui est la valeur par défaut, la transaction est automatiquement validée lorsque l’instruction est exécutée. Pour plus d’informations, consultez [Transactions](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Pour exécuter une instruction dans une nouvelle transaction, l’application retourne à l’étape 3. Pour vous déconnecter de la source de données, l’application passe à l’étape 6.
