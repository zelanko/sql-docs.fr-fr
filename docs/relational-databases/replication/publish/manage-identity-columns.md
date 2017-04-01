---
title: "G&#233;rer des colonnes d&#39;identit&#233; | Microsoft Docs"
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
  - "valeurs d'identité [réplication SQL Server]"
  - "réplication de fusion [réplication SQL Server], gestion des plages d’identité"
  - "publication [réplication SQL Server], colonnes d’identité"
  - "réplication transactionnelle, gestion des plages d’identité"
  - "colonnes d’identité [SQL Server], réplication"
ms.assetid: 98892836-cf63-494a-bd5d-6577d9810ddf
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# G&#233;rer des colonnes d&#39;identit&#233;
  Cette rubrique explique comment gérer des colonnes d'identité dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Lorsque les insertions de l'Abonné sont répliquées sur le serveur de publication, les colonnes d'identité doivent être gérées afin d'éviter d'affecter la même valeur d'identité sur l'Abonné et sur le serveur de publication. La réplication peut gérer automatiquement les plages d'identité ou vous pouvez choisir de les gérer manuellement.  Pour plus d’informations sur les options de gestion de plage identité fournies par la réplication, consultez [répliquer les colonnes d’identité](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
-   **Pour gérer des colonnes d'identité à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Lors de la publication d'une table dans plusieurs publications, vous devez spécifier les mêmes options de gestion des plages d'identité pour les différentes publications. Pour plus d’informations, consultez « Publication de Tables dans plusieurs publications » dans [publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
-   Pour créer un numéro à incrémentation automatique qui peut être utilisé dans plusieurs tables ou qui peut être appelée à partir d’applications sans faire référence à n’importe quelle table, consultez [numéros de séquence](../../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Spécifier une option de gestion de colonne identity sur la **propriétés** onglet de le **Propriétés de l’Article - \< Article>** boîte de dialogue de l’Assistant Nouvelle Publication. Pour plus d’informations sur l’utilisation de cet Assistant, consultez la page [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md). Dans l'Assistant Nouvelle publication :  
  
-   Si vous sélectionnez **la publication de fusion** ou **une publication transactionnelle avec abonnements mis à jour** sur la **Type de Publication** sélectionnez gestion de plages d’identité automatique ou manuel (automatique, la valeur par défaut, est recommandée). Après la publication de la table, la propriété ne peut plus être modifiée mais d'autres propriétés liées peuvent l'être.  
  
-   Si vous sélectionnez d'autres types de publication, vous devez définir une gestion manuelle des plages d'identité.  
  
 Modifier les seuils et les plages d’identité sur le **propriétés** onglet de la **Propriétés de l’Article - \< Article>**, qui est disponible dans le **Propriétés de la Publication - \< Publication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Pour spécifier une option de gestion de colonnes d'identité  
  
1.  Si le serveur de publication exécute une version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieure à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], dans la page **Type de publication** de l'Assistant Nouvelle publication, sélectionnez **Publication de fusion** ou **Publication transactionnelle avec abonnements mis à jour**.  
  
2.  Dans la page **Articles** , sélectionnez une table avec une colonne d'identité.  
  
3.  Cliquez sur **Propriétés de l'article**puis sur **Définir les propriétés de l'article de la table en surbrillance**.  
  
4.  Sur le **propriétés** onglet de le **Propriétés de l’Article - \< Article>** boîte de dialogue le **plages d’identités** section, définissez la **gérer automatiquement les plages d’identité** propriété **automatique** ou **manuel** (pour les serveurs de publication exécutant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure), ou **True** ou **False** (pour les serveurs de publication exécutant une version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]).  
  
5.  Si vous avez sélectionné la valeur **Automatique** ou **Vrai** dans l'étape 4, entrez des valeurs pour les options du tableau suivant. Pour plus d’informations sur l’utilisation de ces paramètres, consultez la section « Affectation de plages d’identité » de [répliquer les colonnes d’identité](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
    |Option|Valeur|Description|  
    |------------|-----------|-----------------|  
    |**Taille de la plage sur le serveur de publication**|Valeur entière représentant la taille de la plage (par exemple, 20000).|Consultez la section « Affectation de plages d’identité » de [répliquer les colonnes d’identité](../../../relational-databases/replication/publish/replicate-identity-columns.md).|  
    |**Taille de la plage sur l'Abonné**|Valeur entière représentant la taille de la plage (par exemple, 10000).|Consultez la section « Affectation de plages d’identité » de [répliquer les colonnes d’identité](../../../relational-databases/replication/publish/replicate-identity-columns.md).|  
    |**Pourcentage du seuil de plage**|Valeur entière représentant le pourcentage du seuil (par exemple, 90 signifie 90 %)|Pourcentage représentant le nombre total de valeurs d'identité utilisées sur un nœud avant d'affecter une nouvelle plage d'identité.<br /><br /> <br /><br /> Remarque : cette valeur doit être spécifiée, mais n’est utilisée que par les Abonnés utilisant des abonnements mis à jour en attente et les Abonnés aux publications de fusion qui exécutent [!INCLUDE[ssEW](../../../includes/ssew-md.md)] ou des versions antérieures d’autres éditions de SQL Server. Pour plus d’informations, consultez la section « Affectation de plages d’identité » de [répliquer les colonnes d’identité](../../../relational-databases/replication/publish/replicate-identity-columns.md).|  
    |**Valeur de départ de la prochaine plage**|Valeur de type entier. En lecture seule.|Valeur de départ de la prochaine plage. Si, par exemple, la plage actuelle va de 5001 à 6000, il s'agira de la valeur 6001.|  
    |**Valeur d'identité maximale**|Valeur de type entier. En lecture seule.|Valeur maximale de la colonne identité. Déterminée par le type de données de base de la colonne.|  
    |**Incrément**|Valeur de type entier. En lecture seule.|Valeur utilisée pour augmenter ou diminuer le nombre de la colonne d'identité à chaque insertion : en règle générale définie à 1.|  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Pour modifier les seuils et les plages d'identité après la publication d'une table  
  
1.  Sur le **Articles** page de le **Propriétés de la Publication - \< Publication>** boîte de dialogue, sélectionnez une table avec une colonne d’identité.  
  
2.  Cliquez sur **Propriétés de l'article**puis sur **Définir les propriétés de l'article de la table en surbrillance**.  
  
3.  Sur le **propriétés** onglet de la **Propriétés de l’Article - \< Article>** boîte de dialogue le **plages d’identités** section, entrez des valeurs pour un ou plusieurs des propriétés suivantes : **taille de la plage Publisher**, **taille de la plage abonné**, et **pourcentage de seuil de plage**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Cliquez sur **OK** sur la **Propriétés de la Publication - \< Publication>** boîte de dialogue.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Vous pouvez utiliser des procédures stockées de réplication pour spécifier les options de gestion des plages d'identité lors de la création d'un article.  
  
#### Pour activer la gestion automatique des plages d'identité lors de la définition d'articles pour une publication transactionnelle  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Si la table source en cours de publication a une colonne d’identité, spécifiez une valeur de **automatique** pour **@identityrangemanagementoption**, la plage de valeurs d’identité affectée au serveur de publication pour **@pub_identity_range**, la plage de valeurs d’identité affectées à chaque abonnés pour **@identity_range**, et le pourcentage total de valeurs d’identité utilisées avant une nouvelle plage d’identité est assignée pour **@threshold**. Pour plus d’informations sur la définition d’articles, consultez [définir un Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Vérifiez que le type de données de la colonne d'identité est suffisamment grand pour prendre en charge la plage totale des identités affectées à l'ensemble des Abonnés.  
  
#### Pour désactiver la gestion automatique des plages d'identité lors de la définition d'articles pour une publication transactionnelle  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Affectez la valeur **manual** à **@identityrangemanagementoption**. Pour plus d’informations sur la définition d’articles, consultez [définir un Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Affectez des plages aux colonnes d'identité d'article sur l'Abonné pour éviter de générer des conflits lors de la mise à jour des Abonnés. Pour plus d’informations, consultez la section sur l’affectation de plages pour la gestion de plages d’identité manuelle dans la rubrique [répliquer les colonnes d’identité](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
#### Pour activer la gestion automatique des plages d'identité lors de la définition d'articles pour une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Si la table source en cours de publication a une colonne d’identité, spécifiez une valeur de **automatique** pour **@identityrangemanagementoption**, la plage de valeurs d’identité affectées à un abonnement serveur pour **@pub_identity_range**, la plage de valeurs d’identité affectée à l’éditeur et pour chaque abonnement client **@identity_range**, et le pourcentage total de valeurs d’identité utilisées avant une nouvelle plage d’identité est assignée pour **@threshold**. Pour plus d’informations lorsque les nouvelles plages d’identité sont affectés, consultez Affectation les plages d’identité dans la rubrique [répliquer les colonnes d’identité](../../../relational-databases/replication/publish/replicate-identity-columns.md). Pour plus d’informations sur la définition d’articles, consultez [définir un Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Vérifiez que le type de données de la colonne d'identité est suffisamment grand pour prendre en charge la plage totale des identités qui sont assignées à l'ensemble des Abonnés, en particulier pour les Abonnés avec des abonnements serveur.  
  
#### Pour désactiver la gestion automatique des plages d'identité lors de la définition d'articles pour une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Affectez l'une des valeurs suivantes à **@identityrangemanagementoption**:  
  
    -   **manuel** -les plages d’identité doivent être affectées manuellement pour mettre à jour des abonnés.  
  
    -   **aucun** -colonnes d’identité sur le serveur de publication ne seront pas définies en tant que colonnes d’identité sur l’abonné.  
  
     Pour plus d’informations sur la définition d’articles, consultez [définir un Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Affectez des plages aux colonnes d'identité d'article sur l'Abonné pour éviter de générer des conflits lors de la mise à jour des Abonnés.  
  
#### Pour modifier les paramètres de gestion automatique des plages d'identité pour un article existant dans une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md) et notez la valeur de **identityrangemanagementoption** dans le résultat défini. Si cette valeur est **0**, la gestion automatique des plages d'identité n'est pas activée.  
  
2.  Si la valeur de **identityrangemanagementoption** dans le jeu de résultats est **1**, modifiez les paramètres suivants :  
  
    -   Pour modifier les plages d’identité affectées, exécutez [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) sur le serveur de publication sur la base de données de publication. Spécifiez la valeur **identity_range** ou **pub_identity_range** pour **@property** et la nouvelle valeur de plage **@value**.  
  
    -   Pour modifier le seuil d’affectation de nouvelles plages, exécutez [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) sur le serveur de publication sur la base de données de publication. Affectez la valeur **threshold** à **@property** et spécifiez la nouvelle valeur de seuil pour **@value**.  
  
#### Pour modifier les paramètres de gestion automatique des plages d'identité pour un article existant dans une publication de fusion  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) et notez la valeur de **identity_support** dans le résultat défini. Si cette valeur est **0**, la gestion automatique des plages d'identité n'est pas activée.  
  
2.  Si la valeur de **identity_support** dans le résultat de jeu est **1**, modifiez les paramètres comme suit :  
  
    -   Pour modifier les plages d’identité affectées, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) sur le serveur de publication sur la base de données de publication. Spécifiez la valeur **identity_range** ou **pub_identity_range** pour **@property** et la nouvelle valeur de plage **@value**.  
  
    -   Pour modifier le seuil d’affectation de nouvelles plages, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) sur le serveur de publication sur la base de données de publication. Affectez la valeur **threshold** à **@property** et spécifiez la nouvelle valeur de seuil pour **@value**. Pour plus d’informations lorsque les nouvelles plages d’identité sont affectés, consultez Affectation les plages d’identité dans la rubrique [répliquer les colonnes d’identité](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
    -   Pour désactiver la gestion de plages d’identité automatiques, exécutez [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) sur le serveur de publication sur la base de données de publication. Affectez la valeur **identityrangemanagementoption** à **@property** et la valeur **manual** ou **none** à **@value**.  
  
## Voir aussi  
 [Réplication transactionnelle d'égal à égal](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Répliquer des colonnes d'identité](../../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  