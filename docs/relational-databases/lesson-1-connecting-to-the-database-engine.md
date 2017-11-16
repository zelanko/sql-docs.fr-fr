---
title: "Leçon 1 : Connexion au moteur de base de données | Microsoft Docs"
ms.custom: 
ms.date: 08/05/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: e8db82f0-50ed-4531-9209-940006ed34cb
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: a005345fe51f1b1b1479f854c636464b728429f7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="lesson-1-connecting-to-the-database-engine"></a>Leçon 1 : Connexion au moteur de base de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

 > Pour accéder au contenu relatif aux versions précédentes de SQL Server, consultez [Leçon 1 : Connexion au moteur de base de données](https://msdn.microsoft.com/en-US/library/ms345332(SQL.120).aspx).

<a name="when-you-install-the-includessdenoversionincludesssdenoversion-mdmd-the-tools-that-are-installed-depend-upon-the-edition-and-your-setup-choices-this-lesson-reviews-the-principal-tools-and-shows-you-how-to-connect-and-perform-a-basic-function-authorizing-more-users"></a>Les outils installés lors de l'installation du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]dépendent de l'édition du produit et de la configuration choisies. Cette leçon passe en revue les outils principaux et décrit comment faire pour se connecter et exécuter une fonction de base (autorisation de plusieurs utilisateurs).  
 -  
 <a name="-this-lesson-contains-the-following-tasks"></a>Cette leçon contient les tâches suivantes :  
 -  
 <a name="-----tools-for-getting-startedtools"></a>--   [Outils de mise en route](#tools)  
 -  
 <a name="-----connecting-with-management-studioconnect"></a>--   [Connexion à Management Studio](#connect)  
 -  
 <a name="-----authorizing-additional-connectionsadditional"></a>--   [Autorisation de connexions supplémentaires](#additional)  
 -  
 -## <a name="tools"></a>Outils de mise en route  
 -Le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] est fourni avec un éventail d'outils. Cette rubrique décrit les premiers outils dont vous aurez besoin et vous aide à choisir l'outil adapté à votre travail. Vous pouvez accéder à tous les outils à partir du menu **Démarrer** . Certains outils, comme [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], ne sont pas installés par défaut. Vous devez sélectionner les outils en tant qu'éléments inhérents aux composants clients lors de l'installation. Pour obtenir une description complète des outils décrits ci-dessous, recherchez-les dans la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] contient uniquement un sous-ensemble des outils.  
 -  
 -### Outils de base  
 -  
 --   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (SSMS) est l’outil principal employé pour administrer le [!INCLUDE[ssDE](../includes/ssde-md.md)] et écrire le code [!INCLUDE[tsql](../includes/tsql-md.md)]. Il est hébergé dans le shell [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. SSMS peut être téléchargé gratuitement depuis le [Centre de téléchargement Microsoft](https://msdn.microsoft.com/library/mt238290.aspx). La version la plus récente peut être utilisée avec les versions antérieures du [!INCLUDE[ssDE_md](../includes/ssde-md.md)].  
 -  
 Le Gestionnaire de configuration --   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est installé avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les outils clients. Il vous permet d'activer les protocoles serveur, configurer des options de protocole (notamment les ports TCP), configurer le démarrage automatique de services serveur et configurer des ordinateurs clients pour définir leur mode de connexion selon vos préférences. Cet outil configure les éléments de connectivité les plus avancés mais n'active pas les fonctionnalités.  
 -  
 -### Exemple de base de données  
 -Les exemples de bases de données et les exemples ne sont pas fournis avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La plupart des exemples décrits dans la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilisent l'exemple de base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] .  
 -  
 -##### Pour démarrer SQL Server Management Studio  
 -  
 -- Dans les versions actuelles de Windows, dans la page **Accueil** , tapez SSMS, puis cliquez sur **Microsoft SQL Server Management Studio**.  
 --   Si vous utilisez une version ancienne de Windows, dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], puis cliquez sur **SQL Server Management Studio**.  
 -  
 -##### Pour démarrer le Gestionnaire de configuration SQL Server  
 -  
 -- Dans les versions actuelles de Windows, dans la page **Démarrer** , tapez **Gestionnaire de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server *version* Gestionnaire de configuration**.   
 --   Si vous utilisez une version ancienne de Windows, dans le menu **Démarrer** , pointez successivement sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
 -  
 -## <a name="connect"></a>Connexion à Management Studio  
 -La connexion au [!INCLUDE[ssDE](../includes/ssde-md.md)] à partir d’outils s’exécutant sur le même ordinateur est un jeu d’enfant si vous connaissez le nom de l’instance et si vous vous connectez en tant que membre du groupe Administrateurs local sur l’ordinateur. Vous devez effectuer les procédures suivantes sur le même ordinateur qui héberge [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
 -  
 -> [!NOTE]  
 -> Cette rubrique décrit la connexion à un serveur SQL Server local. Pour vous connecter à Azure SQL Database, consultez [Se connecter à SQL Database avec SQL Server Management Studio et exécuter un exemple de requête T-SQL](https://azure.microsoft.com/documentation/articles/sql-database-connect-query-ssms/).  
 -  
 -##### Pour définir le nom de l'instance du moteur de base de données  
 -  
 -1.  Ouvrez une session Windows en tant que membre du groupe Administrateurs, puis ouvrez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
 -  
 -2.  Dans la boîte de dialogue **Se connecter au serveur** , cliquez sur **Annuler**.  
 -  
 -3.  Si le composant Serveurs inscrits n'apparaît pas, dans le menu **Affichage** , cliquez sur **Serveurs inscrits**.  
 -  
 -4.  Sélectionnez l’option **Moteur de base de données** dans la barre d’outils Serveurs inscrits, développez **Moteur de base de données**, cliquez avec le bouton droit sur **Groupes de serveurs locaux**, pointez sur **Tâches**, puis cliquez sur **Inscrire les serveurs locaux**. Toutes les instances du [!INCLUDE[ssDE](../includes/ssde-md.md)] installées sur l'ordinateur s'affichent, L'instance par défaut n'a pas de nom et prend le nom de l'ordinateur. Une instance nommée s’affiche sous le nom de l’ordinateur suivi d’une barre oblique inversée (\\), puis du nom de l’instance. Pour [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], l’instance est nommée *<nom_ordinateur>*\sqlexpress sauf si vous avez modifié le nom pendant l’installation.  
 -  
 -##### Pour vérifier que le moteur de base de données est en cours d'exécution  
 -  
 -1.  Dans le composant Serveurs inscrits, si le nom de l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contient un point vert avec une flèche blanche en regard du nom, le [!INCLUDE[ssDE](../includes/ssde-md.md)] est exécuté et aucune autre action n'est requise.  
 -  
 -2.  Si le nom de votre instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contient un point rouge avec un carré blanc en regard du nom, le [!INCLUDE[ssDE](../includes/ssde-md.md)] s'arrête. Cliquez avec le bouton droit sur le nom du [!INCLUDE[ssDE](../includes/ssde-md.md)], cliquez sur **Contrôle du service**, puis cliquez sur **Démarrer**. Après un message de confirmation, le [!INCLUDE[ssDE](../includes/ssde-md.md)] doit démarrer et le cercle devenir vert avec une flèche blanche.  
 -  
 -##### Pour se connecter au moteur de base de données  
 -
 -Au moins un compte d’administrateur a été sélectionné pendant l’installation de [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]. Effectuez l’étape suivante quand vous êtes connecté à Windows en tant qu’administrateur.
 -  
 -1.  Dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], dans le menu **Fichier** , cliquez sur **Connecter l'Explorateur d'objets**.  
 -  
 -    La boîte de dialogue **Se connecter au serveur** s'ouvre. La zone **Type de serveur** affiche le dernier type de composant utilisé.  
 -  
 -2.  Sélectionnez **Moteur de base de données**.  
 -
 -    ![object-explorer](../relational-databases/media/object-explorer.png)
 -  
 -3.  Dans la zone **Nom du serveur** , tapez le nom de l'instance du [!INCLUDE[ssDE](../includes/ssde-md.md)]. Pour l'instance par défaut de SQL Server, le nom du serveur est celui de l'ordinateur. Pour une instance nommée de SQL Server, le nom du serveur est *<nom_ordinateur>***\\***<nom_instance>,* par exemple **ACCTG_SRVR\SQLEXPRESS**. La capture d’écran suivante montre la connexion à l’instance par défaut (non nommée) de [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] sur un ordinateur nommé « PracticeComputer ». L’utilisateur connecté à Windows est Mary du domaine Contoso. Quand vous utilisez l’authentification Windows, vous ne pouvez pas modifier le nom d’utilisateur. 
 -
 -    ![connect-to-server](../relational-databases/media/connect-to-server.png)
 -  
 -4.  Cliquez sur **Se connecter**.  
 -
 -> [!NOTE]
 -> Ce didacticiel part du principe que vous ne connaissez pas [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et que vous n’avez pas de problème de connexion particulier. Ainsi, il peut convenir au plus grand nombre et garde toute sa simplicité. Pour connaître les étapes de dépannage détaillées, consultez [Résoudre les problèmes de connexion au moteur de base de données SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md). 
 -  
 -## <a name="additional"></a>Autorisation de connexions supplémentaires  
 -Une fois que vous êtes connecté à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en tant qu'administrateur, l'une de vos premières tâches consiste à autoriser d'autres utilisateurs à se connecter. Pour cela, vous pouvez créer une connexion et l'autoriser à accéder à une base de données en tant qu'utilisateur. Les connexions peuvent désigner des connexions d'authentification Windows qui exploitent les informations d'identification Windows, ou bien des connexions d'authentification SQL Server qui stockent les données d'authentification dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et qui n'ont aucun lien avec vos informations d'identification Windows. Utilisez l'authentification Windows chaque fois que cela est possible.
 -
 -> [!TIP]
 -> La plupart des organisations ont des utilisateurs de domaine et utilisent l’authentification Windows. Vous pouvez essayer vous-même, en créant des utilisateurs locaux supplémentaires sur votre ordinateur. Les utilisateurs locaux étant authentifiés par votre ordinateur, le domaine est le nom de l’ordinateur. Par exemple, si votre ordinateur est nommé `MyComputer` et que vous créez un utilisateur nommé `Test`, la description Windows de l’utilisateur est `Mycomputer\Test`.  
 -  
 -##### Créer une connexion d'authentification Windows  
 -  
 -1.  Au cours de la tâche précédente, vous vous êtes connecté au [!INCLUDE[ssDE](../includes/ssde-md.md)] à l'aide de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Dans l’Explorateur d’objets, développez successivement votre instance de serveur et l’option **Sécurité**, cliquez avec le bouton droit sur **Connexions**, puis cliquez sur **Nouvelle connexion**.  
 -  
 -    La boîte de dialogue **Nouvelle connexion** apparaît.  
 -  
 -2.  Dans la page **Général** , dans la zone **Nom de connexion** , tapez une connexion Windows au format suivant : `<domain>\\<login>`
 -  
 -    ![new-login](../relational-databases/media/new-login.png)
 -  
 -3.  Dans la zone **Base de données par défaut** , sélectionnez [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] (si disponible). Sinon, sélectionnez **master**.  
 -  
 -4.  Dans la page **Rôles du serveur** , si la nouvelle connexion doit être celle d'un administrateur, cliquez sur **sysadmin**; sinon, laissez ce champ vide.  
 -  
 -5.  Dans la page **Mappage de l'utilisateur** , sélectionnez **Mappage** pour la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] (si disponible). Sinon, sélectionnez **master**. Notez que la zone **Utilisateur** est renseignée avec le nom de la connexion. Une fois fermée, la boîte de dialogue crée cet utilisateur dans la base de données.  
 -  
 -6.  Dans la zone **Schéma par défaut** , tapez **dbo** pour mapper la connexion au schéma du propriétaire de base de données.  
 -  
 -7.  Acceptez les paramètres par défaut des zones **Éléments sécurisables** et **État** , puis cliquez sur **OK** pour créer la connexion.  
 -  
 -> [!IMPORTANT]  
 -> Ces informations sont des notions de base destinées à vous aider à démarrer. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] offre un environnement de sécurité de qualité. La sécurité est à l'évidence un aspect primordial des opérations de base de données.  
 -  
 -## Leçon suivante  
 -[Leçon 2 : connexion à partir d’un autre ordinateur](../relational-databases/lesson-2-connecting-from-another-computer.md)    
  
  


