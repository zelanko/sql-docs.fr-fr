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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63021337"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a>Configurer les propriétés d'instantané (programmation Transact-SQL de la réplication)
  Les propriétés d'instantané peuvent être définies et modifiées par programme à l'aide de procédures stockées de réplication qui dépendent du type de publication.  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a>Pour configurer les propriétés d'instantané lors de la création d'une publication transactionnelle ou d'instantané  
  
1.  Sur le serveur de publication, exécutez [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql). Spécifiez un nom de **@publication**publication pour, la valeur **snapshot** ou **Continuous** pour **@repl_freq**et un ou plusieurs des paramètres d’instantané suivants :  
  
    -   **@alt_snapshot_folder**-Spécifiez un chemin d’accès si l’instantané de cette publication est accessible à partir de cet emplacement à la place ou en plus du dossier d’instantanés par défaut.  
  
    -   **@compress_snapshot**-Spécifiez la valeur **true** si les fichiers d’instantanés dans le dossier d’instantanés de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] remplacement sont compressés dans le format de fichier CAB.  
  
    -   **@pre_snapshot_script**-Spécifiez le nom de fichier et le chemin d’accès complet d’un fichier **. SQL** qui sera exécuté sur l’abonné au cours de l’initialisation, avant que l’instantané initial soit appliqué.  
  
    -   **@post_snapshot_script**-Spécifiez le nom de fichier et le chemin d’accès complet d’un fichier **. SQL** qui sera exécuté sur l’abonné au cours de l’initialisation après l’application de l’instantané initial.  
  
    -   **@snapshot_in_defaultfolder**-Spécifiez la valeur **false** si l’instantané est disponible uniquement à un emplacement autre que celui par défaut.  
  
     Pour plus d'informations sur la création des publications, consultez [Create a Publication](create-a-publication.md).  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a>Pour configurer les propriétés d'instantané lors de la création d'une publication de fusion  
  
1.  Sur le serveur de publication, exécutez [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Spécifiez un nom de **@publication**publication pour, la valeur **snapshot** ou **Continuous** pour **@repl_freq**et un ou plusieurs des paramètres d’instantané suivants :  
  
    -   **@alt_snapshot_folder**-Spécifiez un chemin d’accès si l’instantané de cette publication est accessible à partir de cet emplacement à la place ou en plus du dossier d’instantanés par défaut.  
  
    -   **@compress_snapshot**-Spécifiez la valeur **true** si les fichiers d’instantanés dans le dossier d’instantanés de remplacement sont compressés dans le format de fichier CAB.  
  
    -   **@pre_snapshot_script**-Spécifiez le nom de fichier et le chemin d’accès complet d’un fichier **. SQL** qui sera exécuté sur l’abonné au cours de l’initialisation, avant que l’instantané initial soit appliqué.  
  
    -   **@post_snapshot_script**-Spécifiez le nom de fichier et le chemin d’accès complet d’un fichier **. SQL** qui sera exécuté sur l’abonné au cours de l’initialisation après l’application de l’instantané initial.  
  
    -   **@snapshot_in_defaultfolder**-Spécifiez la valeur **false** si l’instantané est disponible uniquement à un emplacement autre que celui par défaut.  
  
2.  Pour plus d'informations sur la création des publications, consultez [Create a Publication](create-a-publication.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a>Pour modifier les propriétés d'instantané d'une publication transactionnelle ou d'instantané existante  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql). Spécifiez la valeur **1** pour **@force_invalidate_snapshot** et l’une des valeurs suivantes pour **@property**:  
  
    -   **alt_snapshot_folder** : spécifiez également un nouveau chemin d’accès au dossier d' **@value**instantanés de remplacement pour.  
  
    -   **compress_snapshot** : spécifiez également la valeur **true** ou **false** pour **@value** pour indiquer si les fichiers d’instantanés dans le dossier d’instantanés de remplacement sont compressés dans le format de fichier CAB.  
  
    -   **pre_snapshot_script** : **@value** spécifiez également le nom de fichier et le chemin d’accès complet d’un fichier **. SQL** qui sera exécuté sur l’abonné au cours de l’initialisation, avant que l’instantané initial soit appliqué.  
  
    -   **post_snapshot_script** : **@value** spécifiez également le nom de fichier et le chemin d’accès complet d’un fichier **. SQL** qui sera exécuté sur l’abonné au cours de l’initialisation après l’application de l’instantané initial.  
  
    -   **snapshot_in_defaultfolder** – spécifiez également la valeur **true** ou **false** pour indiquer si l'instantané est disponible uniquement dans un emplacement non défini par défaut.  
  
2.  (Facultatif) Sur le serveur de publication, dans la base de données de publication, exécutez [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql). Spécifiez **@publication** et un ou plusieurs des paramètres de planification ou d’informations d’identification de sécurité en cours de modification.  
  
    > [!IMPORTANT]  
    >  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous devez enregistrer les informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher un accès non autorisé.  
  
3.  Exécutez l' [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) à partir de l'invite de commandes ou démarrez le travail de l'Agent d'instantané pour générer un nouvel instantané. Pour plus d’informations, voir [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a>Pour modifier les propriétés d'instantané d'une publication de fusion existante  
  
1.  Dans la base de données de publication sur le serveur de publication, exécutez [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql). Spécifiez la valeur **1** pour **@force_invalidate_snapshot** et l’une des valeurs suivantes pour **@property**:  
  
    -   **alt_snapshot_folder** : spécifiez également un nouveau chemin d’accès au dossier d' **@value**instantanés de remplacement pour.  
  
    -   **compress_snapshot** : spécifiez également la valeur **true** ou **false** pour **@value** pour indiquer si les fichiers d’instantanés dans le dossier d’instantanés de remplacement sont compressés dans le format de fichier CAB.  
  
    -   **pre_snapshot_script** : **@value** spécifiez également le nom de fichier et le chemin d’accès complet d’un fichier **. SQL** qui sera exécuté sur l’abonné au cours de l’initialisation, avant que l’instantané initial soit appliqué.  
  
    -   **post_snapshot_script** : **@value** spécifiez également le nom de fichier et le chemin d’accès complet d’un fichier **. SQL** qui sera exécuté sur l’abonné au cours de l’initialisation après l’application de l’instantané initial.  
  
    -   **snapshot_in_defaultfolder** – spécifiez également la valeur **true** ou **false** pour indiquer si l'instantané est disponible uniquement dans un emplacement non défini par défaut.  
  
2.  Exécutez l' [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) à partir de l'invite de commandes ou démarrez le travail de l'Agent d'instantané pour générer un nouvel instantané. Pour plus d’informations, voir [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple crée une publication qui utilise un dossier d'instantanés de remplacement et un instantané compressé.  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubaltsnapshot.sql#sp_mergealtsnapshot)]  
  
## <a name="see-also"></a>Voir aussi  
 [Autres emplacements de dossier d’instantanés](../alternate-snapshot-folder-locations.md)   
 [Captures instantanées compressées](../compressed-snapshots.md)   
 [Exécuter des scripts avant et après l’application de l’instantané](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)   
 [Concepts liés aux procédures stockées système de réplication](../concepts/replication-system-stored-procedures-concepts.md)   
 [Transférer des instantanés via FTP](../transfer-snapshots-through-ftp.md)   
 [Modifier les propriétés des publications et des articles](change-publication-and-article-properties.md)  
  
  
