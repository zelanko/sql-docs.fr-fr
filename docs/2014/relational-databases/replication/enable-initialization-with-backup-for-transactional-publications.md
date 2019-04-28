---
title: Activer l’initialisation avec une sauvegarde pour les Publications transactionnelles (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 046eb926391faff26bb3238dfd225619e9fec374
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62721343"
---
# <a name="enable-initialization-with-a-backup-for-transactional-publications-sql-server-management-studio"></a>activer l'initialisation avec une sauvegarde pour les publications transactionnelles (SQL Server Management Studio)
  Pour initialiser un abonnement à une publication transactionnelle à partir d'une sauvegarde, vous devez configurer la publication de telle sorte qu'elle autorise une initialisation à partir d'une sauvegarde puis spécifier les informations de sauvegarde lors de la création de l'abonnement :  
  
-   Activez la publication dans la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](publish/view-and-modify-publication-properties.md).  
  
-   Spécifiez les informations de sauvegarde avec la procédure stockée [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Pour plus d’informations sur les paramètres requis par **sp_addsubscription**, consultez [Initialiser un abonnement transactionnel à partir d’une sauvegarde &#40;programmation Transact-SQL de la réplication&#41;](initialize-a-transactional-subscription-from-a-backup.md).  
  
### <a name="to-enable-initialization-with-a-backup"></a>Pour activer l'initialisation avec une sauvegarde  
  
1.  Dans la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>**, sélectionnez la valeur **True** pour l’option **Autoriser l’initialisation à partir des fichiers de sauvegarde**.  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser un abonnement transactionnel sans instantané](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
