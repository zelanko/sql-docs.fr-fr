---
title: MSSQL_ENG014005 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d701ed8b71e28edf61e87bfedf2a790bfe695403
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="mssqleng014005"></a>MSSQL_ENG014005
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14005|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de supprimer la publication. Il existe un abonnement.|  
  
## <a name="explanation"></a>Explication  
 Vous avez tenté de supprimer une publication qui a un ou plusieurs abonnements associés. Une publication peut être supprimée seulement s'il n'y a pas d'abonnements associés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Supprimez les abonnements avant de supprimer la publication. Si vous utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour supprimer la publication, vous pouvez choisir de supprimer automatiquement tous les abonnements associés avant de supprimer la publication. Si vous utilisez des procédures stockées, vous devez d'abord explicitement supprimer les abonnements. Pour plus d'informations, consultez [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md) et [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 S'il semble ne pas exister d'abonnements pour la publication ou si vous voyez cette erreur quand vous créez une publication, il est possible qu'un abonnement antérieur n'ait pas été complètement nettoyé quand il a été supprimé. Exécutez [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) sur la base de données pour supprimer tous les objets et paramètres liés à la réplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
