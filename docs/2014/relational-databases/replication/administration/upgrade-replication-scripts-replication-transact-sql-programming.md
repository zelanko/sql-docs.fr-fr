---
title: Mettre à niveau les scripts de réplication (programmation Transact-SQL de la réplication) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- scripts [SQL Server replication], upgrading
- upgrading SQL Server, replicated databases
- upgrading replication applications
- replication [SQL Server], scripting
- replication [SQL Server], upgrading
- upgrading replicated databases
ms.assetid: 0b8720bd-f339-4842-bc8f-b35a46f6d3ee
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cd3f6498cbfb4ef8cf38e27879d619472a6693ce
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68210761"
---
# <a name="upgrade-replication-scripts-replication-transact-sql-programming"></a>Mettre à niveau les scripts de réplication (programmation Transact-SQL de la réplication)
  [!INCLUDE[tsql](../../../includes/tsql-md.md)] Les fichiers de script peuvent être utilisés pour configurer une topologie de réplication par programmation. Pour plus d’informations, consultez [Concepts liés aux procédures stockées système de réplication](../concepts/replication-system-stored-procedures-concepts.md).  
  
> [!IMPORTANT]  
>  Bien que vous ne soyez pas tenu de mettre à niveau les scripts exécutés par les membres du rôle `sysadmin`, nous vous recommandons de modifier les scripts existants comme décrit dans cette rubrique. Spécifiez un compte qui possède les autorisations minimales pour chaque agent de réplication comme décrit dans la section « Autorisations requises par les Agents » de la rubrique [Replication Agent Security Model](../security/replication-agent-security-model.md).  
  
 Ces améliorations de sécurité, qui offrent un contrôle accru sur les autorisations en vous permettant de spécifier explicitement les comptes Windows [!INCLUDE[msCoName](../../../includes/msconame-md.md)] sous lesquels les travaux de l'Agent de réplication sont exécutés, affectent les procédures stockées suivantes dans les scripts existants :  
  
-   **sp_addpublication_snapshot**:  
  
     Vous devez maintenant fournir les informations d’identification Windows **@job_login** comme **@job_password** et lors de l’exécution de [SP_ADDPUBLICATION_SNAPSHOT &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) pour créer le travail sous lequel l’agent d’instantané s’exécute sur le serveur de distribution.  
  
-   **sp_addpushsubscription_agent**:  
  
     Vous devez maintenant exécuter [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql) pour ajouter un travail explicitement et fournir les informations d’identification Windows (**@job_login** et **@job_password**) sous lesquelles le travail de l’Agent de distribution s’exécute sur le serveur de distribution. Dans les versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], ces actions étaient exécutées automatiquement lors de la création d'un abonnement par émission de données.  
  
-   **sp_addmergepushsubscription_agent**:  
  
     Vous devez maintenant exécuter [sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql) pour ajouter un travail explicitement et fournir les informations d’identification Windows (**@job_login** et **@job_password**) sous lesquelles le travail de l’Agent de fusion s’exécute sur le serveur de distribution. Dans les versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], ces actions étaient exécutées automatiquement lors de la création d'un abonnement par émission de données.  
  
-   **sp_addpullsubscription_agent**:  
  
     Vous devez maintenant fournir les informations d’identification Windows **@job_login** comme **@job_password** et lors de l’exécution de [SP_ADDPULLSUBSCRIPTION_AGENT &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) pour créer le travail sous lequel l’agent de distribution s’exécute sur l’abonné.  
  
-   **sp_addmergepullsubscription_agent**:  
  
     Vous devez maintenant fournir les informations d’identification Windows **@job_login** comme **@job_password** et lors de l’exécution de [SP_ADDMERGEPULLSUBSCRIPTION_AGENT &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql) pour créer le travail sous lequel l’agent de fusion s’exécute sur l’abonné.  
  
-   **sp_addlogreader_agent**:  
  
     Vous devez maintenant exécuter [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql) pour ajouter manuellement le travail et fournir les informations d’identification Windows sous lesquelles l’Agent de lecture du journal s’exécute sur le serveur de distribution. Dans les versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], ces actions étaient exécutées automatiquement lors de la création d'une publication transactionnelle.  
  
-   **sp_addqreader_agent**:  
  
     Vous devez maintenant exécuter [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) pour ajouter manuellement le travail et fournir les informations d’identification Windows sous lesquelles l’Agent de lecture de la file d’attente s’exécute sur le serveur de distribution. Dans les versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], ces actions étaient exécutées automatiquement lors de la création d'une publication transactionnelle prenant en charge la mise à jour en file d'attente.  
  
 Dans le modèle de sécurité introduit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]dans, les agents de réplication effectuent toujours des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] connexions à l’instance locale de avec l’authentification **@job_name** Windows **@job_password**à l’aide des informations d’identification fournies dans et. Pour plus d'informations sur la configuration requise des comptes Windows lors de l'exécution des travaux de l'Agent de réplication, consultez [Replication Agent Security Model](../security/replication-agent-security-model.md).  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous stockez les informations d'identification dans un fichier de script, assurez-vous que le fichier lui-même est sécurisé.  
  
### <a name="to-upgrade-scripts-that-configure-a-snapshot-or-transactional-publication"></a>Pour mettre à niveau les scripts qui configurent une publication transactionnelle ou d'instantané  
  
1.  Dans le script existant, avant [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), exécutez [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql) sur le serveur de publication sur la base de données de publication. Spécifiez les informations d’identification Windows sous lesquelles l’agent de lecture **@job_name** du **@job_password**journal s’exécute pour et. Si l'agent doit utiliser l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lors de la connexion au serveur de publication, vous devez aussi spécifier la valeur **0** pour **@publisher_security_mode** et les informations de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour **@publisher_login** et **@publisher_password**. Il s'ensuit la création d'un travail de l'Agent de lecture du journal pour la base de données de publication.  
  
    > [!NOTE]  
    >  Cette étape concerne uniquement les publications transactionnelles et n'est pas requise pour les publications d'instantané.  
  
2.  (Facultatif) Avant [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), exécutez [sp_addqreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql) sur la base de données de distribution sur le serveur de distribution. Spécifiez les informations d’identification Windows sous lesquelles l’Agent de lecture de la file d’attente **@job_name** s' **@job_password**exécute pour et. Il s'ensuit la création d'un travail de l'Agent de lecture de la file d'attente pour le serveur de distribution.  
  
    > [!NOTE]  
    >  Cette étape n'est requise que pour les publications transactionnelles qui prennent en charge les Abonnés de mise à jour en file d'attente.  
  
3.  (Facultatif) Mettez à jour l’exécution de [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) pour spécifier les valeurs non définies par défaut des paramètres qui implémentent les nouvelles fonctionnalités de réplication.  
  
4.  Après [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql), exécutez [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) au niveau du serveur de publication sur la base de données de publication. Spécifiez **@publication** et les informations d’identification Windows sous lesquelles l’agent d’instantané **@job_name** s' **@job_password**exécute pour et. Si l'agent doit utiliser l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lors de la connexion au serveur de publication, vous devez aussi spécifier la valeur **0** pour **@publisher_security_mode** et les informations de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour **@publisher_login** et **@publisher_password**. Il s'ensuit la création d'un travail de l'Agent d'instantané pour la publication.  
  
5.  (Facultatif) Mettez à jour l’exécution de [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) pour spécifier les valeurs non définies par défaut des paramètres qui implémentent les nouvelles fonctionnalités de réplication.  
  
### <a name="to-upgrade-scripts-that-add-subscriptions-to-a-snapshot-or-transactional-publication"></a>Pour mettre à niveau les scripts qui ajoutent des abonnements à une publication transactionnelle ou d'instantané  
  
1.  Après avoir exécuté la procédure stockée qui crée l'abonnement, veillez bien à exécuter celle qui crée un travail de l'Agent de distribution pour synchroniser l'abonnement. La procédure stockée que vous utilisez dépend du type d'abonnement.  
  
    -   Pour un abonnement par extraction, mettez à jour l’exécution de [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) afin de fournir les informations d’identification Windows sous lesquelles l’Agent de distribution s’exécute sur l’Abonné pour **@job_name** et **@job_password**. Cette opération s'effectue après l'exécution de [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql). Pour plus d’informations, consultez [Créer un abonnement par extraction de données (pull)](../create-a-pull-subscription.md).  
  
    -   Pour un abonnement par émission de données, exécutez [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql) sur le serveur de publication. **@subscriber**Spécifiez **@subscriber_db**, **@publication**,, les informations d’identification Windows sous lesquelles l’agent de distribution s’exécute **@job_name** sur **@job_password**le serveur de distribution pour et, ainsi qu’une planification pour ce travail de l’agent. Pour plus d’informations, consultez [Spécifier des planifications de synchronisation](../specify-synchronization-schedules.md). Cette opération s'effectue après l'exécution de [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Pour plus d’informations, consultez [Créer un abonnement par émission (push)](../create-a-push-subscription.md).  
  
### <a name="to-upgrade-scripts-that-configure-a-merge-publication"></a>Pour mettre à niveau les scripts qui configurent une publication de fusion  
  
1.  (Facultatif) Dans le script existant, mettez à jour l’exécution de [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) pour spécifier les valeurs non définies par défaut des paramètres qui implémentent de nouvelles fonctionnalités de réplication.  
  
2.  Après [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), exécutez [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) au niveau du serveur de publication sur la base de données de publication. Spécifiez **@publication** et les informations d’identification Windows sous lesquelles l’agent d’instantané **@job_name** s' **@job_password**exécute pour et. Si l'agent doit utiliser l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lors de la connexion au serveur de publication, vous devez aussi spécifier la valeur **0** pour **@publisher_security_mode** et les informations de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour **@publisher_login** et **@publisher_password**. Il s'ensuit la création d'un travail de l'Agent d'instantané pour la publication.  
  
3.  (Facultatif) Mettez à jour l’exécution de [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) pour spécifier les valeurs non définies par défaut des paramètres qui implémentent les nouvelles fonctionnalités de réplication.  
  
### <a name="to-upgrade-scripts-that-add-subscriptions-to-a-merge-publication"></a>Pour mettre à niveau les scripts qui ajoutent des abonnements à une publication de fusion  
  
1.  Après avoir exécuté la procédure stockée qui crée l'abonnement, veillez bien à exécuter celle qui crée un travail de l'Agent de fusion pour synchroniser l'abonnement. La procédure stockée que vous utilisez dépend du type d'abonnement.  
  
    -   Pour un abonnement par extraction, mettez à jour l’exécution de [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql) afin de fournir les informations d’identification Windows sous lesquelles l’Agent de fusion s’exécute sur l’Abonné pour **@job_name** et **@job_password**. Cette opération s'effectue après l'exécution de [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql). Pour plus d’informations, consultez [Créer un abonnement par extraction de données (pull)](../create-a-pull-subscription.md).  
  
    -   Pour un abonnement par émission de données, exécutez [sp_addmergepushsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql) sur le serveur de publication. **@subscriber**Spécifiez **@subscriber_db**, **@publication**,, les informations d’identification Windows sous lesquelles l’agent de fusion sur le serveur **@job_name** de **@job_password**distribution s’exécute pour et, ainsi qu’une planification pour ce travail de l’agent. Pour plus d’informations, consultez [Spécifier des planifications de synchronisation](../specify-synchronization-schedules.md). Cette opération s'effectue après l'exécution de [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql). Pour plus d’informations, consultez [Créer un abonnement par émission (push)](../create-a-push-subscription.md).  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] créant une publication transactionnelle pour la table Product. Cette publication prend en charge la mise à jour immédiate avec la mise à jour en file d'attente comme basculement. Les paramètres par défaut ont été supprimés pour des raisons de lisibilité.  
  
 [!code-sql[HowTo#sp_createtranpub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpub80.sql#sp_createtranpub_nwpreupgrade)]  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de mise à niveau du précédent script, lequel crée une publication transactionnelle, pour qu'il s'exécute avec succès sous [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures. Cette publication prend en charge la mise à jour immédiate avec la mise à jour en file d'attente comme basculement. Les valeurs par défaut des nouveaux paramètres ont été déclarées explicitement.  
  
> [!NOTE]  
>  Les informations d'identification Windows sont fournies pendant l'exécution à l'aide des variables de script **Sqlcmd** .  
  
 [!code-sql[HowTo#sp_createtranpub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpublication.sql#sp_createtranpub_nwpostupgrade)]  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] qui crée une publication de fusion pour la table Customers. Les paramètres par défaut ont été supprimés pour des raisons de lisibilité.  
  
 [!code-sql[HowTo#sp_createmergepub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepub80.sql#sp_createmergepub_nwpreupgrade)]  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de mise à niveau du précédent script, lequel crée une publication de fusion, pour qu'il s'exécute avec succès sous [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures. Les valeurs par défaut des nouveaux paramètres ont été déclarées explicitement.  
  
> [!NOTE]  
>  Les informations d'identification Windows sont fournies pendant l'exécution à l'aide des variables de script **Sqlcmd** .  
  
 [!code-sql[HowTo#sp_createmergepub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepublication.sql#sp_createmergepub_nwpostupgrade)]  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] qui crée un abonnement par émission de données à une publication transactionnelle. Les paramètres par défaut ont été supprimés pour des raisons de lisibilité.  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwtranpushsub80.sql#sp_createtranpushsub_nwpreupgrade)]  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de mise à niveau du précédent script, lequel crée un abonnement par émission de données à une publication transactionnelle, pour qu'il s'exécute avec succès sous [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures. Les valeurs par défaut des nouveaux paramètres ont été déclarées explicitement.  
  
> [!NOTE]  
>  Les informations d'identification Windows sont fournies pendant l'exécution à l'aide des variables de script **Sqlcmd** .  
  
 [!code-sql[HowTo#sp_createtranpushsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpushsub.sql#sp_createtranpushsub_nwpostupgrade)]  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] qui crée un abonnement par émission de données à une publication de fusion. Les paramètres par défaut ont été supprimés pour des raisons de lisibilité.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepushsub80.sql#sp_createmergepushsub_nwpreupgrade)]  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de mise à niveau du précédent script, lequel crée un abonnement par émission de données à une publication de fusion, pour qu'il s'exécute avec succès sous [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures. Les valeurs par défaut des nouveaux paramètres ont été déclarées explicitement.  
  
> [!NOTE]  
>  Les informations d'identification Windows sont fournies pendant l'exécution à l'aide des variables de script **Sqlcmd** .  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpushsub.sql#sp_createmergepushsub_nwpostupgrade)]  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] qui crée un abonnement par extraction à une publication transactionnelle. Les paramètres par défaut ont été supprimés pour des raisons de lisibilité.  
  
 [!code-sql[HowTo#sp_createmergepushsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepushsub80.sql#sp_createmergepushsub_nwpreupgrade)]  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de mise à niveau du précédent script, lequel crée un abonnement par extraction à une publication transactionnelle, pour qu'il s'exécute avec succès sous [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures. Les valeurs par défaut des nouveaux paramètres ont été déclarées explicitement.  
  
> [!NOTE]  
>  Les informations d'identification Windows sont fournies pendant l'exécution à l'aide des variables de script **Sqlcmd** .  
  
 [!code-sql[HowTo#sp_createtranpullsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpullsub.sql#sp_createtranpullsub_nwpostupgrade)]  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de script [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] qui crée un abonnement par extraction à une publication de fusion. Les paramètres par défaut ont été supprimés pour des raisons de lisibilité.  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpreupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwmergepullsub80.sql#sp_createmergepullsub_nwpreupgrade)]  
  
## <a name="example"></a>Exemple  
 Ce qui suit est un exemple de mise à niveau du précédent script, lequel crée un abonnement par extraction à une publication de fusion, pour qu'il s'exécute avec succès sous [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures. Les valeurs par défaut des nouveaux paramètres ont été déclarées explicitement.  
  
> [!NOTE]  
>  Les informations d'identification Windows sont fournies pendant l'exécution à l'aide des variables de script **Sqlcmd** .  
  
 [!code-sql[HowTo#sp_createmergepullsub_NWpostupgrade](../../../snippets/tsql/SQL15/replication/howto/tsql/createnwpullsub.sql#sp_createmergepullsub_nwpostupgrade)]  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](../publish/create-a-publication.md)   
 [Créer un abonnement par émission de notification](../create-a-push-subscription.md)   
 [Create a Pull Subscription](../create-a-pull-subscription.md)   
 [Afficher et modifier les paramètres de sécurité de la réplication](../security/view-and-modify-replication-security-settings.md)   
 [MSSQL_ENG021797](../mssql-eng021797.md)   
 [MSSQL_ENG021798](../mssql-eng021798.md)   
 [Concepts des procédures stockées système de réplication](../concepts/replication-system-stored-procedures-concepts.md)   
 [Mettre à niveau des bases de données répliquées](../../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
  
