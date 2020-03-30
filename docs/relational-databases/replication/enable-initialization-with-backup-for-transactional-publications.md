---
title: Activer l’initialisation avec une sauvegarde (Transactionnel)
description: Découvrez comment activer l’initialisation à partir d’une sauvegarde pour une publication transactionnelle dans SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: 11670347380a3336068091601e739b28d4d34a39
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "75321713"
---
# <a name="enable-initialization-with-backup-for-transactional-publications"></a>Activer l’initialisation avec une sauvegarde pour les publications transactionnelles
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Pour initialiser un abonnement à une publication transactionnelle à partir d'une sauvegarde, vous devez configurer la publication de telle sorte qu'elle autorise une initialisation à partir d'une sauvegarde puis spécifier les informations de sauvegarde lors de la création de l'abonnement :  
  
-   Activez la publication dans la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Spécifiez les informations de sauvegarde avec la procédure stockée [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Pour plus d’informations sur les paramètres requis par **sp_addsubscription**, consultez [Initialiser un abonnement transactionnel à partir d’une sauvegarde &#40;programmation Transact-SQL de la réplication&#41;](../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md).  
  
### <a name="to-enable-initialization-with-a-backup"></a>Pour activer l'initialisation avec une sauvegarde  
  
1.  Dans la page **Options d’abonnement** de la boîte de dialogue **Propriétés de la publication - \<Publication>** , sélectionnez la valeur **True** pour l’option **Autoriser l’initialisation à partir des fichiers de sauvegarde**.  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser un abonnement transactionnel sans instantané](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
