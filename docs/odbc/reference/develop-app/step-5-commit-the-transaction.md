---
title: 'Étape 5 : valider la transaction | Microsoft Docs'
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283349"
---
# <a name="step-5-commit-the-transaction"></a>Étape 5 : Valider la transaction
L’étape suivante consiste à valider la transaction, comme indiqué dans l’illustration suivante.  
  
 ![Présente la validation d'une transaction](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 La cinquième étape consiste à appeler **SQLEndTran** pour valider ou restaurer la transaction. L’application effectue cette étape uniquement si elle définit le mode de validation de transaction sur Manuel-Commit ; Si le mode de validation de transaction est auto-commit, qui est la valeur par défaut, la transaction est automatiquement validée lors de l’exécution de l’instruction. Pour plus d’informations, consultez [Transactions](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Pour exécuter une instruction dans une nouvelle transaction, l’application retourne à l’étape 3. Pour se déconnecter de la source de données, l’application passe à l’étape 6.
