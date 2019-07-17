---
title: 'Étape 5 : Valider la Transaction | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bde493edbc6d677b27ef72a24736b504959a7b59
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114128"
---
# <a name="step-5-commit-the-transaction"></a>Étape 5 : Valider la transaction
L’étape suivante consiste à valider la transaction, comme indiqué dans l’illustration suivante.  
  
 ![Montre comment valider une transaction](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 La cinquième étape consiste à appeler **SQLEndTran** pour valider ou restaurer la transaction. L’application effectue cette étape uniquement si elle la valeur est le mode de validation de transaction de validation manuelle ; Si le mode de validation de transaction est validation automatique, qui est la valeur par défaut, la transaction est automatiquement validée lorsque l’instruction est exécutée. Pour plus d’informations, consultez [Transactions](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Pour exécuter une instruction dans une nouvelle transaction, l’application retourne à l’étape 3. Pour vous déconnecter de la source de données, l’application se poursuit à l’étape 6.
