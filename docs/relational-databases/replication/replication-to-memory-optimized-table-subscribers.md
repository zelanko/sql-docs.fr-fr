---
title: "Abonn&#233;s &#224; la r&#233;plication de tables m&#233;moire optimis&#233;es | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/21/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a8e6bc7-433e-471d-b646-092dc80a2d1a
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Abonn&#233;s &#224; la r&#233;plication de tables m&#233;moire optimis&#233;es
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Les tables agissant comme des abonnés à la réplication de capture instantanée et à la réplication transactionnelle, à l’exclusion de la réplication transactionnelle d’égal à égal, peuvent être configurées en tant que tables mémoire optimisées. Les autres configurations de réplication ne sont pas compatibles avec les tables mémoire optimisées. Cette fonctionnalité est disponible à partir de la version [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
## <a name="two-configurations-are-required"></a>Deux configurations requises  
  
-   **Configurer la base de données de l’abonné pour prendre en charge la réplication vers des tables optimisées en mémoire**  
  
     Définir le **@memory_optimized** propriété **true**, à l’aide de [sp_addsubscription &#40 ; Transact-SQL &#41 ;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) ou [sp_changesubscription &#40 ; Transact-SQL &#41 ;](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md).  
  
-   **Configurer l’article pour prendre en charge la réplication vers des tables optimisées en mémoire**  
  
     Définissez la `@schema_option = 0x40000000000` option pour l’article à l’aide de [sp_addarticle &#40 ; Transact-SQL &#41 ;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) ou [sp_changearticle &#40 ; Transact-SQL &#41 ;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md).  
  
#### <a name="to-configure-a-memory-optimized-table-as-a-subscriber"></a>Pour configurer une table mémoire optimisée en tant qu’abonné  
  
1.  Créez une publication transactionnelle. Pour plus d’informations, voir [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Ajoutez des articles à la publication. Pour plus d'informations, voir [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
     Si la configuration à l’aide [!INCLUDE[tsql](../../includes/tsql-md.md)] définir le **@schema_option** paramètre de la **sp_addarticle** procédure stockée   
    **0x40000000000**.  
  
3.  Dans la fenêtre de propriétés d’article, définissez **Activer l’optimisation mémoire** sur **true**.  
  
4.  Démarrez le travail de l'Agent d'instantané pour générer l'instantané initial pour cette publication. Pour plus d’informations, voir [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
5.  Ensuite, créez un abonnement. Dans l’ **Assistant Nouvel abonnement** , définissez **Abonnement de mémoire optimisée** sur **true**.  
  
 Les tables mémoire optimisées doivent maintenant commencer à recevoir les mises à jour du serveur de publication.  
  
#### <a name="reconfigure-an-existing-transaction-replication"></a>Reconfigurer une réplication de transaction existante  
  
1.  Accédez aux propriétés d’abonnement dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] et définissez **Abonnement de mémoire optimisée** sur **true**. Les modifications ne sont appliquées qu’une fois l’abonnement réinitialisé.  
  
     Si la configuration à l’aide [!INCLUDE[tsql](../../includes/tsql-md.md)] définir le nouveau **@memory_optimized** paramètre de la **sp_addsubscription** une procédure stockée à la valeur true.  
  
2.  Accédez aux propriétés d’article d’une publication dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , puis définissez **Activer l’optimisation mémoire** sur true.  
  
     Si la configuration à l’aide [!INCLUDE[tsql](../../includes/tsql-md.md)] définir le **@schema_option** paramètre de la **sp_addarticle** procédure stockée   
    **0x40000000000**.  
  
3.  Les tables mémoire optimisées ne prennent pas en charge les index cluster. Pour que la réplication gère ces types d’index en les convertissant en index non cluster sur la destination, définissez **Convertir l’index cluster en index non-cluster pour l’article optimisé en mémoire** sur true.  
  
     Si la configuration à l’aide [!INCLUDE[tsql](../../includes/tsql-md.md)] définir le **@schema_option** paramètre de la **sp_addarticle** procédure stockée  **0x0000080000000000**.  
  
4.  Régénérez la capture instantanée.  
  
5.  Réinitialisez l’abonnement.  
  
## <a name="remarks-and-restrictions"></a>Remarques et restrictions  
 Seule la réplication transactionnelle monodirectionnelle est prise en charge. La réplication transactionnelle d'égal à égal n'est pas prise en charge.  
  
 Les tables mémoire optimisées ne peuvent pas être publiées.  
  
 Les tables de réplication sur le serveur de distribution ne peuvent pas être configurées comme des tables mémoire optimisées.  
  
 La réplication de fusion ne peut pas inclure des tables mémoire optimisées.  
  
 Sur l'abonné, les tables impliquées dans la réplication transactionnelle peuvent être configurées en tant que tables mémoire optimisées, mais les tables d'abonné doivent répondre aux exigences des tables mémoire optimisées. Cette fonction requiert les restrictions suivantes.  
 
-   Les tables répliquées en tables mémoire optimisées sur un abonné sont limitées aux types de données autorisés dans les tables mémoire optimisées. Pour plus d’informations, consultez [Types de données pris en charge pour l’OLTP en mémoire](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md).  
  
-   Pas toutes les fonctionnalités de Transact-SQL sont prises en charge avec les tables optimisées en mémoire. Consultez [Transact-SQL construit pas pris en charge par l’OLTP en mémoire](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) Pour plus d’informations.  
  
##  <a name="a-nameschemaa-modifying-a-schema-file"></a><a name="Schema"></a> Modification d’un fichier de schéma  
  
-   Si vous utilisez l'option de table mémoire optimisée `DURABILITY = SCHEMA_AND_DATA` , la table doit avoir un index de clé primaire non cluster.  
  
-   ANSI_PADDING doit être activé.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et les fonctionnalités de réplication](../../relational-databases/replication/replication-features-and-tasks.md)  
  
  