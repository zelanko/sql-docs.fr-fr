---
title: MSSQL_ENG014005 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 418628c33764c6e765e8ba855da20f0890f6191a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62666879"
---
# <a name="mssqleng014005"></a>MSSQL_ENG014005
    
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
 Supprimez les abonnements avant de supprimer la publication. Si vous utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour supprimer la publication, vous pouvez choisir de supprimer automatiquement tous les abonnements associés avant de supprimer la publication. Si vous utilisez des procédures stockées, vous devez d'abord explicitement supprimer les abonnements. Pour plus d'informations, consultez [Delete a Push Subscription](delete-a-push-subscription.md) et [Delete a Pull Subscription](delete-a-pull-subscription.md).  
  
 S'il semble ne pas exister d'abonnements pour la publication ou si vous voyez cette erreur quand vous créez une publication, il est possible qu'un abonnement antérieur n'ait pas été complètement nettoyé quand il a été supprimé. Exécutez [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) sur la base de données pour supprimer tous les objets et paramètres liés à la réplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
