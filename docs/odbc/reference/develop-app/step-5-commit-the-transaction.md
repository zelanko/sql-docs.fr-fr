---
title: 'Étape 5 : Engagez la transaction Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], committing transactions
- committing transactions [ODBC]
- transaction commit [ODBC]
ms.assetid: 311685e2-f7b5-4ddc-8020-59380cd2f035
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e348ce697e512f30db46d14535cf19bd6d530f61
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283349"
---
# <a name="step-5-commit-the-transaction"></a>Étape 5 : Valider la transaction
L’étape suivante consiste à valider la transaction, comme le montre l’illustration suivante.  
  
 ![Présente la validation d'une transaction](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 La cinquième étape consiste à appeler **SQLEndTran** pour engager ou annuler la transaction. L’application n’effectue cette étape que si elle régle le mode d’engagement de transaction à l’engagement manuel; si le mode de validation de transaction est auto-commit, qui est le défaut, la transaction est automatiquement validée lorsque la déclaration est exécutée. Pour plus d’informations, consultez [Transactions](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Pour exécuter une déclaration dans une nouvelle transaction, l’application revient à l’étape 3. Pour se déconnecter de la source de données, l’application se poursuit à l’étape 6.
