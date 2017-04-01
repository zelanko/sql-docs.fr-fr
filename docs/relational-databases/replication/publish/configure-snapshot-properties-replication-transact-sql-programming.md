---
title: "Configurer les propri&#233;t&#233;s d&#39;instantan&#233; (programmation Transact-SQL de la r&#233;plication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "captures instantanées [réplication SQL Server], propriétés"
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Configurer les propri&#233;t&#233;s d&#39;instantan&#233; (programmation Transact-SQL de la r&#233;plication)
  Les propriétés d'instantané peuvent être définies et modifiées par programme à l'aide de procédures stockées de réplication qui dépendent du type de publication.  
  
### Pour configurer les propriétés d'instantané lors de la création d'une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication, exécutez [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md). Spécifiez un nom de publication pour **@publication**, une valeur **instantané** ou **continue** pour **@repl_freq**, et un ou plusieurs des paramètres liés aux suivants :  
  
    -   **@alt_snapshot_folder** -spécifier un chemin d’accès si la capture instantanée pour cette publication est accessible à partir de cet emplacement à la place ou en plus du dossier d’instantanés par défaut.  
  
    -   **@compress_snapshot** -spécifier la valeur **true** si les fichiers d’instantanés dans le dossier de captures instantanées de remplacement sont compressés dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] format de fichier CAB.  
  
    -   **@pre_snapshot_script** -Spécifiez le nom de fichier et le chemin d’accès complet d’un **.sql** fichier sera exécuté sur l’abonné lors de l’initialisation avant de l’instantané initial est appliqué.  
  
    -   **@post_snapshot_script** -Spécifiez le nom de fichier et le chemin d’accès complet d’un **.sql** fichier sera exécuté sur l’abonné lors de l’initialisation après la capture instantanée initiale est appliquée.  
  
    -   **@snapshot_in_defaultfolder** -spécifier la valeur **false** Si l’instantané est disponible uniquement dans un emplacement non définis par défaut.  
  
     Pour plus d’informations sur la création de publications, consultez [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### Pour configurer les propriétés d'instantané lors de la création d'une publication de fusion  
  
1.  Sur le serveur de publication, exécutez [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Spécifiez un nom de publication pour **@publication**, une valeur **instantané** ou **continue** pour **@repl_freq**, et un ou plusieurs des paramètres liés aux suivants :  
  
    -   **@alt_snapshot_folder** -spécifier un chemin d’accès si la capture instantanée pour cette publication est accessible à partir de cet emplacement à la place ou en plus du dossier d’instantanés par défaut.  
  
    -   **@compress_snapshot** -spécifier la valeur **true** si les fichiers d’instantanés dans le dossier de captures instantanées de remplacement sont compressés au format de fichier CAB.  
  
    -   **@pre_snapshot_script** -Spécifiez le nom de fichier et le chemin d’accès complet d’un **.sql** fichier sera exécuté sur l’abonné lors de l’initialisation avant de l’instantané initial est appliqué.  
  
    -   **@post_snapshot_script** -Spécifiez le nom de fichier et le chemin d’accès complet d’un **.sql** fichier sera exécuté sur l’abonné lors de l’initialisation après la capture instantanée initiale est appliquée.  
  
    -   **@snapshot_in_defaultfolder** -spécifier la valeur **false** Si l’instantané est disponible uniquement dans un emplacement non définis par défaut.  
  
2.  Pour plus d’informations sur la création de publications, consultez [créer une Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
### Pour modifier les propriétés d'instantané d'une publication transactionnelle ou d'instantané existante  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md). Spécifiez la valeur **1** pour **@force_invalidate_snapshot** et une de ces valeurs pour **@property**:  
  
    -   **alt_snapshot_folder** -également spécifier un nouveau chemin d’accès au dossier de captures instantanées de remplacement **@value**.  
  
    -   **compress_snapshot** -également spécifier une valeur **true** ou **false** pour **@value** pour indiquer si les fichiers de capture instantanée dans le dossier de captures instantanées de remplacement sont compressés au format de fichier CAB.  
  
    -   **pre_snapshot_script** - également pour **@value** spécifier le nom de fichier et le chemin d’accès complet d’un **.sql** fichier sera exécuté sur l’abonné lors de l’initialisation avant de l’instantané initial est appliqué.  
  
    -   **post_snapshot_script** - également pour **@value** spécifier le nom de fichier et le chemin d’accès complet d’un **.sql** fichier sera exécuté sur l’abonné lors de l’initialisation après la capture instantanée initiale est appliquée.  
  
    -   **snapshot_in_defaultfolder** -également spécifier une valeur **true** ou **false** pour indiquer si l’instantané est disponible uniquement dans un emplacement non définis par défaut.  
  
2.  (Facultatif) Sur le serveur de publication sur la base de données de publication, exécutez [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md). Spécifiez **@publication** et un ou plusieurs des paramètres d’informations d’identification de planification ou de sécurité en cours de modification.  
  
    > [!IMPORTANT]  
    >  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
3.  Exécuter le [Agent de capture instantanée de réplication](../../../relational-databases/replication/agents/replication-snapshot-agent.md) à partir de l’invite de commandes ou démarrer le travail de l’Agent de capture instantanée pour générer un nouvel instantané. Pour plus d'informations, voir [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
### Pour modifier les propriétés d'instantané d'une publication de fusion existante  
  
1.  Sur le serveur de publication sur la base de données de publication, exécutez [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md). Spécifiez la valeur **1** pour **@force_invalidate_snapshot** et une de ces valeurs pour **@property**:  
  
    -   **alt_snapshot_folder** -également spécifier un nouveau chemin d’accès au dossier de captures instantanées de remplacement **@value**.  
  
    -   **compress_snapshot** -également spécifier une valeur **true** ou **false** pour **@value** pour indiquer si les fichiers de capture instantanée dans le dossier de captures instantanées de remplacement sont compressés au format de fichier CAB.  
  
    -   **pre_snapshot_script** - également pour **@value** spécifier le nom de fichier et le chemin d’accès complet d’un **.sql** fichier sera exécuté sur l’abonné lors de l’initialisation avant de l’instantané initial est appliqué.  
  
    -   **post_snapshot_script** - également pour **@value** spécifier le nom de fichier et le chemin d’accès complet d’un **.sql** fichier sera exécuté sur l’abonné lors de l’initialisation après la capture instantanée initiale est appliquée.  
  
    -   **snapshot_in_defaultfolder** -également spécifier une valeur **true** ou **false** pour indiquer si l’instantané est disponible uniquement dans un emplacement non définis par défaut.  
  
2.  Exécuter le [Agent de capture instantanée de réplication](../../../relational-databases/replication/agents/replication-snapshot-agent.md) à partir de l’invite de commandes ou démarrer le travail de l’Agent de capture instantanée pour générer un nouvel instantané. Pour plus d'informations, voir [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
## Exemple  
 Cet exemple crée une publication qui utilise un dossier d'instantanés de remplacement et un instantané compressé.  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../relational-databases/replication/codesnippet/tsql/configure-snapshot-prope_1.sql)]  
  
## Voir aussi  
 [Autres emplacements du dossier d'instantané](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Instantanés compressés](../../../relational-databases/replication/compressed-snapshots.md)   
 [Exécuter des scripts avant et après l'application de l'instantané](../../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [Concepts liés aux procédures stockées système de réplication](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Transférer des instantanés via FTP](../../../relational-databases/replication/transfer-snapshots-through-ftp.md)   
 [Modifier les propriétés des publications et des articles](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)  
  
  