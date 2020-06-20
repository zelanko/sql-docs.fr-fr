---
title: La mise à niveau modifiera les abonnements de mise à jour en attente qui utilisent Message Queuing | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication]
- MSMQ [SQL Server replication]
- queues [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
ms.assetid: 97944de3-fbad-4db1-939a-dcd550bf5893
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d44cbad43d75634cbf8660110cc879522265c54d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058856"
---
# <a name="upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing"></a>La mise à niveau modifiera les abonnements de mise à jour en attente qui utilisent Message Queuing
  Le Conseiller de mise à niveau a détecté que vous possédez un ou plusieurs abonnements de mise à jour en attente qui utilisent [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (MSMQ). Étant donné que la réplication ne prend plus en charge Message Queuing, les abonnements seront modifiés afin d'utiliser une file d'attente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Seule une valeur **SQL** est autorisée. Les publications existantes qui utilisent Message Queuing sont modifiées lors de la mise à niveau afin de prendre en charge une file d'attente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si certaines de vos applications dépendent de la mise à jour en attente à l'aide de Message Queuing, vous devrez les réécrire pour qu'elles puissent utiliser une file d'attente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d'informations sur les abonnements de mise à jour en attente, consultez la rubrique « Abonnements pouvant être mis à jour pour la réplication transactionnelle » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La mise à niveau vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supprime les files d'attente d'abonnement Message Queuing existantes si le service Message Queuing est parallèlement en cours d'exécution.  
  
 Si le service Message Queuing n'est pas en cours d'exécution, supprimez les files d'attente manuellement une fois la mise à niveau achevée. Pour plus d'informations sur la suppression des files d'attente, consultez la documentation de Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de la réplication](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
