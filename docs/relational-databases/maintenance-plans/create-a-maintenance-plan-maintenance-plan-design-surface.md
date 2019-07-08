---
title: Créer un plan de maintenance (aire de conception de plan de maintenance) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Maintenance Plan Design Surface
ms.assetid: 2ef803ee-a9f8-454a-ad63-fedcbe6838d1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 78f09611e71c39902e81580d752d302fee604be9
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67584143"
---
# <a name="create-a-maintenance-plan-maintenance-plan-design-surface"></a>Créer un plan de maintenance (aire de conception de plan de maintenance)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique explique comment créer un plan de maintenance de serveur unique ou multiserveur à l'aide de l'aire de conception de plan de maintenance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. L' **Assistant Plan de maintenance** est conseillé pour créer des plans de maintenance de base, tandis que l'aire de conception permet d'utiliser un flux de travail optimisé.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   [Création d'un plan de maintenance à l'aide de l'aire de conception de plan de maintenance](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Pour créer un plan de maintenance multiserveurs, vous devez configurer un environnement multiserveurs contenant un serveur maître et un ou plusieurs serveurs cibles. Les plans de maintenance multiserveurs doivent être créés et conservés sur le serveur maître. Ces plans peuvent être consultés mais ne peuvent pas être conservés sur les serveurs cibles.  
  
-   Les membres du rôle **db_ssisadmin** et du rôle **dc_admin** peuvent être en mesure d’élever leurs privilèges à **sysadmin**. Cette élévation de privilège est possible, car ces rôles peuvent modifier les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , qui sont exécutables par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec le contexte de sécurité **sysadmin** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Pour empêcher cette élévation de privilège lors de l’exécution de plans de maintenance, de jeux d’éléments de collecte de données et d’autres packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , configurez les travaux de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent qui exécutent des packages de façon à utiliser un compte proxy doté de privilèges limités ou ajoutez uniquement des membres **sysadmin** aux rôles **db_ssisadmin** et **dc_admin** .  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Pour créer ou gérer des plans de maintenance, vous devez être membre du rôle serveur fixe **sysadmin** . L'Explorateur d'objets affiche uniquement le nœud **Plans de maintenance** pour les utilisateurs membres du rôle serveur fixe **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de l'aire de conception de plan de maintenance  
  
#### <a name="to-create-a-maintenance-plan"></a>Pour créer un plan de maintenance  
  
1.  Dans l'Explorateur d'objets, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez créer un plan de maintenance.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez avec le bouton droit sur le dossier **Plans de maintenance** et sélectionnez **Nouveau plan de maintenance**.  
  
4.  Dans la boîte de dialogue **Nouveau plan de maintenance** , dans la zone **Nom** , tapez un nom pour le plan, puis cliquez sur **OK**. Vous ouvrez ainsi la boîte à outils et l’aire *nom_plan_maintenance* **[Conception]** avec le sous-plan **Sous-plan_1** créé dans la grille principale.  
  
     Les options suivantes sont disponibles dans l'en-tête de l'aire de conception.  
  
     **Ajouter le sous-plan**  
     Ajoute un sous-plan que vous pouvez configurer.  
  
     **Propriétés du sous-plan**  
     Affiche la boîte de dialogue **Propriétés du sous-plan** du sous-plan sélectionné dans la grille principale. Vous pouvez également double-cliquer sur un sous-plan dans la grille pour afficher la boîte de dialogue **Propriétés du sous-plan** . Pour plus d'informations sur cette boîte de dialogue, voir ci-dessous.  
  
     **Supprimer le sous-plan sélectionné**  
     Supprime le sous-plan sélectionné.  
  
     **Planification du sous-plan**  
     Affiche la boîte de dialogue **Nouvelle planification du travail** du sous-plan sélectionné.  
  
     **Supprimer la planification**  
     Supprime une planification du sous-plan sélectionné.  
  
     **Gérer les connexion**  
     Affiche la boîte de dialogue **Gérer les connexions** . Permet d'ajouter des connexions d'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supplémentaires au plan de maintenance. Pour plus d'informations sur cette boîte de dialogue, voir ci-dessous.  
  
     **Création de rapport et enregistrement**  
     Affiche la boîte de dialogue **Création de rapport et enregistrement** . Pour plus d'informations sur cette boîte de dialogue, voir ci-dessous.  
  
     **Serveurs**  
     Affichez la boîte de dialogue **Serveurs** qui permet de sélectionner les serveurs où sont exécutées les tâches du sous-plan. Cette option est activée uniquement sur des serveurs maîtres dans des environnements multiserveurs. Pour plus d’informations, consultez [Créer un environnement multiserveur](../../ssms/agent/create-a-multiserver-environment.md) et [Plan de maintenance &#40;Serveurs&#41;](../../relational-databases/maintenance-plans/maintenance-plan-servers.md).  
  
     **Name**  
     Affichez le nom du plan de maintenance. Pour les nouveaux plans de maintenance, le nom est spécifié dans une boîte de dialogue avant l'ouverture du concepteur de plan de maintenance. Pour renommer un plan de maintenance, cliquez dessus avec le bouton droit dans l’Explorateur d’objets, puis cliquez sur **Renommer**.  
  
     **Description**  
     Permet d'afficher ou de spécifier une description du plan de maintenance. La longueur maximale de la description est 512 caractères.  
  
     **Aire du concepteur**  
     Conception et entretien des plans de maintenance. Utilisez l'aire du concepteur pour ajouter des tâches de maintenance à un plan, supprimer des tâches d'un plan, spécifier des liens de précédence entre des tâches et indiquer les branchements et le parallélisme des tâches.  
  
     Un lien de précédence entre deux tâches établit une relation entre ces tâches. La seconde tâche (la *tâche dépendante*) s’exécute seulement si le résultat d’exécution de la première tâche (la *tâche prioritaire*) correspond aux critères spécifiés. En général, le résultat d'exécution spécifié est **Succès**, **Échec**ou **À l'achèvement**. Pour plus d'informations, consultez l'étape **8** ci-dessous.  
  
5.  Dans l’en-tête de l’aire de conception, double-cliquez sur **Sous-plan_1** et entrez un nom et une description pour le sous-plan dans la boîte de dialogue **Propriétés du sous-plan** .  
  
     Les options suivantes sont disponibles dans la boîte de dialogue **Propriétés du sous-plan** .  
  
     **Name**  
     Nom du sous-plan.  
  
     **Description**  
     Brève description du sous-plan.  
  
     **Planifier**  
     Indique pour quelle planification le sous-plan sera exécuté. Cliquez sur **Planification du sous-plan** pour ouvrir la boîte de dialogue **Nouvelle planification du travail** . Cliquez sur **Supprimer la planification** pour supprimer la planification du sous-plan.  
  
     Liste**Exécuter en tant que**  
     Sélectionnez le compte à utiliser pour exécuter cette sous-tâche.  
  
6.  Cliquez sur l'icône **Planification du sous-plan** pour entrer les informations de la planification dans la boîte de dialogue **Nouvelle planification du travail** .  
  
7.  Pour générer le sous-plan, faites glisser les éléments de flux des tâches de la **Boîte à outils** vers l'aire de conception du plan. Double-cliquez sur des tâches pour ouvrir les boîtes de dialogue permettant de configurer les options des tâches.  
  
     Les tâches de plan de maintenance suivantes sont disponibles dans la **Boîte à outils**:  
  
    -   **Tâche Sauvegarder la base de données**  
  
    -   **Tâche Vérifier l'intégrité de la base de données**  
  
    -   **Tâche Exécuter le travail de l'Agent SQL Server**  
  
    -   **Tâche Exécuter l'instruction T-SQL**  
  
    -   **Tâche de nettoyage d'historique**  
  
    -   **Tâche de nettoyage de maintenance**  
  
    -   **Tâche Notifier l'opérateur**  
  
    -   **Tâche Reconstruire l'index**  
  
    -   **Tâche Réorganiser l'index**  
  
    -   **Tâche Réduire la base de données**  
  
    -   **Tâche Mettre à jour les statistiques**  
  
     Pour ajouter des tâches à la **Boîte à outils**:  
  
    1.  Dans le menu **Outils** , cliquez sur **Choisir des éléments de boîte à outils**.  
  
    2.  Sélectionnez les outils que vous souhaitez voir afficher dans la **Boîte à outils**, puis cliquez sur **OK**.  
  
     Les tâches de plan de maintenance que vous ajoutez à la **Boîte à outils** sont également disponibles dans l' **Assistant Plan de maintenance**. Pour plus d’informations sur les différentes tâches présentées ci-dessus, consultez [Utilisation de l’Assistant Plan de maintenance](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) sous **Démarrer l’Assistant Plan de maintenance**.  
  
8.  Pour définir un flux de travail entre les tâches :  
  
    1.  Cliquez avec le bouton droit sur la tâche prioritaire et sélectionnez **Ajouter une contrainte de précédence**.  
  
    2.  Dans la boîte de dialogue **Flux de contrôle** , dans la liste **À** , sélectionnez la tâche dépendante et cliquez sur **OK**.  
  
    3.  Double-cliquez sur le connecteur entre les deux tâches pour ouvrir la boîte de dialogue **Éditeur de contrainte de précédence** .  
  
         Les options suivantes sont disponibles dans la boîte de dialogue **Éditeur de contrainte de précédence** .  
  
         **Option de contrainte**  
         Définit la manière dont une contrainte fonctionne entre deux tâches.  
  
         Liste**Opération d’évaluation**  
         Spécifiez l'opération d'évaluation utilisée par la contrainte de précédence. Ces opérations sont : **Contrainte**, **Expression**, **Expression et contrainte** et **Expression ou contrainte**.  
  
         Liste**Valeur**  
         Spécifiez la valeur de contrainte : **Réussite**, **Échec** ou **À l'achèvement**. **Réussite** est la valeur par défaut.  
  
        > [!NOTE]  
        >  La ligne de contrainte de précédence est verte pour **Réussite**, rouge pour **Échec**et bleue pour **À l’achèvement**.  
  
         **Expression**  
         Si vous utilisez les opérations **Expression**, **Expression et contrainte**ou **Expression ou contrainte**, tapez une expression. L'expression doit prendre une valeur de type Boolean.  
  
         **Tester**  
         Validez l'expression.  
  
         **Contraintes multiples**  
         Définissez la manière dont plusieurs contraintes interopèrent pour contrôler l'exécution de la tâche contrainte.  
  
         **ET logique**  
         Sélectionnez cette option pour spécifier que plusieurs contraintes de précédence sur le même exécutable doivent être évaluées ensemble. Toutes les contraintes doivent prendre la valeur True. Cette option est celle par défaut.  
  
        > [!NOTE]  
        >  Ce type de contrainte de précédence s'affiche sous forme de ligne pleine verte, rouge ou bleue.  
  
         **OU logique**  
         Sélectionnez cette option pour spécifier que plusieurs contraintes de précédence sur le même exécutable doivent être évaluées ensemble. Au moins une contrainte doit prendre la valeur True.  
  
        > [!NOTE]  
        >  Ce type de contrainte de précédence s'affiche sous forme de ligne pointillée verte, rouge ou bleue.  
  
9. Pour ajouter un autre sous-plan qui contient les tâches exécutées sur une autre planification, cliquez sur **Ajouter un sous-plan** dans la barre d'outils pour ouvrir la boîte de dialogue **Propriétés du sous-plan** .  
  
10. Pour ajouter des connexions à d'autres serveurs :  
  
    1.  Dans la barre d'outils de l'aire de conception, cliquez sur **Gérer les connexions**.  
  
    2.  Dans la boîte de dialogue **Gérer les connexions** , cliquez sur **Ajouter**.  
  
    3.  Dans la boîte de dialogue **Propriétés de connexion** , dans la zone **Nom de la connexion** , entrez le nom de la connexion que vous créez.  
  
    4.  Sous **Spécifiez les éléments suivants pour vous connecter aux données de SQL Server**, dans la zone **Sélectionnez ou entrez un nom de serveur**, entrez le nom du serveur SQL Server à utiliser ou cliquez sur les points de suspension **(…)** et sélectionnez un serveur dans la boîte de dialogue **SQL Server**. Si vous sélectionnez un serveur dans la boîte de dialogue **SQL Server** , cliquez sur **OK**.  
  
    5.  Sous **Entrez des informations pour vous connecter au serveur**, sélectionnez **Utiliser la sécurité intégrée de Windows NT** ou **Utiliser un nom d'utilisateur et un mot de passe spécifiques**. Si vous choisissez d'utiliser un nom d'utilisateur et un mot de passe spécifiques, entrez ces informations dans les zones **Nom d'utilisateur** et **Mot de passe** , respectivement.  
  
    6.  Dans la boîte de dialogue **Propriétés de connexion** , cliquez sur **OK**.  
  
    7.  Dans la boîte de dialogue **Gérer les connexions** , cliquez sur **Fermer**.  
  
11. Pour spécifier des options de création de rapports :  
  
    1.  Dans la barre d'outils de l'aire de conception, cliquez sur **Création de rapport et enregistrement**.  
  
    2.  Dans la boîte de dialogue **Création de rapport et enregistrement** , sous **Création de rapports**, sélectionnez **Générer un rapport de fichier texte** ou **Envoyer le rapport à un destinataire de messagerie** ou les deux.  
  
        1.  Si vous sélectionnez **Générer un rapport de fichier texte**, sélectionnez **Créer un nouveau fichier** ou **Ajouter au fichier**.  
  
        2.  En fonction de la sélection ci-dessus, entrez le nom et le chemin complet du nouveau fichier ou du fichier à ajouter dans les zones **Dossier** ou **Nom de fichier** . Vous pouvez également cliquer sur les points de suspension **(...)** , puis sélectionner le chemin du dossier ou le nom de fichier à partir des boîtes de dialogue **Localiser le dossier -** _nom\_serveur_ ou **Rechercher les fichiers de la base de données -** _nom\_serveur_.  
  
        3.  Si vous sélectionnez **Envoyer le rapport à un destinataire de messagerie**, dans la liste **Opérateur d'agent** , sélectionnez le destinataire du rapport envoyé par messagerie électronique.  
  
            > [!NOTE]  
            >  L'Agent SQL Server doit être configuré pour utiliser la messagerie de base de données afin d'envoyer le message. Pour plus d'informations, consultez [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
    3.  Pour enregistrer des informations plus détaillées, sous **Enregistrement**, sélectionnez **Enregistrer les informations étendues**.  
  
    4.  Pour écrire les informations de résultats de plan de maintenance sur un autre serveur, sélectionnez **Se connecter à un serveur distant** , puis sélectionnez une connexion au serveur dans la liste **Connexion** , ou cliquez sur **Nouveau** pour entrer les informations de connexion dans la boîte de dialogue **Propriétés de connexion** .  
  
    5.  Dans la boîte de dialogue **Création de rapport et enregistrement** , cliquez sur **OK**.  
  
12. Pour consulter les résultats dans la visionneuse du fichier journal, dans **l’Explorateur d’objets**, cliquez avec le bouton droit sur le dossier **Plans de maintenance** ou sur le plan de maintenance spécifique et sélectionnez **Afficher l’historique**.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     The following options are available on the **Log File Viewer -**_server\_name_ dialog box.  
  
     **Load Log**  
     Open a dialog box where you can specify a log file to load.  
  
     **Export**  
     Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.  
  
     **Refresh**  
     Refresh the view of the selected logs. The **Refresh** button rereads the selected logs from the target server while applying any filter settings.  
  
     **Filter**  
     Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.  
  
     **Search**  
     Search the log file for specific text. Searching with wildcard characters is not supported.  
  
     **Stop**  
     Stops loading the log file entries. For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.  
  
     **Log file summary**  
     This information panel displays a summary of the log file filtering. If the file is not filtered, you will see the following text, **No filter applied**. If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.  
  
     **Date**  
     Displays the date of the event.  
  
     **Source**  
     Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example). This does not appear for all log types.  
  
     **Message**  
     Displays any messages associated with the event.  
  
     **Log Type**  
     Displays the type of log to which the event belongs. All selected logs appear in the log file summary window.  
  
     **Log Source**  
     Displays a description of the source log in which the event is captured.  
  
     **Selected row details**  
     Select a row to display additional details about the selected event row at the bottom of the page. The columns can be reordered by dragging them to new locations in the grid. The columns can be resized by dragging the column separator bars in the grid header to the left or right. Double-click the column separator bars in the grid header to automatically size the column to the content width.  
  
     **Instance**  
     The name of the instance on which the event occurred. This is displayed as *computer name*\\*instance name*.  
  
  
