---
title: Créer un abonnement pouvant être mis à jour pour une publication transactionnelle (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 07/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- updateable transactional subscriptions
- updateable transactional subscriptions, SSMS
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e784216116bdb9ab308dff5fa998740b0fa459b0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060576"
---
# <a name="create-an-updatable-subscription-to-a-transactional-publication-management-studio"></a>Créer un abonnement pouvant être mis à jour pour une publication transactionnelle (Management Studio)

> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
La réplication transactionnelle permet de propager sur le serveur de publication les modifications apportées au niveau d'un Abonné en utilisant des abonnements avec mise à jour immédiate ou mise à jour en file d'attente. Vous pouvez créer par programme un abonnement avec mise à jour en utilisant des procédures stockées de réplication.

Configurez des abonnements pouvant être mis à jour dans la page **Abonnements pouvant être mis à jour** de l’**Assistant Nouvel abonnement**. Cette page est disponible seulement si vous avez activé une publication transactionnelle pour les abonnements pouvant être mis à jour. Pour plus d’informations sur l’activation des abonnements pouvant être mis à jour, consultez [Activer la mise à jour d’abonnements pour les publications transactionnelles](enable-updating-subscriptions-for-transactional-publications.md).   
  
## <a name="configure-an-updatable-subscription-from-the-publisher"></a>Configurer un abonnement pouvant être mis à jour à partir du serveur de publication  

1. Connectez-vous au serveur de publication dans Microsoft SQL Server Management Studio, puis développez le nœud du serveur.
2. Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .
3. Cliquez avec le bouton droit sur une publication transactionnelle activée pour la mise à jour d’abonnements, puis cliquez sur **Nouveaux abonnements**.
4. Suivez les pages de l'Assistant pour spécifier les options de l'abonnement, par exemple où l'Agent de distribution doit s'exécuter.
5. Dans la page **Abonnements pouvant être mis à jour** de l’**Assistant Nouvel abonnement**, vérifiez que **Répliquer** est sélectionné.
6. Sélectionnez une option dans la liste déroulante **Valider sur le serveur de publication** :

    *  Pour utiliser des abonnements mis à jour immédiatement, sélectionnez **Enregistrer les modifications simultanément**. Si vous sélectionnez cette option et que la publication autorise les abonnements mis à jour en attente (l’option par défaut pour les publications créées avec l’Assistant Nouvelle publication), la propriété d’abonnement **update_mode** a la valeur **failover**. Ce mode vous permet de passer ultérieurement en mise à jour en attente si nécessaire.
    *  Pour utiliser des abonnements mis à jour en attente, sélectionnez **Mettre les modifications en file d’attente et valider dès que possible**. Si vous sélectionnez cette option et que la publication autorise les abonnements mis à jour immédiatement (l’option par défaut pour les publications créées avec l’Assistant Nouvelle publication), et si l’abonné exécute SQL Server 2005 ou une version ultérieure, la propriété d’abonnement **update_mode** a la valeur queued failover. Ce mode vous permet de passer ultérieurement en mise à jour immédiate si nécessaire.

    Pour plus d’informations sur le basculement entre les modes de mise à jour, consultez [Basculer entre les modes de mise à jour d’un abonnement transactionnel pouvant être mis à jour](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

7. La page **Nom d’accès aux abonnements pouvant être mis à jour** est affichée pour les abonnements qui utilisent la mise à jour immédiate ou dont la propriété **update_mode** a la valeur **queued failover**. Dans la page **Nom d’accès aux abonnements pouvant être mis à jour**, spécifiez un serveur lié via lequel sont effectuées les connexions au serveur de publication pour les abonnements mis à jour immédiatement. Les connexions sont utilisées par les déclencheurs qui s'exécutent pour l'abonné et propagent les modifications sur le serveur de publication. Sélectionnez l’une des options suivantes :

    * **Créer un serveur lié qui se connecte par Authentification SQL Server**. Sélectionnez cette option si vous n'avez pas défini un serveur distant ou un serveur lié entre l'Abonné et le serveur de publication. La réplication crée un serveur lié pour vous. Le compte que vous spécifiez doit déjà exister sur le serveur de publication.
    * **Utiliser un serveur lié ou un serveur distant que vous avez déjà défini.** Sélectionnez cette option si vous avez défini un serveur distant ou un serveur lié entre l’abonné et le serveur de publication à l’aide de [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio ou d’une autre méthode.

    Pour plus d’informations sur les autorisations requises par le compte du serveur lié, consultez la section **Abonnements mis à jour en attente** de [saisissez la description de lien ici](../security/secure-the-subscriber.md).

8. Effectuez toutes les étapes de l'Assistant.

## <a name="configure-an-updatable-subscription-from-the-subscriber"></a>Configurer un abonnement pouvant être mis à jour à partir de l’Abonné


1. Connectez-vous à l’abonné dans SQL Server Management Studio, puis développez le nœud du serveur.
2. Développez le dossier **Réplication** .
3. Cliquez avec le bouton droit sur le dossier **Abonnements locaux** , puis cliquez sur **Nouveaux abonnements**.
4. Dans la page **Publication** de l’**Assistant Nouvel abonnement**, sélectionnez **Rechercher un serveur de publication SQL Server** dans la liste déroulante **Serveur de publication**.
5. Connectez-vous au serveur de publication dans la boîte de dialogue **Se connecter au serveur** .
6. Sélectionnez une publication transactionnelle activée pour la mise à jour d’abonnements dans la page **Publication**.
7. Suivez les pages de l'Assistant pour spécifier les options de l'abonnement, par exemple où l'Agent de distribution doit s'exécuter.
8. Dans la page **abonnements pouvant être mis à jour** de l’Assistant nouvel abonnement, vérifiez que **répliquer** est sélectionné.
9. Sélectionnez une option dans la liste déroulante **Valider sur le serveur de publication** :

    * Pour utiliser des abonnements mis à jour immédiatement, sélectionnez **Enregistrer les modifications simultanément**. Si vous sélectionnez cette option et que la publication autorise les abonnements mis à jour en attente (l’option par défaut pour les publications créées avec l’Assistant Nouvelle publication), la propriété d’abonnement **update_mode** a la valeur **failover**. Ce mode vous permet de passer ultérieurement en mise à jour en attente si nécessaire.
    * Pour utiliser des abonnements mis à jour en attente, sélectionnez **Mettre les modifications en file d’attente et valider dès que possible**. Si vous sélectionnez cette option et que la publication autorise les abonnements mis à jour immédiatement (valeur par défaut pour les publications créées avec l’Assistant Nouvelle publication), et si l’abonné exécute SQL Server 2005 ou une version ultérieure, la propriété d’abonnement **update_mode** est définie sur **basculement**en file d’attente. Ce mode vous permet de passer ultérieurement en mise à jour immédiate si nécessaire.

    Pour plus d’informations sur le basculement entre les modes de mise à jour, consultez [Basculer entre les modes de mise à jour d’un abonnement transactionnel pouvant être mis à jour](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

10. La page **connexion pour les abonnements pouvant être mis** à jour s’affiche pour les abonnements qui utilisent la mise à jour immédiate ou qui ont **update_mode** défini sur **basculement**en attente. Dans la page **Nom d’accès aux abonnements pouvant être mis à jour**, spécifiez un serveur lié via lequel sont effectuées les connexions au serveur de publication pour les abonnements mis à jour immédiatement. Les connexions sont utilisées par les déclencheurs qui s'exécutent pour l'abonné et propagent les modifications sur le serveur de publication. Sélectionnez l’une des options suivantes :

    * **Créer un serveur lié qui se connecte par Authentification SQL Server**. Sélectionnez cette option si vous n'avez pas défini un serveur distant ou un serveur lié entre l'Abonné et le serveur de publication. La réplication crée un serveur lié pour vous. Le compte que vous spécifiez doit déjà exister sur le serveur de publication.
    * **Utiliser un serveur lié ou un serveur distant que vous avez déjà défini.** Sélectionnez cette option si vous avez défini un serveur distant ou un serveur lié entre l’abonné et le serveur de publication à l’aide de [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio ou d’une autre méthode.

    Pour plus d’informations sur les autorisations requises par le compte du serveur lié, consultez la section **Abonnements mis à jour en attente** de [saisissez la description de lien ici](../security/secure-the-subscriber.md).

11. Effectuez toutes les étapes de l'Assistant.

## <a name="create-an-immediate-updating-pull-subscription"></a>Créer un abonnement par extraction avec mise à jour immédiate

1. Sur le serveur de publication, vérifiez que la publication prend en charge les abonnements avec mise à jour immédiate en exécutant [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Si la valeur de `allow_sync_tran` dans le jeu de résultats est `1`, la publication prend en charge les abonnements avec mise à jour immédiate.
    * Si la valeur de `allow_sync_tran` dans le jeu de résultats est `0`, la publication doit être recréée en activant la prise en charge des abonnements avec mise à jour immédiate.

2. Sur le serveur de publication, vérifiez que la publication prend en charge les abonnements par extraction en exécutant [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Si la valeur de `allow_pull` dans le jeu de résultats est `1`, la publication prend en charge les abonnements par extraction.
    * Si la valeur de `allow_pull` est `0`, exécutez [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), en spécifiant `allow_pull` pour `@property` , et `true` pour `@value`. 

3. Sur l'Abonné, exécutez [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql). Spécifiez `@publisher` et `@publication`, et l’une des valeurs suivantes pour `@update_mode`:

    * `sync tran` - active l’abonnement pour la mise à jour immédiate.
    * `failover` - active l’abonnement pour la mise à jour immédiate avec mise à jour en file d’attente sous forme d’option de basculement.

    > [!NOTE]  
>  `failover` requiert que la publication soit également activée pour les abonnements avec mise à jour en file d’attente. 
 
4. Sur l'Abonné, exécutez [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql). Spécifiez les éléments suivants :

    * Les paramètres `@publisher`, `@publisher_db`et `@publication` . 
    * Les informations d’identification Microsoft Windows sous lesquelles l’Agent de distribution est exécuté sur l’abonné pour `@job_login` et `@job_password`. 

    > [!NOTE]  
>  Les connexions établies à l’aide de l’authentification intégrée Windows utilisent toujours les informations d’identification Windows spécifiées par `@job_login` et `@job_password`. L'Agent de distribution établit toujours la connexion locale à l'Abonné à l'aide de l'authentification intégrée Windows. Par défaut, l'agent se connecte au serveur de distribution à l'aide de l'authentification intégrée Windows. 
 
    * (Facultatif) Une valeur de `0` pour `@distributor_security_mode` et les informations de connexion Microsoft SQL Server pour `@distributor_login` et `@distributor_password`, si vous devez utiliser l’authentification SQL Server lors de la connexion du distributeur. 
    * Planification du travail de l'Agent de distribution pour cet abonnement. 

5. Dans la base de données d’abonnement de l’Abonné, exécutez [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql). Spécifiez `@publisher`, `@publication`, le nom de la base de données de publication pour `@publisher_db`, et l’une des valeurs suivantes pour `@security_mode`: 

    * `0` - Utiliser l’authentification SQL Server pour effectuer des mises à jour sur le serveur de publication. Avec cette option, vous devez spécifier une connexion valide sur le serveur de publication pour `@login` et `@password`.
    * `1` - Utiliser le contexte de sécurité de l’utilisateur qui apporte des modifications à l’Abonné lors de la connexion au serveur de publication. Consultez [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) pour connaître les restrictions en rapport avec ce mode de sécurité.
    * `2` - Utiliser une connexion de serveur lié existante, définie par l’utilisateur, créée à l’aide de [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).

6. Sur le serveur de publication, exécutez [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) spécifiant `@publication` , `@subscriber` , `@destination_db` , la valeur pull pour `@subscription_type` et la même valeur spécifiée à l’étape 3 pour `@update_mode` .

L'abonnement par extraction est alors inscrit sur le serveur de publication. 


## <a name="create-an-immediate-updating-push-subscription"></a>Créer un abonnement par émission de données avec mise à jour immédiate 

1. Sur le serveur de publication, vérifiez que la publication prend en charge les abonnements avec mise à jour immédiate en exécutant [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Si la valeur de `allow_sync_tran` dans le jeu de résultats est `1`, la publication prend en charge les abonnements avec mise à jour immédiate.
    * Si la valeur de `allow_sync_tran` dans le jeu de résultats est `0`, la publication doit être recréée en activant la prise en charge des abonnements avec mise à jour immédiate.

2. Sur le serveur de publication, vérifiez que la publication prend en charge les abonnements par émission de données en exécutant [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Si la valeur de `allow_push` dans le jeu de résultats est `1`, la publication prend en charge les abonnements par émission de données.
    * Si la valeur de `allow_push` est `0`, exécutez [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), en spécifiant `allow_push` pour `@property` , et `true` pour `@value`. 

3. Sur le serveur de publication, exécutez [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Spécifiez `@publication`, `@subscriber`, `@destination_db`, et l’une des valeurs suivantes pour `@update_mode`:

    * `sync tran` - active la prise en charge de la mise à jour immédiate.
    * `failover` - active la prise en charge de la mise à jour immédiate avec mise à jour en file d’attente comme option de basculement.

    > [!NOTE]  
>  `failover` requiert que la publication soit également activée pour les abonnements avec mise à jour en file d’attente. 
 
4. Sur le serveur de publication, exécutez [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql). Spécifiez les paramètres suivants :

    * `@subscriber`, `@subscriber_db`et `@publication`. 
    * Informations d’identification Windows sous lesquelles l’Agent de distribution s’exécute sur le serveur de distribution pour `@job_login` et `@job_password`. 

    > [!NOTE]  
>  Les connexions établies à l’aide de l’authentification intégrée Windows utilisent toujours les informations d’identification Windows spécifiées par `@job_login` et `@job_password`. L'Agent de distribution crée toujours la connexion locale au serveur de distribution à l'aide de l'authentification intégrée Windows. Par défaut, l'agent se connecte à l'Abonné à l'aide de ces informations. 

    * (Facultatif) Une valeur de `0` pour `@subscriber_security_mode` et les informations de connexion SQL Server pour `@subscriber_login` et `@subscriber_password`, si vous devez utiliser l’authentification SQL Server lors de la connexion de l’abonné. 
    * Planification du travail de l'Agent de distribution pour cet abonnement.

5. Dans la base de données d’abonnement de l’Abonné, exécutez [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql). Spécifiez `@publisher`, `@publication`, le nom de la base de données de publication pour `@publisher_db`, et l’une des valeurs suivantes pour `@security_mode`: 

     * `0` - Utiliser l’authentification SQL Server pour effectuer des mises à jour sur le serveur de publication. Avec cette option, vous devez spécifier une connexion valide sur le serveur de publication pour `@login` et `@password`.
     * `1` - Utiliser le contexte de sécurité de l’utilisateur qui apporte des modifications à l’Abonné lors de la connexion au serveur de publication. Consultez [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) pour connaître les restrictions en rapport avec ce mode de sécurité.
     * `2` - Utiliser une connexion de serveur lié existante, définie par l’utilisateur, créée à l’aide de [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).


## <a name="create-a-queued-updating-pull-subscription"></a>Créer un abonnement par extraction avec mise à jour en file d’attente ##

1. Sur le serveur de publication, vérifiez que la publication prend en charge les abonnements avec mise à jour en file d’attente en exécutant [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Si la valeur de `allow_queued_tran` dans le jeu de résultats est `1`, la publication prend en charge les abonnements avec mise à jour immédiate.
    * Si la valeur de `allow_queued_tran` dans le jeu de résultats est `0`, la publication doit être recréée en activant la prise en charge des abonnements avec mise à jour en file d’attente activée.

2. Sur le serveur de publication, vérifiez que la publication prend en charge les abonnements par extraction en exécutant [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Si la valeur de `allow_pull` dans le jeu de résultats est `1`, la publication prend en charge les abonnements par extraction.
    * Si la valeur de `allow_pull` est `0`, exécutez [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), en spécifiant `allow_pull` pour `@property` , et `true` pour `@value`. 

3. Sur l'Abonné, exécutez [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql). Spécifiez `@publisher` et `@publication`, et l’une des valeurs suivantes pour `@update_mode`:

    * `queued tran` - active l’abonnement pour la mise à jour en attente.
    * `queued failover` - active la prise en charge de la mise à jour en file d’attente avec mise à jour immédiate comme option de basculement.

    > [!NOTE]  
>  `queued failover` requiert que la publication soit également activée pour les abonnements avec mise à jour immédiate. Pour basculer sur la mise à jour immédiate, vous devez utiliser [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) pour définir les informations d’identification sous lesquelles les modifications au niveau de l’Abonné sont répliquées sur le serveur de publication.
 
4. Sur l'Abonné, exécutez [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql). Spécifiez les paramètres suivants :

    * @publisher, `@publisher_db`et `@publication`. 
    * Les informations d’identification Windows sous lesquelles l’Agent de distribution est exécuté sur l’abonné pour `@job_login` et `@job_password`. 

    > [!NOTE]  
>  Les connexions établies à l’aide de l’authentification intégrée Windows utilisent toujours les informations d’identification Windows spécifiées par `@job_login` et `@job_password`. L'Agent de distribution établit toujours la connexion locale à l'Abonné à l'aide de l'authentification intégrée Windows. Par défaut, l'agent se connecte au serveur de distribution à l'aide de l'authentification intégrée Windows. 
 
    * (Facultatif) Une valeur de `0` pour `@distributor_security_mode` et les informations de connexion SQL Server pour `@distributor_login` et `@distributor_password`, si vous devez utiliser l’authentification SQL Server lors de la connexion du distributeur. 
    * Planification du travail de l'Agent de distribution pour cet abonnement.

5. Sur le serveur de publication, exécutez [sp_addsubscriber](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) pour inscrire l’abonné sur le serveur de publication, en spécifiant `@publication` ,, `@subscriber` `@destination_db` , la valeur pull pour `@subscription_type` et la même valeur spécifiée à l’étape 3 pour `@update_mode` .

L'abonnement par extraction est alors inscrit sur le serveur de publication. 


## <a name="to-create-a-queued-updating-push-subscription"></a>Pour créer un abonnement par émission de données avec mise à jour en file d'attente ##

1. Sur le serveur de publication, vérifiez que la publication prend en charge les abonnements avec mise à jour en file d’attente en exécutant [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Si la valeur de allow_queued_tran dans le jeu de résultats est 1, la publication prend en charge les abonnements avec mise à jour immédiate.
    * Si la valeur de allow_queued_tran dans le jeu de résultats est 0, la publication doit être recréée en activant la prise en charge des abonnements avec mise à jour en file d’attente. Pour plus d’informations, voir Procédure : activer les abonnements avec mise à jour pour les publications transactionnelles (programmation Transact-SQL de la réplication).

2. Sur le serveur de publication, vérifiez que la publication prend en charge les abonnements par émission de données en exécutant [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Si la valeur de `allow_push` dans le jeu de résultats est `1`, la publication prend en charge les abonnements par émission de données.
    * Si la valeur de `allow_push` est `0`, exécutez [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), en spécifiant allow_push pour `@property` , et `true` pour `@value`. 

3. Sur le serveur de publication, exécutez [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Spécifiez `@publication`, `@subscriber`, `@destination_db`, et l’une des valeurs suivantes pour `@update_mode`:

    * `queued tran` - active l’abonnement pour la mise à jour en attente.
    * `queued failover` - active la prise en charge de la mise à jour en file d’attente avec mise à jour immédiate comme option de basculement.

    > [!NOTE]  
>  L’option queued failover requiert que la publication soit également activée pour les abonnements avec mise à jour immédiate. Pour basculer sur la mise à jour immédiate, vous devez utiliser [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) pour définir les informations d’identification sous lesquelles les modifications au niveau de l’Abonné sont répliquées sur le serveur de publication.

4. Sur le serveur de publication, exécutez [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql). Spécifiez les paramètres suivants :

    * `@subscriber`, `@subscriber_db`et `@publication`. 
    * Informations d’identification Windows sous lesquelles l’Agent de distribution s’exécute sur le serveur de distribution pour `@job_login` et `@job_password`. 

    > [!NOTE]  
>  Les connexions établies à l’aide de l’authentification intégrée Windows utilisent toujours les informations d’identification Windows spécifiées par `@job_login` et `@job_password`. L'Agent de distribution crée toujours la connexion locale au serveur de distribution à l'aide de l'authentification intégrée Windows. Par défaut, l’agent se connecte à l’Abonné à l’aide de ces informations. 
 
    * (Facultatif) Une valeur de `0` pour `@subscriber_security_mode` et les informations de connexion SQL Server pour `@subscriber_login` et `@subscriber_password`, si vous devez utiliser l’authentification SQL Server lors de la connexion de l’abonné. 
    * Planification du travail de l'Agent de distribution pour cet abonnement.


## <a name="example"></a>Exemple ##

Cet exemple crée un abonnement par extraction avec mise à jour immédiate à une publication qui prend en charge les abonnements avec mise à jour immédiate. Les valeurs de connexion et le mot de passe sont fournis lors de l'exécution à l'aide des variables de script sqlcmd.

> [!NOTE]  
>  Ce script utilise des variables de script sqlcmd. Elles sont au format `$(MyVariable)`. Pour plus d’informations sur l’utilisation des variables de script sur la ligne de commande et dans SQL Server Management Studio, consultez la section **Exécution de scripts de réplication** dans la rubrique [Concepts liés aux procédures stockées système de réplication](../concepts/replication-system-stored-procedures-concepts.md).

```sql
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
```

## <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>définir des options de résolution des conflits de mise à jour en attente (SQL Server Management Studio)
  Définissez les options de résolution des conflits pour les publications qui prennent en charge les abonnements mis à jour en attente dans la page **options d’abonnement** de la boîte de dialogue Propriétés de la **publication- \<Publication> ** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>Pour définir les options de résolution des conflits de mise à jour en attente  
  
1.  Dans la page **options d’abonnement** de la boîte de dialogue Propriétés de la **publication- \<Publication> ** , sélectionnez l’une des valeurs suivantes pour l’option stratégie de résolution des **conflits** :    
    -   **Conserver la modification apportée au serveur de publication**    
    -   **Conserver la modification apportée à l'abonné**    
    -   **Réinitialisation de l’abonnement**    
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

## <a name="see-also"></a>Voir aussi ##
 [Create a Publication](create-a-publication.md)   
 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Utiliser sqlcmd avec des variables de script](../../scripting/sqlcmd-use-with-scripting-variables.md)   

  
