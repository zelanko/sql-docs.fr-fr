---
title: Durées de vie de transaction | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 290d4c43767ba7e1c6f784c84473e9a05503af54
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213039"
---
# <a name="transaction-lifetimes"></a>Durées de vie des transactions
  Il existe une différence importante entre des transactions démarrées dans des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] et celles démarrées dans du code managé : le code CLR (Common Language Runtime) ne peut pas déséquilibrer l'état des transactions lors de l'entrée ou de la sortie d'un appel au CLR. Soyez conscient des implications d'une telle différence :  
  
-   Une transaction démarrée à l'intérieur d'une trame CLR doit être validée ou annulée ; dans le cas contraire, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère une erreur à la sortie de la trame.  
  
-   Une transaction externe ne peut pas être validée ni annulée au sein du code CLR.  
  
-   Une tentative de validation d'une transaction non démarrée dans la même procédure provoque une erreur d'exécution.  
  
-   Une tentative d'annulation d'une transaction non démarrée dans la même procédure provoque le blocage de la transaction (ce qui empêche toute opération collatérale de se produire). La transaction cesse jusqu'à ce que le code CLR soit hors de portée. Notez que cela peut être utile lorsque vous détectez une erreur à l'intérieur de votre procédure et souhaitez vous assurer que la transaction entière se termine.  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration et transactions du CLR](../native-client-ole-db-transactions/transactions.md)  
  
  
