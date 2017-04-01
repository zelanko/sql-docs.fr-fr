---
title: "Utiliser des profils d&#39;agent de r&#233;plication | Microsoft Docs"
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
  - "replication [SQL Server], agents and profiles"
  - "replication agent profiles [SQL Server]"
  - "agents [SQL Server replication], profiles"
  - "profils [SQL Server], agents de réplication"
ms.assetid: 9c290a88-4e9f-4a7e-aab5-4442137a9918
caps.latest.revision: 49
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 49
---
# Utiliser des profils d&#39;agent de r&#233;plication
  Cette rubrique explique comment utiliser les profils de l'Agent de réplication dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou d'objets RMO (Replication Management Objects). Le comportement de chaque agent de réplication est contrôlé par un jeu de paramètres que vous pouvez configurer dans un profil de l'Agent. Chaque agent possède un profil par défaut et certains possèdent d'autres profils prédéfinis ; un Agent ne peut avoir qu'un profil actif à tout moment.  
  
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
  
-   **Suivi :**  [Après avoir modifié les paramètres de l'Agent](#FollowUp)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
###  <a name="Access_SSMS"></a> Pour accéder à la boîte de dialogue Profils d'Agent à partir de SQL Server Management Studio  
  
1.  Sur le **Général** page de le **Propriétés du serveur de distribution - \< serveur de distribution>** boîte de dialogue, cliquez sur **profil par défaut est**.  
  
#### Pour accéder à la boîte de dialogue Profils d'Agent à partir du moniteur de réplication  
  
-   Pour ouvrir la boîte de dialogue pour tous les agents, cliquez sur un serveur de publication, puis cliquez sur **profils d’Agent**.  
  
-   Pour ouvrir la boîte de dialogue d'un seul Agent  
  
    1.  Développez un groupe Serveur de publication dans le volet gauche du moniteur de réplication, développez un serveur de publication puis cliquez sur une publication.  
  
    2.  Pour les profils de l’Agent de Distribution et l’Agent de fusion, cliquez sur un abonnement sur le **tous les abonnements** onglet, puis cliquez sur **profil d’Agent**. Pour les autres agents, cliquez sur l’agent sur le **Agents** onglet, puis cliquez sur **profil d’Agent**.  
  
###  <a name="Specify_SSMS"></a> Pour spécifier un profil d'un Agent  
  
1.  Si la boîte de dialogue **Profils d'Agent** affiche les profils de plusieurs agents, sélectionnez un Agent.  
  
2.  Sélectionnez un profil dans la colonne **Valeur par défaut pour nouveau** de la grille **Profils d'Agent** . Par défaut, le profil est uniquement appliqué aux agents pour les nouveaux abonnements et publications.  
  
3.  Pour que tous les agents du type sélectionné pour les abonnements ou publications existants utilisent ce profil, cliquez sur **Modifier les Agents existants**.  
  
###  <a name="Modify_SSMS"></a> Pour afficher et modifier les paramètres associés à un profil  
  
1.  Si la boîte de dialogue **Profils d'Agent** affiche les profils de plusieurs agents, sélectionnez un Agent.  
  
2.  Cliquez sur le bouton des propriétés (**...**) en regard d’un profil.  
  
3.  Afficher les paramètres et les valeurs dans le **\< nomprofil> Propriétés de profil** boîte de dialogue.  
  
    -   Les paramètres des profils définis par l'utilisateur peuvent être modifiés, ce qui n'est pas le cas des profils système prédéfinis.  
  
    -   Pour afficher tous les paramètres relatifs à un Agent, désactivez la case à cocher **Afficher uniquement les paramètres utilisés dans ce profil** . Pour plus d'informations sur les paramètres des Agents, consultez les liens à la fin de cette rubrique.  
  
4.  Cliquez sur **Fermer**.  
  
###  <a name="Create_SSMS"></a> Pour créer un profil défini par l'utilisateur  
  
1.  Si la boîte de dialogue **Profils d'Agent** affiche les profils de plusieurs agents, sélectionnez un Agent.  
  
2.  Cliquez sur **Nouveau**.  
  
3.  Dans la boîte de dialogue d'initialisation **Nouveau profil de l'Agent** , sélectionnez un profil existant qui servira de base au nouveau profil.  
  
4.  Dans la boîte de dialogue **Nouveau profil de l'Agent** , entrez des valeurs dans les zones de texte **Nom** et **Description** .  
  
5.  Modifiez les paramètres pour adapter le profil à vos besoins. Pour afficher tous les paramètres relatifs à un Agent, désactivez la case à cocher **Afficher uniquement les paramètres utilisés dans ce profil** . Pour plus d'informations sur les paramètres des Agents, consultez les liens à la fin de cette rubrique.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
###  <a name="Delete_SSMS"></a> Pour supprimer un profil défini par l'utilisateur  
  
1.  Si la boîte de dialogue **Profils d'Agent** affiche les profils de plusieurs agents, sélectionnez un Agent.  
  
2.  Si un profil est associé à un ou plusieurs agents, modifiez le profil de ceux-ci :  
  
    1.  Sélectionnez un autre profil dans la grille **Profils d'Agent** .  
  
    2.  Cliquez sur **Modifier les Agents existants**.  
  
        > [!NOTE]  
        >  Cela modifie le profil de tous les agents du type sélectionné pour les publications ou abonnements existants et pas seulement ceux qui utilisent le profil à supprimer.  
  
3.  Cliquez sur le profil à supprimer, puis sur **Supprimer**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
###  <a name="Create_tsql"></a> Pour créer un profil d'agent  
  
1.  Sur le serveur de distribution, exécutez [sp_add_agent_profile & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md). Spécifiez **@name**, une valeur de **1** pour **@profile_type**, et une de ces valeurs pour **@agent_type**:  
  
    -   **1** - [Agent capture instantanée des réplications](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [Agent de lecture du journal de réplication](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [Agent de Distribution](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [Agent de fusion de réplication](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [Agent de lecture de file d’attente de réplication](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Si ce profil devient le nouveau profil par défaut pour son type d'agent de réplication, spécifiez une valeur de **1** pour **@default**. L’identificateur pour le nouveau profil est retourné à l’aide de la **@profile_id** paramètre de sortie. Cela crée un nouveau profil avec un jeu de paramètres de profil basé sur le profil par défaut pour le type d'agent donné.  
  
2.  Après avoir créé le nouveau profil, ajoutez, supprimez ou modifiez les paramètres par défaut pour personnaliser le profil.  
  
###  <a name="Modify_tsql"></a> Pour modifier un profil d'agent existant  
  
1.  Sur le serveur de distribution, exécutez [sp_help_agent_profile & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md). Spécifiez une des valeurs suivantes pour **@agent_type**:  
  
    -   **1** - [Agent capture instantanée des réplications](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [Agent de lecture du journal de réplication](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [Agent de Distribution](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [Agent de fusion de réplication](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [Agent de lecture de file d’attente de réplication](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Tous les profils pour le type d'agent spécifié sont retournés. Notez la valeur de **profile_id** dans le jeu de résultats pour le profil à modifier.  
  
2.  Sur le serveur de distribution, exécutez [sp_help_agent_parameter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md). Spécifier l’identificateur du profil de l’étape 1 pour **@profile_id**. Tous les paramètres du profil sont alors retournés. Notez le nom de tous les paramètres à modifier ou à supprimer du profil.  
  
3.  Pour modifier la valeur d’un paramètre dans un profil, exécutez [sp_change_agent_profile & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md). Spécifier l’identificateur du profil de l’étape 1 pour **@profile_id**, le nom de paramètre pour le modifier pour **@property**, et une nouvelle valeur pour le paramètre **@value**.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas modifier un profil d'agent existant pour qu'il devienne le profil par défaut d'un agent. Vous devez créer à la place un nouveau profil comme profil par défaut, comme illustré dans la procédure précédente.  
  
4.  Pour supprimer un paramètre à partir d’un profil, exécutez [sp_drop_agent_parameter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md). Spécifier l’identificateur du profil de l’étape 1 pour **@profile_id** et le nom du paramètre à supprimer pour **@parameter_name**.  
  
5.  Pour ajouter un nouveau paramètre à un profil, vous devez effectuer les opérations suivantes :  
  
    -   Requête du [MSagentparameterlist & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-tables/msagentparameterlist-transact-sql.md) table sur le serveur de distribution pour déterminer quels paramètres de profil peuvent être définies pour chaque type d’agent.  
  
    -   Sur le serveur de distribution, exécutez [sp_add_agent_parameter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md). Spécifier l’identificateur du profil de l’étape 1 pour **@profile_id**, le nom d’un paramètre valid pour ajouter pour **@parameter_name**, et la valeur du paramètre pour **@parameter_value**.  
  
###  <a name="Delete_tsql"></a> Pour supprimer un profil d'agent  
  
1.  Sur le serveur de distribution, exécutez [sp_help_agent_profile & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md). Spécifiez une des valeurs suivantes pour **@agent_type**:  
  
    -   **1** - [Agent capture instantanée des réplications](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [Agent de lecture du journal de réplication](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [Agent de Distribution](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [Agent de fusion de réplication](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [Agent de lecture de file d’attente de réplication](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Tous les profils pour le type d'agent spécifié sont retournés. Notez la valeur de **profile_id** dans le jeu de résultats pour le profil à supprimer.  
  
2.  Sur le serveur de distribution, exécutez [sp_drop_agent_profile & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md). Spécifier l’identificateur du profil de l’étape 1 pour **@profile_id**.  
  
###  <a name="Synch_tsql"></a> Pour utiliser les profils d'agent pendant la synchronisation  
  
1.  Sur le serveur de distribution, exécutez [sp_help_agent_profile & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md). Spécifiez une des valeurs suivantes pour **@agent_type**:  
  
    -   **1** - [Agent capture instantanée des réplications](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [Agent de lecture du journal de réplication](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [Agent de Distribution](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [Agent de fusion de réplication](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [Agent de lecture de file d’attente de réplication](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Tous les profils pour le type d'agent spécifié sont retournés. Notez la valeur de **nom_profil** dans le jeu de résultats pour le profil à utiliser.  
  
2.  Si l’agent est démarré à partir d’un travail d’agent, modifiez l’étape de travail qui démarre l’agent pour spécifier la valeur de **nom_profil** obtenu à l’étape 1 après le **- ProfileName** paramètre de ligne de commande. Pour plus d’informations, consultez [Afficher et modifier des paramètres de ligne de commande d’Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md).  
  
3.  Lors du démarrage de l’agent à partir de l’invite de commandes, spécifiez la valeur de **nom_profil** obtenu à l’étape 1 après le **- ProfileName** paramètre de ligne de commande.  
  
###  <a name="TsqlExample"></a> Exemple (Transact-SQL)  
 Cet exemple crée un profil personnalisé pour l’Agent de fusion nommé **custom_merge**, modifie la valeur de la **- UploadReadChangesPerBatch** paramètre, ajoute un nouveau **- ExchangeType** paramètre et retourne des informations sur le profil est créé.  
  
 [!code-sql[HowTo#sp_addagentprofileparam](../../../relational-databases/replication/codesnippet/tsql/work-with-replication-ag_1.sql)]  
  
##  <a name="RMOProcedure"></a> Utilisation d'RMO  
  
###  <a name="Create_RMO"></a> Pour créer un profil d'agent  
  
1.  Créer une connexion au serveur de distribution à l’aide d’une instance de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.AgentProfile> (classe).  
  
3.  Définissez les propriétés suivantes de l'objet :  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> -le nom du profil.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> : <xref:Microsoft.SqlServer.Replication.AgentType> valeur qui spécifie le type d’agent de réplication pour lequel le profil est créé.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> créé à l’étape 1.  
  
    -   (Facultatif) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> -description du profil.  
  
    -   (Facultatif) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> -Affectez à cette propriété **true** si tous les nouveaux travaux d’agent pour ce <xref:Microsoft.SqlServer.Replication.AgentType> vont utiliser ce profil par défaut.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> pour créer le profil sur le serveur.  
  
5.  Une fois que le profil existe sur le serveur, vous pouvez le personnaliser en ajoutant, en supprimant ou en modifiant les valeurs des paramètres de l'agent de réplication.  
  
6.  Pour attribuer le profil à un travail de l’agent de réplication existant, appelez le <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> (méthode). Passez le nom de la base de données de distribution pour *distributionDBName* et l'ID du travail pour *agentID*.  
  
###  <a name="Modify_RMO"></a> Pour modifier un profil d'agent existant  
  
1.  Créer une connexion au serveur de distribution à l’aide d’une instance de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.ReplicationServer> classe. Passez le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet créé à l’étape 1.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode. Si cette méthode retourne **false**, vérifiez que le serveur de distribution existe.  
  
4.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> méthode. Passez un <xref:Microsoft.SqlServer.Replication.AgentType> valeur permettant de limiter les profils retournés à un type spécifique de l’agent de réplication.  
  
5.  Obtenir l’élément <xref:Microsoft.SqlServer.Replication.AgentProfile> objet retourné <xref:System.Collections.ArrayList>, où le <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> propriété de l’objet correspond au nom de profil.  
  
6.  Appelez une des méthodes suivantes de <xref:Microsoft.SqlServer.Replication.AgentProfile> pour modifier le profil :  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> -ajoute un paramètre pris en charge pour le profil, où *nom* est le nom du paramètre de l’agent de réplication et *valeur* est la valeur spécifiée. Pour énumérer tous les paramètres d’agent prises en charge pour un type d’agent donné, appelez le <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> (méthode). Cette méthode retourne un <xref:System.Collections.ArrayList> de <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> les objets qui représentent les paramètres tous pris en charge.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> -supprime un paramètre existant du profil, où *nom* est le nom du paramètre de l’agent de réplication. Pour énumérer tous les paramètres de l’agent en cours définies pour le profil, appelez le <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> méthode. Cette méthode retourne un <xref:System.Collections.ArrayList> de <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> objets qui représentent le paramètre existant pour ce profil.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> -modifie le paramètre d’un paramètre existant dans le profil, où *nom* est le nom du paramètre de l’agent et *newValue* est la valeur à laquelle le paramètre est modifié. Pour énumérer tous les paramètres de l’agent en cours définies pour le profil, appelez le <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> méthode. Cette méthode retourne un <xref:System.Collections.ArrayList> de <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> objets qui représentent le paramètre existant pour ce profil. Pour énumérer toutes les prises en charge de paramètres d’agent, appelez le <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> (méthode). Cette méthode retourne un <xref:System.Collections.ArrayList> de <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> les objets qui représentent les valeurs prises en charge pour tous les paramètres.  
  
###  <a name="Delete_RMO"></a> Pour supprimer un profil d'agent  
  
1.  Créer une connexion au serveur de distribution à l’aide d’une instance de la <xref:Microsoft.SqlServer.Management.Common.ServerConnection> (classe).  
  
2.  Créez une instance de la <xref:Microsoft.SqlServer.Replication.AgentProfile> (classe). Définissez le nom du profil pour <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> et <xref:Microsoft.SqlServer.Management.Common.ServerConnection> à l’étape 1 pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Appelez le <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> méthode. Si cette méthode retourne **false**, le nom spécifié était incorrect ou le profil n’existe pas sur le serveur.  
  
4.  Vérifiez que le <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> est définie sur <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>, ce qui indique un profil de client. Ne supprimez pas un profil qui a la valeur <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> pour <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>.  
  
5.  Appelez le <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> méthode pour supprimer le profil défini par l’utilisateur représenté par cet objet à partir du serveur.  
  
##  <a name="FollowUp"></a> Suivi : Après avoir modifié les paramètres de l'Agent  
 Les modifications apportées aux paramètres prennent effet au prochain démarrage de l'Agent. Si l'Agent fonctionne en continu, vous devez l'arrêter, puis le redémarrer.  
  
## Voir aussi  
 [Profils de l'Agent de réplication](../../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Agent d'instantané de réplication](../../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [Agent de lecture du journal des réplications](../../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Agent de distribution de réplication](../../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Agent de fusion de réplication](../../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Agent de lecture de la file d'attente de réplication](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
  