---
title: "Propri&#233;t&#233;s de l&#39;article - &lt;Article&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.articleproperties.f1"
helpviewer_keywords: 
  - "boîte de dialogue Propriétés de l'article"
ms.assetid: 6dd601a4-1233-43d9-a9f0-bc8d84e5d188
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Propri&#233;t&#233;s de l&#39;article - &lt;Article&gt;
  Le **Propriétés de l’Article** boîte de dialogue est disponible à partir de l’Assistant Nouvelle Publication et **Propriétés de la Publication** boîte de dialogue. Elle permet d'afficher et de définir les propriétés de tous les types d'articles. Certaines propriétés peuvent être définies uniquement lors de la création de la publication, et d'autres uniquement si la publication n'a pas d'abonnements actifs. Les propriétés qui ne peuvent pas être définies s'affichent en lecture seule.  
  
> [!NOTE]  
>  Après qu'une publication a été créée, certaines modifications de propriétés nécessitent un nouvel instantané. Si une publication dispose d'abonnements, ces abonnements pourraient devoir alors être réinitialisés selon les modifications que vous avez apportées. Pour plus d’informations, consultez [Publication de modification et les propriétés de l’Article](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
 Chaque propriété de le **Propriétés de l’Article** boîte de dialogue comporte une description. Cliquez sur une propriété pour afficher sa description dans la partie inférieure de la boîte de dialogue. Cette rubrique fournit des informations sur diverses propriétés, Les propriétés sont regroupées selon les catégories suivantes :  
  
-   Propriétés qui s'appliquent à toutes les publications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Propriétés qui s'appliquent aux publications transactionnelles de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Propriétés qui s'appliquent aux publications de fusion.  
  
-   Propriétés qui s'appliquent aux publications transactionnelles et d'instantané des serveurs de publication Oracle.  
  
## Options pour toutes les publications  
 **Copier les schémas de partitionnement de table** et **Copier les schémas de partition d’index**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] le partitionnement de table a introduit et partitionnement d’index, qui ne sont pas liées à la réplication de partitionnement offre filtres par ligne et colonne. Le **Copier les schémas de partitionnement de table** et **Copier les schémas de partition d’index** options spécifient si les schémas de partition doivent être copiés vers l’abonné. Pour plus d’informations sur le partitionnement, consultez [Tables partitionnées et des index](../../relational-databases/partitions/partitioned-tables-and-indexes.md).  
  
 **Convertir les types de données**  
 Détermine si les types de données définis par l'utilisateur doivent être convertis en types de données de base lors de la création d'objets au niveau de l'Abonné. Les types de données définis par l'utilisateur incluent les types CLR introduits dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Spécifiez la valeur **True** Si vous répliquez ces types de données pour les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; Cela garantit qu’ils peuvent être traités correctement sur l’abonné.  
  
 **Créer des schémas sur l'Abonné**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] a introduit des schémas qui sont définies à l’aide de l’instruction CREATE SCHEMA. Un schéma est le propriétaire d’un objet ; elle est utilisée dans un nom en plusieurs parties, telles que \< base de données>. \< schéma>. \< objet>. Si la base de données contient des objets appartenant à des schémas autres que DBO, la réplication peut créer ces schémas au niveau de l'Abonné pour pouvoir créer des objets publiés.  
  
 Si vous répliquez les données vers des versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] :  
  
-   Définissez cette option sur **False**, car les versions antérieures ne prennent pas en charge CREATE SCHEMA.  
  
-   Pour chaque schéma, ajoutez un utilisateur à la base de données d'abonnement ayant le même nom que le schéma.  
  
 **Convertir XML en NTEXT**, **des types de données de convertir un MAX en NTEXT et IMAGE**, **convertir les nouveaux datetime en NVARCHAR**, **convertir filestream en types de données MAX**, **convertir CLR volumineux en types de données MAX**, **convertir hierarchyId en types de données MAX**, et **convertir spatial en types de données MAX**.  
 Indique si les types de données et les attributs doivent être convertis comme indiqué. Spécifiez la valeur **True** Si vous répliquez ces types de données pour les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cela garantit qu'ils pourront être traités correctement sur l'Abonné.  
  
 **Nom de l'objet de destination**  
 Nom de l'objet créé dans la base de données d'abonnement. Cette option ne peut pas être modifiée pour les articles des publications activées pour la réplication transactionnelle d'égal à égal.  
  
 **Propriétaire de l'objet de destination**  
 Schéma sous lequel l'objet est créé dans la base de données d'abonnement. Le schéma par défaut est le schéma auquel l'objet appartient dans la base de données de publication, avec les exceptions suivantes :  
  
-   Pour les articles de publications de fusion d'un niveau de compatibilité inférieur à 90 : par défaut, le propriétaire est laissé vide et spécifié comme **dbo** pendant la création de l'objet sur l'Abonné.  
  
-   Pour les articles des publications Oracle : par défaut, le propriétaire est spécifié comme **dbo**.  
  
-   Pour les articles de publications utilisant les instantanés en mode caractère (utilisées pour les abonnés non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les abonnés [!INCLUDE[ssEW](../../includes/ssew-md.md)]) : le propriétaire est laissé vide par défaut. Le propriétaire prend les valeurs par défaut du propriétaire associé au compte utilisé par l'Agent de distribution ou l'Agent de fusion pour se connecter à l'Abonné.  
  
 Cette option ne peut pas être modifiée pour les articles des publications activées pour la réplication transactionnelle d'égal à égal.  
  
 **Gérer automatiquement les plages d'identité**  
 Par défaut, la réplication gère toutes les colonnes d'identité au niveau du serveur de publication et de chaque abonné. Chaque nœud de réplication se voit attribuer une plage de valeurs d’identité (spécifiée avec le **taille de la plage Publisher** et **taille de la plage abonné** options) pour vous assurer qu’une valeur donnée est utilisée uniquement sur un nœud. Pour plus d’informations, consultez [répliquer les colonnes d’identité](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
## Options des publications transactionnelles  
 **Copie des procédures stockées INSERT, UPDATE et DELETE**  
 If, dans le **remise d’instruction** section de cette boîte de dialogue, vous sélectionnez pour utiliser des procédures stockées pour propager les modifications aux abonnés (valeur par défaut), indiquez si vous souhaitez copier les procédures pour chaque abonné. Si vous sélectionnez **False**, vous devez copier manuellement les procédures ou l’Agent de Distribution échoue lorsque vous essayez de distribuer les modifications.  
  
 **Remise d'instruction**  
 Les options de cette section s'appliquent à toutes les tables, notamment les vues indexées répliquées en tant que tables. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d’utiliser les options par défaut, sauf si votre application requiert des fonctionnalités différentes. Par défaut, la réplication transactionnelle propage les modifications vers les abonnés via un groupe de procédures stockées installées sur chaque abonné. Lorsqu'une insertion, une mise à jour ou une suppression se produit dans une table sur le serveur de publication, l'opération est convertie en appel à une procédure stockée au niveau de l'Abonné.  
  
 La **instruction de remise** options spécifient s’il faut utiliser une procédure stockée, et si, par conséquent, le format doit être utilisé pour les paramètres passés à la procédure. Le **procédure stockée** options permettent d’utiliser des procédures que la réplication automatiquement crée ou substituer des procédures que vous avez créé.  
  
 Pour plus d’informations, consultez [spécifier comment les modifications sont propagées des Articles transactionnels](../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
 **Répliquer**  
 Cette option s'applique uniquement aux procédures stockées. Elle permet d'indiquer si vous voulez répliquer la définition de la procédure stockée (instruction CREATE PROCEDURE) ou son exécution. Si vous répliquez l'exécution de la procédure, la définition de la procédure est répliquée vers l'Abonné lors de l'initialisation de l'abonnement. Lorsque la procédure est exécutée sur le serveur de publication, la réplication exécute la procédure correspondante au niveau de l'Abonné. Ceci peut améliorer les performances de manière significative lorsque des opérations de traitement par lot volumineuses sont exécutées. Pour plus d’informations, voir [Publishing Stored Procedure Execution in Transactional Replication](../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
## Options des publications de fusion  
 Le **Propriétés de l’Article** boîte de dialogue pour les publications de fusion comporte deux onglets : **propriétés** et **résolution**.  
  
### Onglet Propriétés  
 **Direction de la synchronisation**  
 Indique si les modifications peuvent être téléchargées depuis les abonnés qui utilisent le type d'abonnement client :  
  
-   **Bidirectionnel** (la valeur par défaut) : modifications peuvent être téléchargées à l’abonné et téléchargées vers le serveur de publication.  
  
-   **Téléchargement seul pour l’abonné, interdire les modifications de l’abonné**: modifications peuvent être téléchargées vers l’abonné, mais ils ne peuvent pas être téléchargés vers le serveur de publication. Les déclencheurs empêchent les modifications au niveau de l'Abonné.  
  
-   **Téléchargement seul pour l’abonné, autoriser les modifications de l’abonné**: modifications peuvent être téléchargées vers l’abonné, mais ils ne peuvent pas être téléchargés vers le serveur de publication.  
  
 Pour plus d’informations, consultez [optimiser les performances de réplication de fusion avec des Articles avec](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 **Options de la partition**  
 Définit le type des partitions que crée un filtre paramétrable. Pour plus d’informations, consultez la section « Définition des options de partition » de [filtres de lignes paramétrable](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **Niveau de suivi**  
 Indique si les modifications d'une même ligne ou d'une même colonne doivent être traitées sous la forme d'un conflit.  
  
 **Vérifier l’autorisation INSERT**, **vérifier l’autorisation UPDATE**, et **vérifier l’autorisation DELETE**  
 Permet d'indiquer si vous voulez vérifier au cours de la synchronisation si la connexion de l'Abonné dispose de l'autorisation INSERT, UPDATE ou DELETE sur les tables publiées dans la base de données de publication. La valeur par défaut est **False** car la réplication de fusion ne nécessite pas de ces autorisations à accorder ; l’accès aux tables publiées est contrôlé via la liste d’accès Publication (PAL). Pour plus d’informations sur la publication, consultez [sécuriser le serveur de publication](../../relational-databases/replication/security/secure-the-publisher.md).  
  
 Vous pouvez demander la vérification des autorisations si vous voulez autoriser des abonnés à télécharger certaines modifications des données publiées. Vous pouvez, par exemple, ajouter un abonné à une liste d'accès à la publication, et ne fournir à l'abonné aucune autorisation sur les tables de la base de données de publication. Vous pouvez ensuite définir les autorisations DELETE en leur affectant **True**: l’abonné serait en mesure de télécharger les insertions et mises à jour, mais pas les suppressions.  
  
 **UPDATE multicolonne**  
 Lorsque la réplication de fusion effectue une mise à jour, elle met à jour toutes les colonnes modifiées dans une instruction UPDATE et réinitialise les valeurs d'origine des colonnes non modifiées. Dans ce cas, l'alternative consiste à émettre plusieurs instructions UPDATE avec une instruction UPDATE pour chaque colonne modifiée. L’instruction UPDATE multicolonne est généralement plus efficace, mais vous devez envisager l’option **False** si les déclencheurs de la table sont définies pour répondre aux mises à jour de certaines colonnes, et qu’ils répondent incorrectement, car ces colonnes sont réinitialisées lorsque des mises à jour se produisent.  
  
> [!IMPORTANT]  
>  Cette option est déconseillée et ne figurera plus dans les prochaines versions  
  
### Onglet Résolveur  
 **Utiliser le résolveur par défaut**  
 Si vous sélectionnez le résolveur par défaut, les conflits sont résolus en fonction de la priorité affectée à chaque abonné ou de la première modification écrite sur le serveur de publication, selon le type d'abonnement utilisé. Pour plus d'informations, consultez [Detect and Resolve Merge Replication Conflicts](../../relational-databases/replication/merge/detect-and-resolve-merge-replication-conflicts.md).  
  
 **Utiliser un résolveur personnalisé (inscrit sur le serveur de distribution)**  
 Si vous décidez d'utiliser un résolveur d'article (fourni par [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou que vous avez écrit), vous devez sélectionner un résolveur dans la zone de liste. Pour plus d’informations, consultez [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
 Si le programme de résolution nécessite une entrée, spécifiez-le dans **Entrez les informations requises par le résolveur** zone de texte. Pour plus d’informations sur l’entrée nécessaire par [!INCLUDE[msCoName](../../includes/msconame-md.md)] résolveurs personnalisés, consultez [Microsoft résolveurs COM](../../relational-databases/replication/merge/microsoft-com-based-resolvers.md).  
  
 **Autoriser l'Abonné à résoudre les conflits de manière interactive au cours de la synchronisation à la demande**  
 Sélectionnez cette option si les abonnés utilisent la synchronisation à la demande (synchronisation par défaut de la réplication de fusion) et que vous voulez résoudre les conflits de manière interactive. Spécifiez la synchronisation à la demande sur le **calendrier de synchronisation** page de l’Assistant Nouvel abonnement. Pour résoudre les conflits de manière interactive, utilisez l'interface utilisateur Résolveur interactif. Pour plus d’informations, consultez [Interactive Conflict Resolution](../../relational-databases/replication/merge/interactive-conflict-resolution.md).  
  
 **Exiger la vérification d'une signature numérique avant la fusion**  
 Tous les résolveurs COM fournis par [!INCLUDE[msCoName](../../includes/msconame-md.md)] sont signés. Sélectionnez cette option pour vérifier que le résolveur est valide lors de la synchronisation.  
  
## Options des publications Oracle  
 Le **Propriétés de l’Article** boîte de dialogue pour les publications Oracle comporte deux onglets : **propriétés** et **le mappage de données**. Les publications Oracle ne prennent pas en charge toutes les propriétés que prennent en charge les publications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Considérations et Limitations pour les serveurs de publication Oracle](../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
### Onglet Propriétés  
 **Copie des procédures stockées INSERT, UPDATE et DELETE**  
 Si l’article se trouve dans une publication transactionnelle et, dans le **remise d’instruction** section de cette boîte de dialogue, vous sélectionnez pour utiliser des procédures stockées pour propager les modifications aux abonnés (valeur par défaut), indiquez si vous souhaitez copier les procédures pour chaque abonné. Si vous sélectionnez **False**, vous devez copier manuellement les procédures ou l’Agent de Distribution échoue lorsque vous essayez de distribuer les modifications.  
  
 **Propriétaire de l'objet de destination**  
 Si vous entrez une valeur autre que **dbo**:  
  
-   Pour les abonnés qui exécutent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou une version ultérieure, vous devez vérifier qu'un schéma est créé au niveau de l'Abonné ayant le même nom que la valeur que vous entrez. Pour plus d’informations, consultez [CREATE SCHEMA & #40 ; Transact-SQL & #41 ;](../../t-sql/statements/create-schema-transact-sql.md).  
  
-   Pour chaque abonné qui exécute des versions antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], pour chaque schéma, ajoutez un utilisateur à la base de données d'abonnement ayant le même nom que le schéma.  
  
 **Nom de l'espace disque logique**  
 Nom de l'espace disque logique dans lequel doivent être créées les tables de suivi des modifications de réplication sur l'instance du serveur Oracle. Pour plus d’informations, consultez [Gérer les espaces de stockage Oracle](../../relational-databases/replication/non-sql/manage-oracle-tablespaces.md).  
  
 **Remise d'instruction**  
 Les options de cette section s'appliquent à toutes les tables dans les publications transactionnelles. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d’utiliser les options par défaut, sauf si votre application requiert des fonctionnalités différentes. Par défaut, la réplication transactionnelle propage les modifications vers les abonnés via un groupe de procédures stockées installées sur chaque abonné. Lorsqu'une insertion, une mise à jour ou une suppression se produit dans une table sur le serveur de publication, l'opération est convertie en appel à une procédure stockée au niveau de l'Abonné.  
  
 La **instruction de remise** options spécifient s’il faut utiliser une procédure stockée, et si, par conséquent, le format doit être utilisé pour les paramètres passés à la procédure. Le **procédure stockée** options permettent d’utiliser des procédures que la réplication automatiquement crée ou substituer des procédures que vous avez créé.  
  
 Pour plus d’informations, consultez [spécifier comment les modifications sont propagées des Articles transactionnels](../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
### Onglet Mappage de données  
 **Nom de colonne**  
 Nom de la colonne du serveur de publication (en lecture seule).  
  
 **Type de données du serveur de publication**  
 Type de données Oracle de la colonne du serveur de publication (lecture seule). Le type de données peut être modifié uniquement directement dans la base de données Oracle. Pour plus d'informations, consultez votre documentation Oracle.  
  
 **Type de données de l'Abonné**  
 Type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auquel le type de données Oracle est associé lors de la réplication des données :  
  
-   Pour certains types de données, il existe uniquement une seule possibilité de mappage dans laquelle la colonne de la grille de propriétés est en lecture seule.  
  
-   Pour certains types, vous pouvez sélectionner plus d'un type. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'utiliser le mappage par défaut si l'application ne nécessite pas un mappage différent. Pour plus d'informations, voir [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d'une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Créer et appliquer l'instantané initial](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Réinitialiser un abonnement](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  