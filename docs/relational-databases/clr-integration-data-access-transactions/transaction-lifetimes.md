---
title: Durée de vie des transactions (fr) Microsoft Docs
description: Renseignez-vous sur les durées de vie des transactions dans l’intégration SQL Server CLR. Les transactions commencées dans les procédures stockées De Transact-SQL diffèrent de celles commencées dans le code géré.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
ms.openlocfilehash: 1fed737c644ebb241a5761fffd2409c2556d28ea
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487495"
---
# <a name="transaction-lifetimes"></a>Durées de vie des transactions
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Il existe une différence importante entre des transactions démarrées dans des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] et celles démarrées dans du code managé : le code CLR (Common Language Runtime) ne peut pas déséquilibrer l'état des transactions lors de l'entrée ou de la sortie d'un appel au CLR. Soyez conscient des implications d'une telle différence :  
  
-   Une transaction démarrée à l'intérieur d'une trame CLR doit être validée ou annulée ; dans le cas contraire, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère une erreur à la sortie de la trame.  
  
-   Une transaction externe ne peut pas être validée ni annulée au sein du code CLR.  
  
-   Une tentative de validation d'une transaction non démarrée dans la même procédure provoque une erreur d'exécution.  
  
-   Une tentative de faire reculer une transaction qui n’a pas été amorcée dans la même procédure fait cesser de répondre à la transaction (empêchant toute autre opération d’effet secondaire). La transaction cesse jusqu'à ce que le code CLR soit hors de portée. Notez que cela peut être utile lorsque vous détectez une erreur à l'intérieur de votre procédure et souhaitez vous assurer que la transaction entière se termine.  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration et transactions du CLR](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
