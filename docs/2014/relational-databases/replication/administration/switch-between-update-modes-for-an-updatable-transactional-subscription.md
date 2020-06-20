---
title: Basculer entre les modes de mise à jour d’un abonnement transactionnel pouvant être mis à jour | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, update modes
- subscriptions [SQL Server replication], updatable
ms.assetid: ab5ebab1-7ee4-41f4-999b-b4f0c420c921
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c31814d1e2ab6fac64ffcde883f3cac2439828a1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055729"
---
# <a name="switch-between-update-modes-for-an-updatable-transactional-subscription"></a>Basculer entre les modes de mise à jour d'un abonnement transactionnel pouvant être mis à jour
  Cette rubrique explique comment basculer entre les modes de mise à jour d'un abonnement transactionnel pouvant être mis à jour dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Spécifiez le mode des abonnements pouvant être mis à jour à l'aide de l'Assistant Nouvel abonnement. Pour plus d’informations sur la définition de ce mode lors de l’utilisation de cet Assistant, consultez [Afficher et modifier les propriétés d’un abonnement par extraction](../view-and-modify-pull-subscription-properties.md).  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Vous pouvez basculer à tout instant d’une mise à jour immédiate vers une mise à jour en file d’attente. Après que vous avez basculé, cependant, vous ne pouvez pas repasser en mise à jour immédiate avant que l'abonné et le serveur de publication ne soient connectés et que l'Agent de lecture de la file d'attente n'ait appliqué tous les messages en attente dans la file d'attente sur le serveur de publication.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
  
-   Lorsqu'un abonnement avec mise à jour à une publication transactionnelle prend en charge le basculement d'un mode de mise à jour vers un autre, vous pouvez basculer par programmation les modes de mise à jour pour gérer les situations où la connectivité change pendant une courte période de temps. Le mode de mise à jour peut être défini par programmation et à la demande à l'aide de procédures stockées de réplication. Pour plus d’informations, voir [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
> [!NOTE]  
>  Pour modifier le mode de mise à jour après que l'abonnement a été créé, vous devez affecter à la propriété **update_mode** la valeur **failover** (qui permet de basculer de la mise à jour immédiate vers la mise à jour en attente) ou **queued failover** (qui permet de basculer de la mise à jour en attente vers la mise à jour immédiate) lors de la création de l'abonnement. Ces propriétés sont automatiquement définies dans l'Assistant Nouvel abonnement.  
  
#### <a name="to-set-the-updating-mode-for-a-push-subscription"></a>Pour définir le mode de mise à jour d'un abonnement envoyé  
  
1.  Connectez-vous à l'Abonné dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Abonnements locaux** .  
  
3.  Cliquez avec le bouton droit sur l'abonnement dont vous voulez définir le mode de mise à jour puis cliquez sur **Définir la méthode de mise à jour**.  
  
4.  Dans la boîte de dialogue **définir la méthode de mise à jour- \<Subscriber> : \<SubscriptionDatabase> ** , sélectionnez **mise à jour immédiate** ou mise à jour en **attente**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-the-updating-mode-for-a-pull-subscription"></a>Pour définir le mode de mise à jour d'un abonnement extrait  
  
1.  Dans la boîte de dialogue Propriétés de l' **abonnement- \<Publisher> \<PublicationDatabase> :** , sélectionnez la valeur **répliquer immédiatement les modifications** ou mettre les **modifications en file d’attente** pour l’option **méthode de mise à jour** de l’abonné.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 Pour plus d’informations sur l’accès à la boîte de dialogue **Propriétés de l’abonnement- \<Publisher> \<PublicationDatabase> :** , consultez [afficher et modifier les propriétés](../view-and-modify-pull-subscription-properties.md)d’un abonnement par extraction.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-switch-between-update-modes"></a>Pour basculer d'un mode de mise à jour vers un autre  
  
1.  Vérifiez que l'abonnement prend en charge le basculement en exécutant [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql) pour un abonnement par extraction ou [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) pour un abonnement par émission de données. Si la valeur de **mode de mise à jour** dans le jeu de résultats est **3** ou **4**, le basculement est pris en charge.  
  
2.  Sur l'Abonné de la base de données d'abonnement, exécutez [sp_setreplfailovermode](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql). Spécifiez **@publisher** ,, **@publisher_db** et l' **@publication** une des valeurs suivantes pour **@failover_mode** :  
  
    -   **mis en file d'attente** - basculement sur la mise à jour en attente lorsque la connectivité a été perdue temporairement.  
  
    -   **immédiat** - basculement sur la mise à jour immédiate lorsque la connectivité a été restaurée.  
  
## <a name="see-also"></a>Voir aussi  
 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
