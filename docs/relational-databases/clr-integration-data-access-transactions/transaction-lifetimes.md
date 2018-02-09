---
title: "Durée de vie des transactions | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f24c0e6642a01b5f1d59ae82c7c09ce9ed94e7fb
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="transaction-lifetimes"></a>Durées de vie des transactions
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Il existe une différence importante entre des transactions démarrées dans des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] et celles démarrées dans du code managé : le code CLR (Common Language Runtime) ne peut pas déséquilibrer l'état des transactions lors de l'entrée ou de la sortie d'un appel au CLR. Soyez conscient des implications d'une telle différence :  
  
-   Une transaction démarrée à l'intérieur d'une trame CLR doit être validée ou annulée ; dans le cas contraire, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère une erreur à la sortie de la trame.  
  
-   Une transaction externe ne peut pas être validée ni annulée au sein du code CLR.  
  
-   Une tentative de validation d'une transaction non démarrée dans la même procédure provoque une erreur d'exécution.  
  
-   Une tentative d'annulation d'une transaction non démarrée dans la même procédure provoque le blocage de la transaction (ce qui empêche toute opération collatérale de se produire). La transaction cesse jusqu'à ce que le code CLR soit hors de portée. Notez que cela peut être utile lorsque vous détectez une erreur à l'intérieur de votre procédure et souhaitez vous assurer que la transaction entière se termine.  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions et l’intégration du CLR](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
