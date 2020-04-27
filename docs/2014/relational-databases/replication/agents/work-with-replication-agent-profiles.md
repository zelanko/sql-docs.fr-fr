---
title: Utiliser des profils d’Agent de réplication | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], agents and profiles
- replication agent profiles [SQL Server]
- agents [SQL Server replication], profiles
- profiles [SQL Server], replication agents
ms.assetid: 9c290a88-4e9f-4a7e-aab5-4442137a9918
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b6f66d1bab70619db1631117268e5d62c24c943f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63157128"
---
# <a name="work-with-replication-agent-profiles"></a>Utiliser des profils d'agent de réplication
  Cette rubrique explique comment utiliser les profils de l'Agent de réplication dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou d'objets RMO (Replication Management Objects). Le comportement de chaque agent de réplication est contrôlé par un jeu de paramètres que vous pouvez configurer dans un profil de l'Agent. Chaque agent possède un profil par défaut et certains possèdent d'autres profils prédéfinis ; un Agent ne peut avoir qu'un profil actif à tout moment.  
  
 **Dans cette rubrique**  
  
-   **Pour utiliser les profils de l'Agent de réplication à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
    -   Accéder à la boîte de dialogue Profils de l'Agent  
  
    -   Spécifier un profil d'Agent  
  
    -   Créer un profil  
  
    -   Modifier un profil  
  
    -   Supprimer un profil  
  
     [Transact-SQL](#TsqlProcedure)  
  
    -   Créer un profil  
  
    -   Modifier un profil  
  
    -   Supprimer un profil  
  
    -   Utiliser des profils d'Agent pendant la synchronisation  
  
    -   Exemple Transact-SQL  
  
     [Replication Management Objects](#RMOProcedure)  
  
    -   Créer un profil  
  
    -   Modifier un profil  
  
    -   Supprimer un profil  
  
-   **Suivi :**  [Après avoir changé les paramètres de l’Agent](#FollowUp)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
###  <a name="to-access-the-agent-profiles-dialog-box-from-sql-server-management-studio"></a><a name="Access_SSMS"></a> Pour accéder à la boîte de dialogue Profils d'Agent à partir de SQL Server Management Studio  
  
1.  Dans la page **Général** de la boîte de dialogue **Propriétés du serveur de distribution - \<serveur_distribution**, cliquez sur **Profils par défaut**.  
  
#### <a name="to-access-the-agent-profiles-dialog-box-from-replication-monitor"></a>Pour accéder à la boîte de dialogue Profils d'Agent à partir du moniteur de réplication  
  
-   Pour ouvrir la boîte de dialogue relative à tous les Agents, cliquez avec le bouton droit sur un serveur de publication puis cliquez sur **Profils d'Agent**.  
  
-   Pour ouvrir la boîte de dialogue d'un seul Agent  
  
    1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
    2.  Pour les profils de l'Agent de distribution et de l'Agent de fusion, cliquez avec le bouton droit sur un abonnement dans l'onglet **Tous les abonnements** puis cliquez sur **Profil de l'Agent**. Pour les autres agents, cliquez avec le bouton droit sur l'agent sous l'onglet **Agents** , puis cliquez sur **Profil d'agent**.  
  
###  <a name="to-specify-a-profile-for-an-agent"></a><a name="Specify_SSMS"></a> Pour spécifier un profil d'un Agent  
  
1.  Si la boîte de dialogue **Profils d'Agent** affiche les profils de plusieurs agents, sélectionnez un Agent.  
  
2.  Sélectionnez un profil dans la colonne **Valeur par défaut pour nouveau** de la grille **Profils d'Agent** . Par défaut, le profil est uniquement appliqué aux agents pour les nouveaux abonnements et publications.  
  
3.  Pour que tous les agents du type sélectionné pour les abonnements ou publications existants utilisent ce profil, cliquez sur **Modifier les Agents existants**.  
  
###  <a name="to-view-and-edit-the-parameters-associated-with-a-profile"></a><a name="Modify_SSMS"></a> Pour afficher et modifier les paramètres associés à un profil  
  
1.  Si la boîte de dialogue **Profils d'Agent** affiche les profils de plusieurs agents, sélectionnez un Agent.  
  
2.  Cliquez sur le bouton des propriétés ( **...** ) en regard d’un profil.  
  
3.  Affichez les paramètres et les valeurs dans la boîte de dialogue **Propriétés du profil \<Nom_du_profil**.  
  
    -   Les paramètres des profils définis par l'utilisateur peuvent être modifiés, ce qui n'est pas le cas des profils système prédéfinis.  
  
    -   Pour afficher tous les paramètres relatifs à un Agent, désactivez la case à cocher **Afficher uniquement les paramètres utilisés dans ce profil** . Pour plus d'informations sur les paramètres des Agents, consultez les liens à la fin de cette rubrique.  
  
4.  Cliquez sur **Fermer**.  
  
###  <a name="to-create-a-user-defined-profile"></a><a name="Create_SSMS"></a> Pour créer un profil défini par l'utilisateur  
  
1.  Si la boîte de dialogue **Profils d'Agent** affiche les profils de plusieurs agents, sélectionnez un Agent.  
  
2.  Cliquez sur **Nouveau**.  
  
3.  Dans la boîte de dialogue d'initialisation **Nouveau profil de l'Agent** , sélectionnez un profil existant qui servira de base au nouveau profil.  
  
4.  Dans la boîte de dialogue **Nouveau profil de l'Agent** , entrez des valeurs dans les zones de texte **Nom** et **Description** .  
  
5.  Modifiez les paramètres pour adapter le profil à vos besoins. Pour afficher tous les paramètres relatifs à un Agent, désactivez la case à cocher **Afficher uniquement les paramètres utilisés dans ce profil** . Pour plus d'informations sur les paramètres des Agents, consultez les liens à la fin de cette rubrique.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
###  <a name="to-delete-a-user-defined-profile"></a><a name="Delete_SSMS"></a> Pour supprimer un profil défini par l'utilisateur  
  
1.  Si la boîte de dialogue **Profils d'Agent** affiche les profils de plusieurs agents, sélectionnez un Agent.  
  
2.  Si un profil est associé à un ou plusieurs agents, modifiez le profil de ceux-ci :  
  
    1.  Sélectionnez un autre profil dans la grille **Profils d'Agent** .  
  
    2.  Cliquez sur **Modifier les Agents existants**.  
  
        > [!NOTE]  
        >  Cela modifie le profil de tous les agents du type sélectionné pour les publications ou abonnements existants et pas seulement ceux qui utilisent le profil à supprimer.  
  
3.  Cliquez sur le profil à supprimer, puis sur **Supprimer**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_tsql"></a> Pour créer un profil d'agent  
  
1.  Sur le serveur de distribution, exécutez [sp_add_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql). Spécifiez **@name**, la valeur **1** pour **@profile_type**et l’une des valeurs suivantes pour **@agent_type**:  
  
    -   **1** - [Replication Snapshot Agent](replication-snapshot-agent.md)  
  
    -   **2** - [Replication Log Reader Agent](replication-log-reader-agent.md)  
  
    -   **3** - [Replication Distribution Agent](replication-distribution-agent.md)  
  
    -   **4** - [Replication Merge Agent](replication-merge-agent.md)  
  
    -   **9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)  
  
     Si ce profil devient le nouveau profil par défaut pour son type d'agent de réplication, spécifiez une valeur de **1** pour **@default**. L’identificateur pour le nouveau profil est retourné à l’aide **@profile_id** du paramètre de sortie. Cela crée un nouveau profil avec un jeu de paramètres de profil basé sur le profil par défaut pour le type d'agent donné.  
  
2.  Après avoir créé le nouveau profil, ajoutez, supprimez ou modifiez les paramètres par défaut pour personnaliser le profil.  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_tsql"></a> Pour modifier un profil d'agent existant  
  
1.  Sur le serveur de distribution, exécutez [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql). Spécifiez l’une des valeurs suivantes **@agent_type**pour :  
  
    -   **1** - [Replication Snapshot Agent](replication-snapshot-agent.md)  
  
    -   **2** - [Replication Log Reader Agent](replication-log-reader-agent.md)  
  
    -   **3** - [Replication Distribution Agent](replication-distribution-agent.md)  
  
    -   **4** - [Replication Merge Agent](replication-merge-agent.md)  
  
    -   **9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)  
  
     Tous les profils pour le type d'agent spécifié sont retournés. Notez la valeur de **profile_id** dans le jeu de résultats pour le profil à modifier.  
  
2.  Sur le serveur de distribution, exécutez [sp_help_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql). Spécifiez l’identificateur de profil de l’étape **@profile_id**1 pour. Tous les paramètres du profil sont alors retournés. Notez le nom de tous les paramètres à modifier ou à supprimer du profil.  
  
3.  Pour modifier la valeur d’un paramètre dans un profil, exécutez [sp_change_agent_profile & #40 ; Transact-SQL & #41;](/sql/relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql). Spécifiez l’identificateur de profil de l’étape **@profile_id**1 pour, le nom du paramètre à modifier **@property**pour et une nouvelle valeur pour le paramètre pour **@value**.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas modifier un profil d'agent existant pour qu'il devienne le profil par défaut d'un agent. Vous devez créer à la place un nouveau profil comme profil par défaut, comme illustré dans la procédure précédente.  
  
4.  Pour supprimer un paramètre d’un profil, exécutez [sp_drop_agent_parameter & #40 ; Transact-SQL & #41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql). Spécifiez l’identificateur de profil de l’étape **@profile_id** 1 pour et le nom du paramètre à supprimer **@parameter_name**pour.  
  
5.  Pour ajouter un nouveau paramètre à un profil, vous devez effectuer les opérations suivantes :  
  
    -   Interrogez la table [MSagentparameterlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msagentparameterlist-transact-sql) sur le serveur de distribution pour déterminer quels paramètres de profil peuvent être définis pour chaque type d’agent.  
  
    -   Sur le serveur de distribution, exécutez [sp_add_agent_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql). Spécifiez l’identificateur de profil de l’étape **@profile_id**1 pour, le nom d’un paramètre valide à **@parameter_name**ajouter pour et la valeur du paramètre pour **@parameter_value**.  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_tsql"></a> Pour supprimer un profil d'agent  
  
1.  Sur le serveur de distribution, exécutez [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql). Spécifiez l’une des valeurs suivantes **@agent_type**pour :  
  
    -   **1** - [Replication Snapshot Agent](replication-snapshot-agent.md)  
  
    -   **2** - [Replication Log Reader Agent](replication-log-reader-agent.md)  
  
    -   **3** - [Replication Distribution Agent](replication-distribution-agent.md)  
  
    -   **4** - [Replication Merge Agent](replication-merge-agent.md)  
  
    -   **9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)  
  
     Tous les profils pour le type d'agent spécifié sont retournés. Notez la valeur de **profile_id** dans le jeu de résultats pour le profil à supprimer.  
  
2.  Sur le serveur de distribution, exécutez [sp_drop_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql). Spécifiez l’identificateur de profil de l’étape **@profile_id**1 pour.  
  
###  <a name="to-use-agent-profiles-during-synchronization"></a><a name="Synch_tsql"></a> Pour utiliser les profils d'agent pendant la synchronisation  
  
1.  Sur le serveur de distribution, exécutez [sp_help_agent_profile &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql). Spécifiez l’une des valeurs suivantes **@agent_type**pour :  
  
    -   **1** - [Replication Snapshot Agent](replication-snapshot-agent.md)  
  
    -   **2** - [Replication Log Reader Agent](replication-log-reader-agent.md)  
  
    -   **3** - [Replication Distribution Agent](replication-distribution-agent.md)  
  
    -   **4** - [Replication Merge Agent](replication-merge-agent.md)  
  
    -   **9** - [Replication Queue Reader Agent](replication-queue-reader-agent.md)  
  
     Tous les profils pour le type d'agent spécifié sont retournés. Notez la valeur de `profile_name` dans le jeu de résultats pour le profil à utiliser.  
  
2.  Si l’agent est démarré à partir d’un travail de l’agent, modifiez l’étape du travail qui démarre l’agent `profile_name` pour spécifier la valeur obtenue à l’étape 1 après le paramètre de ligne de commande **-ProfileName** . Pour plus d’informations, consultez [Afficher et modifier des paramètres d’invite de commandes d’un Agent de réplication &#40;SQL Server Management Studio&#41;](view-and-modify-replication-agent-command-prompt-parameters.md).  
  
3.  Lors du démarrage de l’agent à partir de l’invite de commandes `profile_name` , spécifiez la valeur de obtenue à l’étape 1 après le paramètre de ligne de commande **-ProfileName** .  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Exemple (Transact-SQL)  
 Cet exemple crée un profil personnalisé pour l'Agent de fusion nommé **custom_merge**, modifie la valeur du paramètre **-UploadReadChangesPerBatch** , ajoute un nouveau paramètre **-ExchangeType** et retourne des informations sur le profil créé.  
  
 [!code-sql[HowTo#sp_addagentprofileparam](../../../snippets/tsql/SQL15/replication/howto/tsql/createperfparammerge.sql#sp_addagentprofileparam)]  
  
##  <a name="using-rmo"></a><a name="RMOProcedure"></a> Utilisation d'RMO  
  
###  <a name="to-create-a-new-agent-profile"></a><a name="Create_RMO"></a> Pour créer un profil d'agent  
  
1.  Créez une connexion avec le serveur de distribution en utilisant une instance de la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.AgentProfile>.  
  
3.  Définissez les propriétés suivantes de l'objet :  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> - nom du profil.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - une valeur <xref:Microsoft.SqlServer.Replication.AgentType> qui spécifie le type d'agent de réplication pour lequel le profil est créé.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> créé dans l'étape 1.  
  
    -   (Facultatif) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> - une description du profil.  
  
    -   (Facultatif) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A>- définit cette propriété sur `true` si tous les nouveaux travaux d'agent pour ce <xref:Microsoft.SqlServer.Replication.AgentType> utiliseront ce profil par défaut.  
  
4.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> pour créer le profil sur le serveur.  
  
5.  Une fois que le profil existe sur le serveur, vous pouvez le personnaliser en ajoutant, en supprimant ou en modifiant les valeurs des paramètres de l'agent de réplication.  
  
6.  Pour assigner le profil à un travail d'agent de réplication existant, appelez la méthode <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> . Passez le nom de la base de données de distribution pour *distributionDBName* et l'ID du travail pour *agentID*.  
  
###  <a name="to-modify-an-existing-agent-profile"></a><a name="Modify_RMO"></a> Pour modifier un profil d'agent existant  
  
1.  Créez une connexion avec le serveur de distribution en utilisant une instance de la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Passez l'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection> créé dans l'étape 1.  
  
3.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Si cette méthode retourne `false`, vérifiez que le serveur de distribution existe.  
  
4.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> . Passez une valeur <xref:Microsoft.SqlServer.Replication.AgentType> pour limiter les profils retournés à un type spécifique d'agent de réplication.  
  
5.  Obtenez l'objet <xref:Microsoft.SqlServer.Replication.AgentProfile> souhaité à partir du <xref:System.Collections.ArrayList>retourné, où la propriété <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> de l'objet correspond au nom de profil.  
  
6.  Appelez l'une des méthodes suivantes de <xref:Microsoft.SqlServer.Replication.AgentProfile> pour modifier le profil :  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> - ajoute un paramètre pris en charge au profil, où *name* est le nom du paramètre d'agent de réplication et *value* la valeur spécifiée. Pour énumérer tous les paramètres d'agent pris en charge pour un type d'agent donné, appelez la méthode <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> . Cette méthode retourne un <xref:System.Collections.ArrayList> des objets <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> qui représentent tous les paramètres pris en charge.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> - supprime un paramètre existant du profil, où *name* est le nom du paramètre d'agent de réplication. Pour énumérer tous les paramètres d'agent actuels définis pour le profil, appelez la méthode <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> . Cette méthode retourne un <xref:System.Collections.ArrayList> des objets <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> qui représentent le paramètre existant de ce profil.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> - modifie le paramètre d'un paramètre existant du profil, où *name* est le nom du paramètre d'agent et *newValue* la nouvelle valeur du paramètre. Pour énumérer tous les paramètres d'agent actuels définis pour le profil, appelez la méthode <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> . Cette méthode retourne un <xref:System.Collections.ArrayList> des objets <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> qui représentent le paramètre existant de ce profil. Pour énumérer toutes les valeurs des paramètres d'agent pris en charge, appelez la méthode <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> . Cette méthode retourne un <xref:System.Collections.ArrayList> des objets <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> qui représentent les valeurs prises en charge pour tous les paramètres.  
  
###  <a name="to-delete-an-agent-profile"></a><a name="Delete_RMO"></a> Pour supprimer un profil d'agent  
  
1.  Créez une connexion avec le serveur de distribution en utilisant une instance de la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.AgentProfile>. Définissez le nom du profil pour <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> et le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à partir de l'étape 1 de <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Si cette méthode retourne `false`, le nom spécifié était incorrect ou le profil n'existe pas sur le serveur.  
  
4.  Vérifiez que la propriété <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> a la valeur <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>, ce qui indique un profil de client. Vous ne devez pas supprimer un profil qui a une valeur de <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> pour <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>.  
  
5.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> pour supprimer le profil défini par l'utilisateur représenté par cet objet du serveur.  
  
##  <a name="follow-up-after-changing-agent-parameters"></a><a name="FollowUp"></a> Suivi : Après avoir changé les paramètres de l’Agent  
 Les modifications apportées aux paramètres prennent effet au prochain démarrage de l'Agent. Si l'Agent fonctionne en continu, vous devez l'arrêter, puis le redémarrer.  
  
## <a name="see-also"></a>Voir aussi  
 [Profils de l’agent de réplication](replication-agent-profiles.md)   
 [Agent d’instantané de réplication](replication-snapshot-agent.md)   
 [Agent de lecture du journal de réplication](replication-log-reader-agent.md)   
 [Agent de distribution de réplication](replication-distribution-agent.md)   
 [Agent de fusion de réplication](replication-merge-agent.md)   
 [Agent de lecture de la file d'attente de réplication](replication-queue-reader-agent.md)  
  
  
