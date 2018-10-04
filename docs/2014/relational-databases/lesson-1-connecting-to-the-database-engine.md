---
title: 'Leçon 1 : Connexion au moteur de base de données | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: e8db82f0-50ed-4531-9209-940006ed34cb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 145adf31e3b59e846eb17369a897e4012f0177ed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132391"
---
# <a name="lesson-1-connecting-to-the-database-engine"></a>Leçon 1 : Connexion au moteur de base de données
  Les outils installés lors de l'installation du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]dépendent de l'édition du produit et de la configuration choisies. Cette leçon passe en revue les outils principaux et décrit comment faire pour se connecter et exécuter une fonction de base (autorisation de plusieurs utilisateurs).  
  
  
  
##  <a name="tools"></a> Outils de mise en route  
 Le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] est fourni avec un éventail d'outils. Cette rubrique décrit les premiers outils dont vous aurez besoin et vous aide à choisir l'outil adapté à votre travail. Vous pouvez accéder à tous les outils à partir du menu **Démarrer** . Certains outils, comme [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], ne sont pas installés par défaut. Vous devez sélectionner les outils en tant qu'éléments inhérents aux composants clients lors de l'installation. Pour obtenir une description complète des outils décrits ci-dessous, recherchez-les dans la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] contient uniquement un sous-ensemble des outils.  
  
### <a name="basic-tools"></a>Outils de base  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] est l’outil principal pour administrer le [!INCLUDE[ssDE](../includes/ssde-md.md)] et l’écriture [!INCLUDE[tsql](../includes/tsql-md.md)] code. Il est hébergé dans le shell [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Il n’est pas inclus dans [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] mais n’est disponible en téléchargement séparé à partir de [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=144346).  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est installé avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les outils clients. Il vous permet d'activer les protocoles serveur, configurer des options de protocole (notamment les ports TCP), configurer le démarrage automatique de services serveur et configurer des ordinateurs clients pour définir leur mode de connexion selon vos préférences. Cet outil configure les éléments de connectivité les plus avancés mais n'active pas les fonctionnalités.  
  
### <a name="sample-database"></a>Base de données exemple  
 Les exemples de bases de données et les exemples ne sont pas fournis avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La plupart des exemples décrits dans la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilisent l'exemple de base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] .  
  
##### <a name="to-start-sql-server-management-studio"></a>Pour démarrer SQL Server Management Studio  
  
-   Sur le **Démarrer** menu, pointez sur **tous les programmes**, pointez sur [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], puis cliquez sur **SQL Server Management Studio**.  
  
##### <a name="to-start-sql-server-configuration-manager"></a>Pour démarrer le Gestionnaire de configuration SQL Server  
  
-   Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
##  <a name="connect"></a> Connexion à Management Studio  
 Il est facile de se connecter à la [!INCLUDE[ssDE](../includes/ssde-md.md)] à partir des outils qui sont exécutent sur le même ordinateur si vous connaissez le nom de l’instance, et si vous vous connectez en tant que membre du groupe Administrateurs sur l’ordinateur. Vous devez effectuer les procédures suivantes sur le même ordinateur qui héberge [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##### <a name="to-determine-the-name-of-the-instance-of-the-database-engine"></a>Pour définir le nom de l'instance du moteur de base de données  
  
1.  Ouvrez une session Windows en tant que membre du groupe Administrateurs, puis ouvrez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
    > [!IMPORTANT]  
    >  Si vous vous connectez à [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] sur [!INCLUDE[wiprlhlong](../includes/wiprlhlong-md.md)] ou [!INCLUDE[nextref_longhorn](../includes/nextref-longhorn-md.md)] (ou plus récente), vous devrez peut-être avec le bouton droit [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] puis cliquez sur **exécuter en tant qu’administrateur** afin de vous connecter à l’aide de votre administrateur informations d’identification. À partir de [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], le programme d'installation ajoute les connexions sélectionnées à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], aussi vos informations d'identification d'administrateur ne sont-elles pas nécessaires.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** , cliquez sur **Annuler**.  
  
3.  Si le composant Serveurs inscrits n'apparaît pas, dans le menu **Affichage** , cliquez sur **Serveurs inscrits**.  
  
4.  Sélectionnez l’option **Moteur de base de données** dans la barre d’outils Serveurs inscrits, développez **Moteur de base de données**, cliquez avec le bouton droit sur **Groupes de serveurs locaux**, pointez sur **Tâches**, puis cliquez sur **Inscrire les serveurs locaux**. Toutes les instances du [!INCLUDE[ssDE](../includes/ssde-md.md)] installées sur l'ordinateur s'affichent, L'instance par défaut n'a pas de nom et prend le nom de l'ordinateur. Une instance nommée s’affiche sous le nom de l’ordinateur suivi d’une barre oblique inversée (\\), puis du nom de l’instance. Pour [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], l’instance est nommée *<nom_ordinateur>* \sqlexpress sauf si vous avez modifié le nom pendant l’installation.  
  
##### <a name="to-verify-that-the-database-engine-is-running"></a>Pour vérifier que le moteur de base de données est en cours d'exécution  
  
1.  Dans le composant Serveurs inscrits, si le nom de l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contient un point vert avec une flèche blanche en regard du nom, le [!INCLUDE[ssDE](../includes/ssde-md.md)] est exécuté et aucune autre action n'est requise.  
  
2.  Si le nom de votre instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contient un point rouge avec un carré blanc en regard du nom, le [!INCLUDE[ssDE](../includes/ssde-md.md)] s'arrête. Cliquez avec le bouton droit sur le nom du [!INCLUDE[ssDE](../includes/ssde-md.md)], cliquez sur **Contrôle du service**, puis cliquez sur **Démarrer**. Après un message de confirmation, le [!INCLUDE[ssDE](../includes/ssde-md.md)] doit démarrer et le cercle devenir vert avec une flèche blanche.  
  
##### <a name="to-connect-to-the-database-engine"></a>Pour se connecter au moteur de base de données  
  
1.  Dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], dans le menu **Fichier** , cliquez sur **Connecter l'Explorateur d'objets**.  
  
     La boîte de dialogue **Se connecter au serveur** s'ouvre. La zone **Type de serveur** affiche le dernier type de composant utilisé.  
  
2.  Sélectionnez **Moteur de base de données**.  
  
3.  Dans la zone **Nom du serveur** , tapez le nom de l'instance du [!INCLUDE[ssDE](../includes/ssde-md.md)]. Pour l'instance par défaut de SQL Server, le nom du serveur est celui de l'ordinateur. Pour une instance nommée de SQL Server, le nom du serveur est *<nom_ordinateur>***\\***<nom_instance>,* par exemple **ACCTG_SRVR\SQLEXPRESS**.  
  
4.  Cliquez sur **Se connecter**.  
  
##  <a name="additional"></a> Autorisation de connexions supplémentaires  
 Une fois que vous êtes connecté à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en tant qu'administrateur, l'une de vos premières tâches consiste à autoriser d'autres utilisateurs à se connecter. Pour cela, vous pouvez créer une connexion et l'autoriser à accéder à une base de données en tant qu'utilisateur. Les connexions peuvent désigner des connexions d'authentification Windows qui exploitent les informations d'identification Windows, ou bien des connexions d'authentification SQL Server qui stockent les données d'authentification dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et qui n'ont aucun lien avec vos informations d'identification Windows. Utilisez l'authentification Windows chaque fois que cela est possible.  
  
##### <a name="create-a-windows-authentication-login"></a>Créer une connexion d'authentification Windows  
  
1.  Au cours de la tâche précédente, vous vous êtes connecté au [!INCLUDE[ssDE](../includes/ssde-md.md)] à l'aide de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Dans l’Explorateur d’objets, développez successivement votre instance de serveur et l’option **Sécurité**, cliquez avec le bouton droit sur **Connexions**, puis cliquez sur **Nouvelle connexion**.  
  
     La boîte de dialogue **Nouvelle connexion** apparaît.  
  
2.  Sur le **général** page, dans le **nom de connexion** , tapez un compte de connexion Windows au format  *\<domaine >\\< connexion\>*.  
  
3.  Dans la zone **Base de données par défaut** , sélectionnez [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] (si disponible). Sinon, sélectionnez **master**.  
  
4.  Dans la page **Rôles du serveur** , si la nouvelle connexion doit être celle d'un administrateur, cliquez sur **sysadmin**; sinon, laissez ce champ vide.  
  
5.  Dans la page **Mappage de l'utilisateur** , sélectionnez **Mappage** pour la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] (si disponible). Sinon, sélectionnez **master**. Notez que la zone **Utilisateur** est renseignée avec le nom de la connexion. Une fois fermée, la boîte de dialogue crée cet utilisateur dans la base de données.  
  
6.  Dans la zone **Schéma par défaut** , tapez **dbo** pour mapper la connexion au schéma du propriétaire de base de données.  
  
7.  Acceptez les paramètres par défaut des zones **Éléments sécurisables** et **État** , puis cliquez sur **OK** pour créer la connexion.  
  
> [!IMPORTANT]  
>  Ces informations sont des notions de base destinées à vous aider au démarrage. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] offre un environnement de sécurité de qualité. La sécurité est à l'évidence un aspect primordial des opérations de base de données.  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Connexion depuis un autre ordinateur](lesson-2-connecting-from-another-computer.md)  
  
  
