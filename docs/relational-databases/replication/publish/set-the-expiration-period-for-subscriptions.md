---
title: "D&#233;finir la p&#233;riode d&#39;expiration des abonnements | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "abonnements [réplication SQL Server], expiration"
  - "expiration [réplication SQL Server]"
  - "périodes de rétention [SQL Server replication]"
  - "désactivation d'abonnements"
ms.assetid: 542f0613-5817-42d0-b841-fb2c94010665
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# D&#233;finir la p&#233;riode d&#39;expiration des abonnements
  Cette rubrique explique comment définir la période d'expiration des abonnements dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. La période d'expiration des abonnements détermine le temps qui précède l'expiration et la suppression d'un abonnement. Pour plus d'informations, voir [Subscription Expiration and Deactivation](../../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
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
 Définir la période d’expiration des abonnements sur le **Général** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour définir la période d'expiration des abonnements  
  
1.  Dans la **expiration de l’abonnement** section sur le **Général** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, spécifiez si l’abonnement doit expirer.  
  
2.  S'il doit expirer, spécifiez un délai d'expiration.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez utiliser des procédures stockées de réplication pour définir cette valeur lorsqu'une publication est créée ou pour modifier cette valeur ultérieurement.  
  
#### Pour définir la période d'expiration d'un abonnement à une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication, exécutez [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Spécifiez la période de l'expiration de l'abonnement souhaitée, en heures, pour **@retention**. La période d'expiration par défaut est de 336 heures. Pour plus d'informations, voir [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Pour définir la période d'expiration d'un abonnement à une publication de fusion  
  
1.  Sur le serveur de publication, exécutez [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Spécifiez la période d'expiration de l'abonnement en affectant la valeur de votre choix à **@retention**. Spécifiez les unités dans lesquelles la période d’expiration est exprimée pour **@retention_period_unit**, qui peut être une des opérations suivantes :  
  
    -   **1** = semaine  
  
    -   **2** = mois  
  
    -   **3** = année  
  
     La période d'expiration par défaut est de 14 jours. Pour plus d'informations, voir [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Pour modifier la période d'expiration d'un abonnement à une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication, exécutez [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Spécifiez **retention** pour **@property** et la nouvelle période d'expiration de l'abonnement, en heures, pour **@value**.  
  
#### Pour modifier la période d'expiration d'un abonnement à une publication de fusion  
  
1.  Sur le serveur de publication, exécutez [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), en spécifiant **@publication** et **@publisher**. Notez la valeur de **retention_period_unit** du jeu de résultats, qui peut être une des opérations suivantes :  
  
    -   **0** = jour  
  
    -   **1** = semaine  
  
    -   **2** = mois  
  
    -   **3** = année  
  
2.  Sur le serveur de publication, exécutez [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Spécifiez **retention** pour **@property** et la nouvelle période d'expiration de l'abonnement, sous forme de texte basé sur l'unité de période de rétention définie à l'étape 1, pour **@value**.  
  
3.  (Facultatif) Sur le serveur de publication, exécutez [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Spécifier **retention_period_unit** pour **@property** et une unité pour la période d’expiration d’abonnement pour **@value**.  
  
## Voir aussi  
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Expiration et désactivation des abonnements](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  