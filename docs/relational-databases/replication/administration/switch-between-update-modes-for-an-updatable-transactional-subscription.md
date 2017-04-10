---
title: "Basculer entre les modes de mise &#224; jour d&#39;un abonnement transactionnel pouvant &#234;tre mis &#224; jour | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "réplication transactionnelle, abonnements pouvant être mis à jour"
  - "abonnements pouvant être mis à jour, modes de mise à jour"
  - "abonnements [réplication SQL Server], abonnements pouvant être mis à jour"
ms.assetid: ab5ebab1-7ee4-41f4-999b-b4f0c420c921
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Basculer entre les modes de mise &#224; jour d&#39;un abonnement transactionnel pouvant &#234;tre mis &#224; jour
  Cette rubrique explique comment basculer entre les modes de mise à jour d'un abonnement transactionnel pouvant être mis à jour dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Spécifiez le mode des abonnements pouvant être mis à jour à l'aide de l'Assistant Nouvel abonnement. Pour plus d’informations sur la définition du mode lors de l’utilisation de cet Assistant, consultez [Afficher et modifier les propriétés d’abonnement extrait](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
-   **Pour basculer entre les modes de mise à jour d'un abonnement transactionnel pouvant être mis à jour à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Vous pouvez basculer à tout instant d’une mise à jour immédiate vers une mise à jour en file d’attente. Après que vous avez basculé, cependant, vous ne pouvez pas repasser en mise à jour immédiate avant que l'abonné et le serveur de publication ne soient connectés et que l'Agent de lecture de la file d'attente n'ait appliqué tous les messages en attente dans la file d'attente sur le serveur de publication.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Lorsqu'un abonnement avec mise à jour à une publication transactionnelle prend en charge le basculement d'un mode de mise à jour vers un autre, vous pouvez basculer par programmation les modes de mise à jour pour gérer les situations où la connectivité change pendant une courte période de temps. Le mode de mise à jour peut être défini par programmation et à la demande à l'aide de procédures stockées de réplication. Pour plus d’informations, consultez la page [à des abonnements pour la réplication transactionnelle](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
> [!NOTE]  
>  Pour modifier le mode de mise à jour une fois l’abonnement est créé, le **update_mode** propriété doit être définie sur **basculement** (ce qui permet à un commutateur à partir de la mise à jour immédiate à la file d’attente mise à jour) ou **en file d’attente de basculement** (ce qui permet à un commutateur à partir de la mise à jour en file d’attente de mise à jour immédiate) lorsque l’abonnement est créé. Ces propriétés sont automatiquement définies dans l'Assistant Nouvel abonnement.  
  
#### Pour définir le mode de mise à jour d'un abonnement envoyé  
  
1.  Connectez-vous à l'Abonné dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** , puis développez le dossier **Abonnements locaux** .  
  
3.  Cliquez sur l’abonnement pour lequel vous souhaitez définir le mode de mise à jour, puis cliquez sur **définir la méthode de mise à jour**.  
  
4.  Dans la **définir la méthode de mise à jour - \< abonné>: \< BasededonnéesAbonnement>** boîte de dialogue, sélectionnez **mise à jour immédiate** ou **la mise à jour en file d’attente**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Pour définir le mode de mise à jour d'un abonnement extrait  
  
1.  Dans la **Propriétés de l’abonnement - \< Publisher>: \< Basedonnéespublication>** boîte de dialogue, sélectionnez la valeur **répliquer les modifications immédiatement** ou **modifications en file d’attente** pour la **méthode de mise à jour d’abonnés** option.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 Pour plus d’informations sur l’accès à la **Propriétés de l’abonnement - \< serveur de publication>: \< Basedonnéespublication>** boîte de dialogue, consultez [Afficher et modifier les propriétés d’abonnement extrait](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour basculer d'un mode de mise à jour vers un autre  
  
1.  Vérifiez que l’abonnement prend en charge le basculement en exécutant [sp_helppullsubscription](../../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md) pour un abonnement extrait ou [sp_helpsubscription](../../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md) pour un abonnement envoyé. Si la valeur de **mode de mise à jour** dans le jeu de résultats est **3** ou **4**, le basculement est pris en charge.  
  
2.  Sur la base de données d’abonnement de l’abonné, exécutez [sp_setreplfailovermode](../../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md). Spécifiez **@publisher**, **@publisher_db**, **@publication**, et une de ces valeurs pour **@failover_mode**:  
  
    -   **la file d’attente** -basculer la mise à jour en file d’attente lors de la connexion a été perdue temporairement.  
  
    -   **immédiate** -Basculer vers une mise à jour immédiate lorsque la connectivité a été rétablie.  
  
## Voir aussi  
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  