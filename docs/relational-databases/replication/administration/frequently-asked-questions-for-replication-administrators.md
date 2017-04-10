---
title: "Forum Aux Questions pour les Administrateurs de r&#233;plication | Microsoft Docs"
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
  - "administration de la réplication, forum aux questions"
  - "réplication [SQL Server], administration"
ms.assetid: 5a9e4ddf-3cb1-4baf-94d6-b80acca24f64
caps.latest.revision: 59
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 59
---
# Forum Aux Questions pour les Administrateurs de r&#233;plication
  Les questions et réponses suivantes fournissent des indications sur une variété de tâches auxquelles les administrateurs de bases de données répliquées sont confrontés.  
  
## Configuration d'une réplication  
  
### L'activité doit-elle être arrêtée sur une base de données lorsqu'elle est publiée ?  
 Non. L'activité peut continuer sur une base de données pendant la création d'une publication. Sachez que la création d'un instantané utilise de nombreuses ressources, il est donc préférable de générer les instantanés lors de périodes de faible activité sur la base de données (un instantané est généré par défaut lorsque vous terminez l'Assistant Nouvelle publication).  
  
### Les tables sont-elles verrouillées pendant la génération d'un instantané ?  
 La durée de verrouillage dépend du type de réplication utilisé :  
  
-   Pour les publications de fusion, l'Agent d'instantané n'utilise aucun verrou.  
  
-   Pour les publications transactionnelles, par défaut l'Agent d'instantané utilise des verrous uniquement lors de la phase initiale de génération d'instantané.  
  
-   Pour les publications d'instantané, l'Agent d'instantané utilise des verrous pendant toute la durée du processus de génération d'instantané.  
  
 Comme les verrous empêchent les autres utilisateurs de mettre à jour les tables, l'exécution de l'Agent d'instantané devrait être planifiée lors de périodes de faible activité sur la base de données, principalement pour les publications d'instantané.  
  
### Quand un abonnement est-il disponible, quand la base de données d'abonnement peut-elle être utilisée ?  
 Un abonnement est disponible après que l'instantané ait été appliqué à la base de données d'abonnement. Bien que la base de données d'abonnement soit accessible avant, il est conseillé de ne pas l'utiliser tant que l'instantané n'a pas été appliqué. Utilisez le Moniteur de réplication pour vérifier l'état de génération et d'application d'instantané :  
  
-   L'instantané est généré par l'Agent d'instantané. Affichez l'état de génération de l'instantané sur l'onglet **Agents** pour une publication du moniteur de réplication. Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
-   L'instantané est appliqué par l'Agent de distribution ou par l'Agent de fusion. Affichez l'état d'application d'instantané sur la page **Agent de distribution** ou **Agent de fusion** du Moniteur de réplication. Pour plus d’informations, consultez [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
### Que se passe-t-il si l’Agent d'instantané n’a pas terminé lorsque l’Agent de distribution ou l'Agent de fusion démarre ?  
 Cela n'entraînera aucune erreur si l'Agent de distribution ou l'Agent de fusion s'exécute en même temps que l'Agent d'instantané. Vous devez cependant prendre en compte les éléments suivants :  
  
-   Si l'Agent de distribution ou l'Agent de fusion est configuré pour une exécution en continu, l'Agent applique automatiquement l'instantané une fois que l'Agent d'instantané est terminé.  
  
-   Si l'Agent de distribution ou l'Agent de fusion est configuré pour une exécution planifiée ou à la demande, et qu'aucun instantané n'est disponible pendant que l'Agent s'exécute, l'Agent s'arrêtera en affichant un message indiquant qu'un instantané n'est pas encore disponible. Vous devez relancer l'exécution de l'Agent pour appliquer l'instantané une fois que l'Agent d'instantané est terminé. Pour plus d’informations sur l’exécution des agents, consultez [synchroniser un abonnement Push](../../../relational-databases/replication/synchronize-a-push-subscription.md), [synchroniser un abonnement extrait](../../../relational-databases/replication/synchronize-a-pull-subscription.md), et [Concepts des exécutables de l’Agent réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
### Dois-je créer un script de ma configuration de réplication ?  
 Oui. Le script de la configuration de réplication est un composant clé de tout plan de récupération d'urgence pour une topologie de réplication. Pour plus d'informations sur les scripts, consultez [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
### Quel est le mode de récupération nécessaire sur une base de données répliquée ?  
 La réplication fonctionne correctement à l'aide de n'importe quel mode de récupération : simple, journalisé en bloc ou restauration complète. La réplication de fusion assure le suivi des modifications en stockant les informations dans des tables de métadonnées. La réplication transactionnelle assure le suivi des modifications par un marquage du journal des transactions, mais ce processus de marquage n'est pas concerné par le mode de récupération.  
  
### Pourquoi la réplication ajoute-t-elle une colonne aux tables répliquées, sera-t-elle supprimée si la table n'est pas publiée ?  
 Afin d'assurer le suivi des modifications, la réplication de fusion et la réplication transactionnelle avec mise à jour d'abonnements en attente doivent pouvoir identifier de manière unique chaque ligne dans chaque table publiée. À cet effet :  
  
-   La réplication de fusion ajoute la colonne **rowguid** à chaque table, sauf si la table contient déjà une colonne de type de données **uniqueidentifier** avec la **ROWGUIDCOL** propriété définie (auquel cas cette colonne est utilisée). Si la table est supprimée de la publication, la colonne **rowguid** est supprimée, si une colonne existante était utilisée pour le suivi, la colonne n'est pas supprimée.  
  
-   Si une publication transactionnelle prend en charge les abonnements mis à jour en file d’attente, la réplication ajoute la colonne **msrepl_tran_version** à chaque table. Si la table est supprimée de la publication, le **msrepl_tran_version** colonne n’est pas supprimée.  
  
-   Aucun filtre ne doit inclure le **rowguidcol** utilisé par la réplication pour identifier les lignes. Par défaut, il s'agit de la colonne ajoutée lorsque vous avez configuré la réplication de fusion et qui a pour nom **rowguid**.  
  
### Comment puis-je gérer les contraintes sur les tables publiées ?  
 Il convient de tenir compte de plusieurs problèmes concernant les contraintes sur les tables publiées :  
  
-   La réplication transactionnelle nécessite une contrainte de clé primaire sur chaque table publiée. La réplication de fusion ne nécessite pas de clé primaire, mais s'il en existe une, elle doit être répliquée. La réplication d'instantané ne nécessite pas de clé primaire.  
  
-   Par défaut, les contraintes de clé primaire, les index et les contraintes de validation sont répliquées aux abonnés.  
  
-   L'option NOT FOR REPLICATION est spécifiée par défaut pour les contraintes de clé étrangère et les contraintes de validation, les contraintes étant renforcées pour les opérations d'utilisateurs mais pas pour les opérations d'agents.  
  
 Pour plus d'informations sur le paramétrage des options de schéma permettant de contrôler si les contraintes sont répliquées, consultez [Specify Schema Options](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
### Comment puis-je gérer les colonnes d'identité ?  
 La réplication fournit une gestion automatique de plages d'identité pour les topologies de réplication comprenant des mises à jour sur l'Abonné. Pour plus d’informations, consultez [répliquer les colonnes d’identité](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
### Les mêmes objets peuvent-ils être publiés dans différentes publications ?  
 Oui, mais avec quelques restrictions. Pour plus d’informations, consultez la section « Publication de Tables dans plusieurs publications » dans la rubrique [publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
### Plusieurs publications peuvent-elles utiliser la même base de données de distribution ?  
 Oui. Il n'existe aucune restriction sur le nombre ou les types de publications pouvant utiliser la même base de données de distribution. Toutes les publications d'un serveur de publication donné doivent utiliser le même serveur de distribution et la même base de données de distribution.  
  
 Si vous avez plusieurs publications, vous pouvez configurer plusieurs bases de données de distribution sur l'Abonné pour garantir que les données passant dans chaque base de données de distribution proviennent d'une seule publication. Utilisez la **des propriétés de serveur de distribution** boîte de dialogue ou [sp_adddistributiondb & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) Pour ajouter une base de données de distribution. Pour plus d’informations sur l’accès à la boîte de dialogue, consultez [Afficher et de modifier le serveur de distribution et de propriétés de l’éditeur](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### Comment puis-je trouver des informations sur le serveur de distribution et de publication, par exemple quels objets d'une base de données sont publiés ?  
 Ces informations sont disponibles via [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]et plusieurs procédures stockées de réplication. Pour plus d’informations, voir [Distributor and Publisher Information Script](../../../relational-databases/replication/administration/distributor-and-publisher-information-script.md).  
  
### La réplication chiffre-t-elle les données ?  
 Non. La réplication ne chiffre pas les données stockées dans la base de données ou transférées sur le réseau. Pour plus d’informations, consultez la section « Chiffrement » de la rubrique [vue d’ensemble de la sécurité & #40 ; Réplication & #41 ;](../../../relational-databases/replication/security/security-overview-replication.md).  
  
### Comment puis-je répliquer des données via Internet ?  
 Vous pouvez répliquer des données via Internet en utilisant :  
  
-   Un réseau privé virtuel (VPN). Pour plus d’informations, consultez [publier des données via Internet à l’aide de VPN](../../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md).  
  
-   L'option de synchronisation Web pour la réplication de fusion. Pour plus d’informations, voir [Web Synchronization for Merge Replication](../../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 Tous les types de réplication [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peuvent répliquer des données via un réseau privé virtuel (VPN), mais vous devrez plutôt utiliser la synchronisation Web si vous utilisez une réplication de fusion.  
  
### La réplication reprend-elle si une connexion est supprimée ?  
 Oui. Le traitement de la réplication reprend là où il s'est interrompu si une connexion est supprimée. Si vous utilisez une réplication de fusion sur un réseau non fiable, envisagez d'utiliser des enregistrements logiques qui garantissent que les modifications liées sont traitées en tant qu'unité. Pour plus d’informations, consultez [modifications du groupe de lignes associées avec les enregistrements logiques](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
### La réplication fonctionne-t-elle sur les connexions à faible bande passante ? Utilise-t-elle la compression ?  
 Oui, la réplication fonctionne sur les connexions à faible bande passante. Pour les connexions via TCP/IP, elle utilise la compression fournie par le protocole mais ne fournit pas de compression supplémentaire. Pour les connexions à synchronisation Web via HTTPS, elle utilise la compression fournie par le protocole ainsi qu'une compression supplémentaire des fichiers XML utilisés pour répliquer les modifications.  
  
## Noms d'accès et propriété d'objet  
  
### Les noms d'accès et mots de passe sont-ils répliqués ?  
 Non. Vous pourriez créer un package DTS pour transférer les noms d'accès et mots de passe d'un serveur de publication sur un ou plusieurs abonnés.  
  
### Que sont les schémas et comment sont-ils répliqués ?  
 À commencer par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], *schéma* a deux significations :  
  
-   La définition d'un objet, par exemple une instruction CREATE TABLE. Par défaut, la réplication copie les définitions de tous les objets répliqués sur l'Abonné.  
  
-   L’espace de noms dans lequel un objet est créé : \< base de données>. \< schéma>. \< objet>. Les schémas sont définis à l'aide de l'instruction CREATE SCHEMA.  
  
-   La réplication fonctionne par défaut de la façon suivante dans l'Assistant Nouvelle publication quant aux schémas et à la propriété des objets :  
  
-   Pour les articles de publications de fusion d'un niveau de compatibilité de 90 ou supérieur, les publications d'instantané et les publications transactionnelles : par défaut, le propriétaire de l'objet sur l'Abonné est le même que le propriétaire de l'objet correspondant sur le serveur de publication. Si les schémas propriétaires des objets n'existent pas sur l'Abonné, ils sont créés automatiquement.  
  
-   Pour les articles de publications de fusion d'un niveau de compatibilité inférieur à 90 : par défaut, le propriétaire est laissé vide et spécifié comme **dbo** pendant la création de l'objet sur l'Abonné.  
  
-   Pour les articles des publications Oracle : par défaut, le propriétaire est spécifié comme **dbo**.  
  
-   Pour les articles de publications utilisant les instantanés en mode caractère (utilisées pour les abonnés non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et les abonnés [!INCLUDE[ssEW](../../../includes/ssew-md.md)]) : le propriétaire est laissé vide par défaut. Le propriétaire prend les valeurs par défaut du propriétaire associé au compte utilisé par l'Agent de distribution ou l'Agent de fusion pour se connecter à l'Abonné.  
  
 Le propriétaire de l’objet peut être modifié via le **Propriétés de l’Article - \<***Article***>** boîte de dialogue et par le biais de procédures stockées : **sp_addarticle**, **sp_addmergearticle**, **sp_changearticle**, et **sp_changemergearticle**. Pour plus d’informations, consultez [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md), [définir un Article](../../../relational-databases/replication/publish/define-an-article.md), et [Afficher et modifier les propriétés d’Article](../../../relational-databases/replication/publish/view-and-modify-article-properties.md).  
  
### Comment configurer les demandes sur la base de données d'abonnement afin qu'elles correspondent aux demandes sur la base de données de publication ?  
 Par défaut, la réplication n'exécute pas d'instructions GRANT sur la base de données d'abonnement. Si vous voulez que les autorisations sur la base de données d'abonnement correspondent à celles de la base de données de publication, utilisez une des méthodes suivantes :  
  
-   Exécutez les instructions GRANT directement sur la base de données d'abonnement.  
  
-   Utilisez un script après l'instantané pour exécuter les instructions. Pour plus d’informations, consultez [exécuter des Scripts avant et après l’application de capture instantanée](../../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Utilisez la procédure stockée [sp_addscriptexec](../../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md) pour exécuter les instructions.  
  
### Qu'advient-il des autorisations accordées dans une base de données d'abonnement si un abonnement est réinitialisé ?  
 Par défaut, les objets sur l'Abonné sont supprimés et recréés lorsqu'un abonnement est réinitialisé, ce qui entraîne la suppression de toutes les autorisations accordées à ces objets. Il existe deux moyens de gérer cela :  
  
-   Appliquer à nouveau les demandes après la réinitialisation à l'aide des techniques décrites dans la section précédente.  
  
-   Spécifier de ne pas supprimer les objets lorsque l'abonnement est réinitialisé. Avant la réinitialisation, vous pouvez au choix :  
  
    -   Exécutez [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) ou [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Spécifiez la valeur 'pre_creation_cmd' (**sp_changearticle**) ou « pre_creation_command » (**sp_changemergearticle**) pour le paramètre **@property** et une valeur de 'none', 'delete' ou 'truncate' du paramètre **@value**.  
  
    -   Dans la **Propriétés de l’Article - \< Article>** boîte de dialogue de le **l’objet de Destination** sélectionnez une valeur de **conserver l’objet existant inchangé**, **Supprimer des données. Si l’article possède un filtre de lignes, supprimez uniquement les données qui correspondent au filtre.** ou **tronquer toutes les données dans l’objet existant** pour l’option **Action si le nom est en cours d’utilisation**. Pour plus d’informations sur l’accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés de la Publication](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
## Maintenance de la base de données  
  
### Pourquoi ne puis-je pas exécuter TRUNCATE TABLE sur une table publiée ?  
 TRUNCATE TABLE est une opération non journalisée qui n'exécute pas de déclencheurs. Cette opération n'est pas autorisée, car la réplication ne peut assurer le suivi des modifications engendrées par cette opération : la réplication transactionnelle assure le suivi des modifications via le journal des transactions, la réplication de fusion via des déclencheurs sur les tables publiées.  
  
### Quel est l'effet de l'exécution d'une commande d'insertion en bloc sur une base de données répliquée ?  
 Pour la réplication transactionnelle, les insertions en bloc sont suivies et répliquées comme les autres insertions. Pour la réplication de fusion, vous devez vérifier que les métadonnées de suivi des modifications sont correctement mises à jour.  
  
### Existe-t-il des règles de réplication pour l'enregistrement et la restauration ?  
 Oui. Il existe de nombreuses règles spécifiques pour les bases de données impliquées dans une réplication. Pour plus d’informations, consultez [sauvegarder et restaurer les bases de données répliquées](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md).  
  
### La réplication affecte-t-elle la taille du journal des transactions ?  
 La réplication de fusion et la réplication d'instantané n'affectent pas la taille du journal des transactions, contrairement à la réplication transactionnelle. Si une base de données comprend une ou plusieurs publications transactionnelles, le journal n'est pas tronqué tant que toutes les transactions relatives aux publications n'ont pas été remises à la base de données de distribution. Si la taille du journal des transactions devient trop importante et que l'Agent de lecture du journal s'exécute de manière planifiée, envisagez de réduire l'intervalle entre les exécutions. Ou, définissez-le pour qu'il s'exécute en mode continu. S'il est paramétré pour s'exécuter en mode continu (par défaut), vérifiez qu'il fonctionne. Pour plus d’informations sur la vérification du statut de l’Agent de lecture du journal, consultez [afficher des informations et effectuer des tâches pour les Agents associés à une Publication & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md).  
  
 De plus, si vous avez défini l'option « sync with backup » sur la base de données de publication ou la base de données de distribution, le journal des transactions n'est pas tronqué tant que toutes les transactions ne sont pas sauvegardées. Si la taille du journal des transactions devient trop importante et que cette option est définie, envisagez de réduire l'intervalle entre les enregistrements du journal des transactions. Pour plus d’informations sur la sauvegarde et restauration des bases de données impliquées dans la réplication transactionnelle, consultez [stratégies de sauvegarde et restauration de capture instantanée et la réplication transactionnelle](../../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
### Comment puis-je reconstruire les index ou les tables dans des bases de données répliquées ?  
 Il existe différents mécanismes pour la reconstruction d'index. Ils peuvent tous être utilisés sans règle spécifique à la réplication, à l'exception suivante près : des clés primaires sont nécessaires sur les tables dans les publications transactionnelles, vous ne pouvez donc pas supprimer et recréer de clés primaires sur ces tables.  
  
### Comment puis-je ajouter ou modifier des index sur des bases de données de publication ou d'abonnement ?  
 Les index peuvent être ajoutés sur le serveur de publication ou sur les abonnés sans règle spécifique à la réplication (sachez que les index peuvent affecter les performances). CREATE INDEX et ALTER INDEX ne sont pas répliqués, donc si par exemple vous ajoutez ou modifiez un index sur le serveur de publication, vous devez effectuer le même ajout ou la même modification sur l'Abonné si vous souhaitez qu'il ou qu'elle soit prise en compte.  
  
### Comment puis-je déplacer ou renommer des fichiers pour des bases de données impliquées dans une réplication ?  
 Dans les versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], le déplacement ou le changement de noms de fichiers de base de données nécessitait le détachement et le rattachement de la base de données. Comme une base de données répliquée ne peut pas être détachée, la réplication a d'abord du être supprimée de ces bases de données. Avec [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], vous pouvez déplacer ou renommer les fichiers sans détachement ou rattachement de la base de données, sans aucune incidence sur la réplication. Pour plus d’informations sur le déplacement et renommer les fichiers, consultez la page [ALTER DATABASE & #40 ; Transact-SQL & #41 ;](../../../t-sql/statements/alter-database-transact-sql.md).  
  
### Comment puis-je supprimer une table en cours de réplication ?  
 Tout d’abord supprimer l’article de la publication à l’aide [sp_droparticle](../../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md), [sp_dropmergearticle](../../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md), ou **Propriétés de la Publication - \< Publication>** boîte de dialogue zone, puis supprimez-le de la base de données à l’aide `DROP <Object>`. Vous ne pouvez pas supprimer d'articles d'un instantané ou de publications transactionnelles après avoir ajouté les abonnements, vous devez d'abord supprimer les abonnements. Pour plus d’informations, consultez [Ajouter et supprimer des Articles de Publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
### Comment puis-je ajouter ou supprimer des colonnes sur une table publiée ?  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge une large variété de modifications de schéma sur les objets publiés, y compris l'ajout et la suppression de colonnes. Par exemple, si vous exécutez ALTER TABLE … DROP COLUMN sur le serveur de publication, l’instruction est répliquée vers les abonnés, puis exécutée pour supprimer la colonne. Les abonnés exécutant des versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] prennent en charge Ajout et suppression de colonnes dans les procédures stockées [sp_repladdcolumn](../../../relational-databases/system-stored-procedures/sp-repladdcolumn-transact-sql.md) et [sp_repldropcolumn](../../../relational-databases/system-stored-procedures/sp-repldropcolumn-transact-sql.md). Pour plus d’informations, consultez [apporter des modifications de schéma sur les bases de données de Publication](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
## Maintenance de réplication  
  
### Comment puis-je déterminer si les données sur les abonnés sont synchronisées avec celles du serveur de publication ?  
 Utilisez la validation. La validation fournit un rapport sur la synchronisation ou non de l'Abonné avec le serveur de publication. Pour plus d’informations, consultez [valider les données répliquées](../../../relational-databases/replication/validate-replicated-data.md). La validation ne fournit pas d'informations sur les lignes non correctement synchronisées, à l'inverse de l'utilitaire [tablediff utility](../../../tools/tablediff-utility.md) .  
  
### Comment puis-je ajouter une table à une publication existante ?  
 Il n'est pas nécessaire d'arrêter l'activité sur les bases de données de publication ou d'abonnement pour ajouter une table (ou un autre objet). Ajouter une table à une publication via le **Propriétés de la Publication - \< Publication>** boîte de dialogue ou les procédures stockées [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) et [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Pour plus d’informations, consultez [Ajouter et supprimer des Articles de Publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
### Comment puis-je supprimer une table d'une publication ?  
 Supprimer une table de la publication à l’aide [sp_droparticle](../../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md), [sp_dropmergearticle](../../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md), ou **Propriétés de la Publication - \< Publication>** boîte de dialogue. Vous ne pouvez pas supprimer d'articles d'un instantané ou de publications transactionnelles après avoir ajouté les abonnements, vous devez d'abord supprimer les abonnements. Pour plus d’informations, consultez [Ajouter et supprimer des Articles de Publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
### Quelles actions nécessitent de réinitialiser les abonnements ?  
 Il existe de nombreuses modifications d'articles et de publications qui nécessitent de réinitialiser les abonnements. Pour plus d’informations, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
### Quelles actions entraînent l'invalidation d'instantanés ?  
 Il existe de nombreuses modifications d'articles et de publications qui invalident les instantanés et nécessitent de générer un nouvel instantané. Pour plus d’informations, consultez [Publication de modification et les propriétés de l’Article](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
### Comment puis-je supprimer une réplication ?  
 Les actions nécessaires à la suppression de la réplication d'une base de données varient suivant que la base de données ait servi de base de données de publication, de base de données d'abonnement, ou des deux à la fois.  
  
### Comment puis-je déterminer s'il existe des transactions ou des lignes à répliquer ?  
 Pour la réplication transactionnelle, utilisez les procédures stockées ou l'onglet **Commandes non distribuées** du Moniteur de réplication. Pour plus d’informations, consultez [commandes répliquées de vue et d’autres informations dans la base de données de Distribution & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/monitor/view replicated commands and information in distribution database.md) et [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
 La réplication de fusion, utilisez la procédure stockée **sp_showpendingchanges**. Pour plus d’informations, consultez [sp_showpendingchanges & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md).  
  
### L'Agent de distribution est-il en retard ? Dois-je réinitialiser ?  
 Utilisez le **sp_replmonitorsubscriptionpendingcmds** procédure stockée ou la **commandes non distribuées** onglet du moniteur de réplication. La procédure stockée et l'onglet affichent :  
  
-   Nombre de commandes dans la base de données de distribution qui n'ont pas été distribuées à l'abonné sélectionné. Une commande est constituée d'une instruction DML (Data Manipulation Language) Transact-SQL ou d'une instruction DDL (Data Definition Language).  
  
-   Délai estimé de distribution des commandes à l'Abonné. Si cette valeur est supérieure au délai nécessaire pour générer et appliquer un instantané à l'Abonné, réinitialisez l'Abonné. Pour plus d’informations, consultez [Réinitialiser les abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
 Pour plus d’informations, consultez [sp_replmonitorsubscriptionpendingcmds & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-replmonitorsubscriptionpendingcmds-transact-sql.md) et [afficher des informations et effectuer des tâches pour les Agents associés à un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Réplication et autres fonctionnalités de base de données  
  
### La réplication fonctionne-t-elle conjointement avec la copie des journaux et la mise en miroir de bases de données ?  
 Oui. Pour plus d’informations, consultez [l’envoi de journaux et la réplication & #40 ; SQL Server & #41 ;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md) et [la mise en miroir de base de données et réplication & #40 ; SQL Server & #41 ;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
### La réplication fonctionne-t-elle conjointement avec le clustering ?  
 Oui. Aucune règle spécifique n'est nécessaire car toutes les données sont stockées sur un ensemble de disques sur le cluster.  
  
## Voir aussi  
 [Administration & #40 ; Réplication & #41 ;](../../../relational-databases/replication/administration/administration-replication.md)   
 [Méthodes conseillées pour l'administration de la réplication](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)  
  
  