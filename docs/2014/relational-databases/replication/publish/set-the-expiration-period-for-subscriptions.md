---
title: Définir la période d’expiration des abonnements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], expiration
- expiration [SQL Server replication]
- retention periods [SQL Server replication]
- deactivating subscriptions
ms.assetid: 542f0613-5817-42d0-b841-fb2c94010665
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 95cdae09ead5238e8a48d3797f2b1f9a32b483f3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37268925"
---
# <a name="set-the-expiration-period-for-subscriptions"></a>Définir la période d'expiration des abonnements
  Cette rubrique explique comment définir la période d'expiration des abonnements dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. La période d'expiration des abonnements détermine le temps qui précède l'expiration et la suppression d'un abonnement. Pour plus d'informations, voir [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
-   **Pour définir la période d'expiration des abonnements à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   La période d'expiration de l'abonnement est également nommée *période de rétention de la publication*. Le nettoyage des métadonnées des réplications de fusion dépend de ce paramètre :  
  
    -   La réplication ne peut pas nettoyer les métadonnées dans les bases de données de publication et d'abonnement tant que la période de rétention n'est pas achevée. Soyez prudent si vous spécifiez une longue période de rétention, car cela peut affecter négativement les performances de réplication. Vous avez intérêt à spécifier une valeur faible si vous êtes certain que tous les Abonnés procéderont régulièrement à la synchronisation dans ce délai.  
  
         La période de rétention pour les publications de fusion offre un délai de grâce de 24 heures pour tenir compte des Abonnés situés dans différents fuseaux horaires. Si, par exemple, vous définissez une période de rétention d'un jour, la période de rétention réelle est de 48 heures.  
  
    -   Il est possible de spécifier que les abonnements n'expirent jamais, mais ceci est fortement déconseillé car les métadonnées ne pourront pas être nettoyées.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Définissez la période d’expiration des abonnements dans la page **Général** de la boîte de dialogue **Propriétés de la publication - \<Publication>**. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](view-and-modify-publication-properties.md).  
  
#### <a name="to-set-the-expiration-period-for-subscriptions"></a>Pour définir la période d'expiration des abonnements  
  
1.  Dans la section **Expiration de l’abonnement** de la page **Général** de la boîte de dialogue **Propriétés de la publication - \<Publication>**, spécifiez si l’abonnement doit expirer.  
  
2.  S'il doit expirer, spécifiez un délai d'expiration.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez utiliser des procédures stockées de réplication pour définir cette valeur lorsqu'une publication est créée ou pour modifier cette valeur ultérieurement.  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a>Pour définir la période d'expiration d'un abonnement à une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication, exécutez [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql). Spécifiez la période de l'expiration de l'abonnement souhaitée, en heures, pour **@retention**. La période d'expiration par défaut est de 336 heures. Pour plus d’informations, voir [Create a Publication](create-a-publication.md).  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-merge-publication"></a>Pour définir la période d'expiration d'un abonnement à une publication de fusion  
  
1.  Sur le serveur de publication, exécutez [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Spécifiez la période d'expiration de l'abonnement en affectant la valeur de votre choix à **@retention**. Spécifiez les unités dans lesquelles la période d'expiration est exprimée pour **@retention_period_unit**; les unités possibles sont les suivantes :  
  
    -   **1** = semaine  
  
    -   **2** = mois  
  
    -   **3** = année  
  
     La période d'expiration par défaut est de 14 jours. Pour plus d’informations, voir [Create a Publication](create-a-publication.md).  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a>Pour modifier la période d'expiration d'un abonnement à une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication, exécutez [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql). Spécifiez **retention** pour **@property** et la nouvelle période d'expiration de l'abonnement, en heures, pour **@value**.  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-merge-publication"></a>Pour modifier la période d'expiration d'un abonnement à une publication de fusion  
  
1.  Sur le serveur de publication, exécutez [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), en spécifiant **@publication** et **@publisher**. Notez la valeur de **retention_period_unit** dans le jeu de résultats ; elle peut correspondre à l'une des valeurs suivantes :  
  
    -   **0** = jour  
  
    -   **1** = semaine  
  
    -   **2** = mois  
  
    -   **3** = année  
  
2.  Sur le serveur de publication, exécutez [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql). Spécifiez **retention** pour **@property** et la nouvelle période d'expiration de l'abonnement, sous forme de texte basé sur l'unité de période de rétention définie à l'étape 1, pour **@value**.  
  
3.  (Facultatif) Sur le serveur de publication, exécutez [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql). Spécifiez **retention_period_unit** pour **@property** et une nouvelle unité pour la période d'expiration de l'abonnement pour **@value**.  
  
## <a name="see-also"></a>Voir aussi  
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md)  
  
  
