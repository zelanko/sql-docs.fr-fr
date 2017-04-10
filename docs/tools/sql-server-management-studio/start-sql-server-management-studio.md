---
title: "D&#233;marrer SQL Server Management Studio | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# D&#233;marrer SQL Server Management Studio
Pour commencer ce didacticiel, commençons par regarder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## Ouverture de SQL Server Management Studio  
  
#### Pour ouvrir SQL Server Management Studio  
  
1.  La façon dont vous démarrez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] (SSMS) dépend de votre système d’exploitation.  
* Pour les versions plus récentes de Windows dotées d’une page **Accueil**, dans la page **Accueil**, tapez **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]** et le programme apparaît. Cliquez sur le programme pour ouvrir SSMS. Si vous le souhaitez, vous pouvez cliquer avec le bouton droit sur le programme et l’épingler à la page **Accueil**.   
* Dans le cas d’une version ancienne de Windows, dans le menu **Démarrer**, pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], puis cliquez sur **SQL Server Management Studio**. Ou bien, à partir de la boîte de dialogue **Exécuter**, tapez **SSMS.exe**, puis cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Si SSMS n’apparaît pas, vous ne l’avez peut-être pas installé correctement. Installez-le à partir du [centre de téléchargement](https://msdn.microsoft.com/library/mt238290.aspx). SSMS n’est pas installé automatiquement avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016. Utilisez la dernière version pour accéder à toutes les fonctionnalités.  
  
2.  Dans l’étape suivante, vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide du composant **Explorateur d’objets** de SSMS. Si le volet Explorateur d’objets n’est pas visible, dans le menu **Affichage**, cliquez sur **Explorateur d’objets**. Dans le menu Explorateur d’objets, cliquez sur le bouton **Connecter**, puis sur **Moteur de base de données**. La boîte de dialogue **Se connecter au serveur** doit s’ouvre. (Si vous avez déjà installé SSMS, la boîte de dialogue **Se connecter au serveur** peut s’afficher automatiquement suivant la définition des paramètres utilisateur.)  
  
3.  Dans la boîte de dialogue **Se connecter au serveur**, renseignez la zone **Nom du serveur**. Vous pouvez vous connecter à l’un des trois types de serveurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Chaque type a un format légèrement différent pour la zone **Nom du serveur**. Choisissez l’un des formats suivants :  
--  **Une instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :** quand vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur, vous pouvez spécifier que l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] soit une instance par défaut (sans nom) ou nommée. Si vous vous connectez à une instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], insérez le nom de l’ordinateur. Par exemple, si vous exécutez SSMS sur un ordinateur nommé Accounting et que vous vous connectez à une instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installée sur cet ordinateur, tapez **Accounting** dans la zone **Nom du serveur**.  
--  **Une instance nommée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :** pendant l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez spécifier un nom pour l’instance ; par exemple, sur un ordinateur nommé Accounting, vous pouvez spécifier une instance nommée appelée **Receivables**. Pour vous connecter à une instance nommée, dans la zone **Nom du serveur**, tapez le nom de l’ordinateur, suivi d’une barre oblique inverse et du nom de l’instance, par exemple **Accounting\Receivables**.  
--  **Une base de données SQL Azure : ** le format du nom de serveur pour SQL Database est nom_serveur_SQL_Server.database.windows.net, par exemple **mydb2.database.windows.net**. Si vous ne parvenez pas à déterminer le nom de votre serveur, visitez le portail Azure pour obtenir de l’aide sur la création d’une chaîne de connexion.  
  
4. Dans la zone **Authentification**  
  
## Composants Management Studio  
[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] fournit des informations dans des fenêtres dédiées à des types d’informations précis. Les informations sur les bases de données s'affichent dans l'Explorateur d'objets et dans des fenêtres de documents.  
  
-   L'Explorateur d'objets est une arborescence qui présente tous les objets de base de données sur un serveur. Cela peut inclure les bases de données du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. L'Explorateur d'objets contient des informations sur tous les serveurs auxquels il est connecté. Lorsque vous ouvrez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], le système vous demande de vous connecter à l'Explorateur d'objets avec les derniers paramètres utilisés. Vous pouvez double-cliquer sur n'importe quel serveur dans la fenêtre Serveurs inscrits pour y établir une connexion, mais il n'est pas nécessaire d'inscrire un serveur pour pouvoir vous y connecter.  
  
-   La fenêtre de document occupe la plus grande partie de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Elle contient les fenêtres des éditeurs de requêtes et du navigateur. Par défaut, la page Résumé s’affiche, connectée à l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] sur l’ordinateur actif.  
  
## Affichage de fenêtres supplémentaires  
  
#### Pour afficher la fenêtre Serveurs inscrits  
  
1.  Dans le menu **Affichage**, cliquez sur **Serveurs inscrits**.  
  
    La fenêtre Serveurs inscrits apparaît au-dessus ou à côté de l’Explorateur d’objets. Vous pouvez la faire glisser et l’ancrer à différents emplacements. La fenêtre Serveurs inscrits présente la liste des serveurs que vous administrez fréquemment. Il est possible d'ajouter et de supprimer des serveurs de cette liste. Les seuls serveurs répertoriés sont les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur sur lequel vous exécutez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Si votre serveur n’apparaît pas dans la liste des serveurs inscrits, cliquez avec le bouton droit sur **Moteur de base de données**, cliquez sur **Tâches**, puis cliquez sur **Mettre à jour l’inscription du serveur local**. Pour ajouter des serveurs SQL Server ou une base de données SQL, cliquez avec le bouton droit sur un emplacement dans Serveurs inscrits, puis cliquez sur **Nouvelle inscription de serveur**. Renseignez la zone **Connexion**, comme vous avez complété la boîte de dialogue **Se connecter au serveur**.  
  
## Tâche suivante de la leçon  
[Connexion avec le composant Serveurs inscrits et l'Explorateur d'objets](../../tools/sql-server-management-studio/connect-with-registered-servers-and-object-explorer.md)  
  
