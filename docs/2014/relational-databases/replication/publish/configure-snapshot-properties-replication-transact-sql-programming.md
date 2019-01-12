---
title: Configurer les propriétés d’instantané (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server replication], properties
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b03dd7f886cee5816d591034d1be63ece45d8d1d
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54127880"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a>Configurer les propriétés d'instantané (programmation Transact-SQL de la réplication)
  Les propriétés d'instantané peuvent être définies et modifiées par programme à l'aide de procédures stockées de réplication qui dépendent du type de publication.  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a>Pour configurer les propriétés d'instantané lors de la création d'une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication, exécutez [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql). Spécifiez un nom de publication pour **@publication**, la valeur **snapshot** ou **continuous** pour **@repl_freq**, ainsi qu'un ou plusieurs des paramètres suivants, liés à l'instantané :  
  
    -   **@alt_snapshot_folder** – spécifiez un chemin d'accès si l'accès à l'instantané pour cette publication s'effectue à partir de cet emplacement à la place ou en plus du dossier d'instantanés par défaut.  
  
    -   **@compress_snapshot** – spécifiez la valeur **true** si les fichiers d'instantanés dans le dossier d'instantanés de remplacement sont compressés dans le format de fichier CAB de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .  
  
    -   **@pre_snapshot_script** – spécifiez le nom de fichier et le chemin d'accès complet d'un fichier **.sql** qui sera exécuté sur l'Abonné au cours de l'initialisation, avant que l'instantané initial soit appliqué.  
  
    -   **@post_snapshot_script** – spécifiez le nom de fichier et le chemin d'accès complet d'un fichier **.sql** qui sera exécuté sur l'Abonné au cours de l'initialisation, après l'application de l'instantané initial.  
  
    -   **@snapshot_in_defaultfolder** – spécifiez la valeur **false** si l'instantané est disponible uniquement dans un emplacement non défini par défaut.  
  
     Pour plus d'informations sur la création des publications, consultez [Create a Publication](create-a-publication.md).  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a>Pour configurer les propriétés d'instantané lors de la création d'une publication de fusion  
  
1.  Sur le serveur de publication, exécutez [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Spécifiez un nom de publication pour **@publication**, la valeur **snapshot** ou **continuous** pour **@repl_freq**, ainsi qu'un ou plusieurs des paramètres suivants, liés à l'instantané :  
  
    -   **@alt_snapshot_folder** – spécifiez un chemin d'accès si l'accès à l'instantané pour cette publication s'effectue à partir de cet emplacement à la place ou en plus du dossier d'instantanés par défaut.  
  
    -   **@compress_snapshot** – spécifiez la valeur **true** si les fichiers d'instantanés dans le dossier d'instantanés de remplacement sont compressés dans le format de fichier CAB.  
  
    -   **@pre_snapshot_script** – spécifiez le nom de fichier et le chemin d'accès complet d'un fichier **.sql** qui sera exécuté sur l'Abonné au cours de l'initialisation, avant que l'instantané initial soit appliqué.  
  
    -   **@post_snapshot_script** – spécifiez le nom de fichier et le chemin d'accès complet d'un fichier **.sql** qui sera exécuté sur l'Abonné au cours de l'initialisation, après l'application de l'instantané initial.  
  
    -   **@snapshot_in_defaultfolder** – spécifiez la valeur **false** si l'instantané est disponible uniquement dans un emplacement non défini par défaut.  
  
2.  Pour plus d'informations sur la création des publications, consultez [Create a Publication](create-a-publication.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a>Pour modifier les propriétés d'instantané d'une publication transactionnelle ou d'instantané existante  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql). Spécifiez la valeur **1** pour **@force_invalidate_snapshot** et l'une des valeurs suivantes pour **@property**:  
  
    -   **alt_snapshot_folder** – spécifiez également un nouveau chemin d'accès au dossier d'instantanés de remplacement pour **@value**.  
  
    -   **compress_snapshot** – spécifiez également la valeur **true** ou **false** pour **@value** pour indiquer si les fichiers d'instantanés stockés dans le dossier d'instantanés de remplacement sont compressés dans le format de fichier CAB.  
  
    -   **pre_snapshot_script** – spécifiez également pour **@value** le nom de fichier et le chemin d'accès complet d'un fichier **.sql** qui sera exécuté sur l'Abonné au cours de l'initialisation, avant que l'instantané initial soit appliqué.  
  
    -   **post_snapshot_script** – spécifiez également pour **@value** le nom de fichier et le chemin d'accès complet d'un fichier **.sql** qui sera exécuté sur l'Abonné au cours de l'initialisation, après l'application de l'instantané initial.  
  
    -   **snapshot_in_defaultfolder** – spécifiez également la valeur **true** ou **false** pour indiquer si l'instantané est disponible uniquement dans un emplacement non défini par défaut.  
  
2.  (Facultatif) Sur le serveur de publication, dans la base de données de publication, exécutez [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql). Spécifiez **@publication** et un ou plusieurs des paramètres de planification ou d'informations d'identification de sécurité en cours de modification.  
  
    > [!IMPORTANT]  
    >  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
3.  Exécutez l' [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) à partir de l'invite de commandes ou démarrez le travail de l'Agent d'instantané pour générer un nouvel instantané. Pour plus d’informations, voir [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a>Pour modifier les propriétés d'instantané d'une publication de fusion existante  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql). Spécifiez la valeur **1** pour **@force_invalidate_snapshot** et l'une des valeurs suivantes pour **@property**:  
  
    -   **alt_snapshot_folder** – spécifiez également un nouveau chemin d'accès au dossier d'instantanés de remplacement pour **@value**.  
  
    -   **compress_snapshot** – spécifiez également la valeur **true** ou **false** pour **@value** pour indiquer si les fichiers d'instantanés stockés dans le dossier d'instantanés de remplacement sont compressés dans le format de fichier CAB.  
  
    -   **pre_snapshot_script** – spécifiez également pour **@value** le nom de fichier et le chemin d'accès complet d'un fichier **.sql** qui sera exécuté sur l'Abonné au cours de l'initialisation, avant que l'instantané initial soit appliqué.  
  
    -   **post_snapshot_script** – spécifiez également pour **@value** le nom de fichier et le chemin d'accès complet d'un fichier **.sql** qui sera exécuté sur l'Abonné au cours de l'initialisation, après l'application de l'instantané initial.  
  
    -   **snapshot_in_defaultfolder** – spécifiez également la valeur **true** ou **false** pour indiquer si l'instantané est disponible uniquement dans un emplacement non défini par défaut.  
  
2.  Exécutez l' [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) à partir de l'invite de commandes ou démarrez le travail de l'Agent d'instantané pour générer un nouvel instantané. Pour plus d'informations, voir [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple crée une publication qui utilise un dossier d'instantanés de remplacement et un instantané compressé.  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubaltsnapshot.sql#sp_mergealtsnapshot)]  
  
## <a name="see-also"></a>Voir aussi  
 [Autres emplacements du dossier d’instantanés](../alternate-snapshot-folder-locations.md)   
 [Instantanés compressés](../compressed-snapshots.md)   
 [Exécuter des scripts avant et après l’application de l’instantané](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Transférer des instantanés via FTP](../transfer-snapshots-through-ftp.md)   
 [Modifier les propriétés des publications et des articles](change-publication-and-article-properties.md)  
  
  
