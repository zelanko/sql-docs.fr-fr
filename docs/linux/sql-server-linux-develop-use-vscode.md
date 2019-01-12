---
title: Utiliser l’extension mssql de Visual Studio Code pour SQL Server sur Linux | Microsoft Docs
description: Utiliser l’extension mssql pour Visual Studio Code pour modifier et exécuter des scripts Transact-SQL pour SQL Server sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/18/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: sql-linux
ms.openlocfilehash: 583c7ac13b49370b333e80568c4b52885b58dcf3
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100564"
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-on-linux"></a>Utiliser Visual Studio Code pour créer et exécuter des scripts Transact-SQL sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article montre comment utiliser le *mssql* extension pour Visual Studio Code développer des bases de données SQL Server sous Linux.

## <a name="install-and-start-visual-studio-code"></a>Installez et démarrez Visual Studio Code

Visual Studio Code est un éditeur de code graphique pour Linux, MacOS et Windows qui supporte les extensions. 

1. [Téléchargez et installez Visual Studio Code] sur votre ordinateur.
   
1. Démarrez Visual Studio Code.
   
   >[!NOTE]
   >Si Visual Studio Code ne démarre pas lorsque vous êtes connecté via une session Bureau à distance de xrdp, consultez [VS Code ne fonctionne ne pas sur Ubuntu lorsque connectés à l’aide de XRDP](https://github.com/Microsoft/vscode/issues/3451).

## <a name="install-the-mssql-extension"></a>Installer l’extension mssql

Le [extension mssql pour Visual Studio Code] permet de vous connecter à un serveur SQL, interroger avec Transact-SQL (T-SQL) et afficher les résultats.

1. Dans Visual Studio Code, sélectionnez **vue** > **Palette de commandes**, ou appuyez sur **Ctrl**+**MAJ** + **P**, ou appuyez sur **F1** pour ouvrir le **Palette de commandes**. 
   
1. Dans le **Palette de commandes**, sélectionnez **Extensions : Installer les Extensions** dans la liste déroulante. 
   
1. Dans le **Extensions** volet, tapez *mssql*.
   
1. Sélectionnez le **SQL Server (mssql)** extension, puis sélectionnez **installer**. 
   
   ![Installer l’extension mssql](./media/sql-server-linux-develop-use-vscode/vscode-extension.png)   
   
1. Une fois l’installation terminée, sélectionnez **recharger** pour activer l’extension. 

## <a name="create-or-open-a-sql-file"></a>Créez ou ouvrez un fichier SQL

L’extension mssql permet les commandes mssql et T-SQL IntelliSense dans l’éditeur de code lorsque le mode de langage est défini sur **SQL**.

1. Sélectionnez **fichier** > **nouveau fichier** ou appuyez sur **Ctrl**+**N**. Visual Studio Code ouvre un nouveau fichier de texte brut par défaut. 

1. Sélectionnez **texte brut** dans la barre d’état inférieure, ou appuyez sur **Ctrl**+**K** > **M**, puis sélectionnez **SQL** dans la liste déroulante de langues. 
   
   ![Mode de langage SQL](./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png)   
   
Si vous ouvrez un fichier existant qui a un *.sql* extension de fichier, le mode de langage a automatiquement la valeur SQL.  

## <a name="connect-to-sql-server"></a>Se connecter à SQL Server

Suivez ces étapes pour créer un profil de connexion et de se connecter à un serveur SQL Server.

> [!TIP] 
> Vous pouvez également créer et modifier des profils de connexion dans le fichier de paramètres utilisateur (*settings.json*). Pour ouvrir le fichier de paramètres, sélectionnez **fichier** > **préférences** > **paramètres**. Pour plus d’informations, consultez [gérer les profils de connexion].
   
1. Appuyez sur **Ctrl**+**MAJ**+**P** ou **F1** pour ouvrir la **Palette de commandes**. 
   
1. Type *sql* pour afficher le mssql commandes ou type *sqlcon*, puis sélectionnez **MS SQL : Se connecter** dans la liste déroulante.
   
   ![commandes MSSQL](./media/sql-server-linux-develop-use-vscode/vscode-commands.png)   
   
   >[!NOTE]
   >Un fichier SQL, tel que le fichier SQL vide que vous avez créé, doit avoir le focus dans l’éditeur de code avant de pouvoir exécuter les commandes mssql. 

1. Sélectionnez **créer un profil de connexion** pour créer un nouveau profil de connexion pour votre serveur SQL Server.
   
1. Suivez les invites pour spécifier les propriétés du nouveau profil de connexion. Après avoir spécifié chaque valeur, appuyez sur **entrée** pour continuer. 
   
   1. **Nom du serveur ou la chaîne de connexion ADO**: Spécifiez le nom de l’instance SQL Server. Utilisez *localhost* pour se connecter à une instance de SQL Server sur votre ordinateur local. Pour vous connecter à un serveur SQL distant, entrez le nom de la cible de SQL Server, ou son adresse IP. Si vous avez besoin de spécifier un port, utilisez une virgule pour séparer à partir du nom. Par exemple, pour un serveur local en cours d’exécution sur le port 1401, entrez *localhost, 1401*. 
      
      >[!NOTE]
      >Vous pouvez également entrer la chaîne de connexion ADO pour votre base de données ici, appuyez sur **entrée**, éventuellement le nom du profil de connexion, puis appuyez sur **entrée** à nouveau pour vous connecter et créer le profil. 
      
   1. **Nom de la base de données** (facultatif) : La base de données que vous voulez utiliser. Pour créer une nouvelle base de données, ne spécifiez pas une base de données nom, puis appuyez sur **entrée** pour continuer. 
      
   1. **Type d’authentification**: Appuyez sur **entrée** pour sélectionner **connexion SQL**. 
      
   1. **Nom d’utilisateur**: Entrez le nom d'un utilisateur ayant accès à une base de données sur le serveur.
      
   1. **Mot de passe**: Entrez le mot de passe de l'utilisateur spécifié.
      
   1. **Enregistrer le mot de passe**: Appuyez sur **entrée** pour sélectionner **Oui** et enregistrer le mot de passe. Sélectionnez **non** pour être invité à entrer le mot de passe chaque fois que le profil de connexion est utilisé. 
      
   1. **Nom du profil** (facultatif) : Tapez un nom pour le profil de connexion, tel que *localhost profil*. 
   
   Une fois que vous sélectionnez **entrée**, Visual Studio Code crée le profil de connexion et se connecte à SQL Server. 
   
   > [!TIP]
   > Si la connexion échoue, essayez de diagnostiquer le problème du message d’erreur dans le **sortie** Panneau de configuration dans Visual Studio Code. Pour ouvrir le **sortie** panneau, sélectionnez **vue** > **sortie**. Examinez également le [recommandations de résolution des problèmes de connexion].
   
1. Vérifiez votre connexion dans la barre d’état inférieure.
   
  ![État de la connexion](./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png)   
   
## <a name="create-a-sql-database"></a>Créer une base de données SQL

1. Dans le nouveau fichier SQL que vous avez démarrée précédemment, tapez *sql* pour afficher une liste d’extraits de code modifiable. 

  ![Extraits de code SQL](./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png)   
   
1. Sélectionnez **sqlCreateDatabase**.
   
1. Dans l’extrait de code, remplacez `DatabaseName` avec `TutorialDB`:
   
   ```sql
   -- Create a new database called 'TutorialDB'
   -- Connect to the 'master' database to run this snippet
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO
   ```
   
1. Appuyez sur **Ctrl**+**MAJ**+**E** pour exécuter les commandes Transact-SQL. Afficher les résultats dans la fenêtre de requête.
   
  ![Créer des messages de la base de données](./media/sql-server-linux-develop-use-vscode/vscode-create-database-messages.png)   
   
> [!TIP]
> Vous pouvez personnaliser les touches de raccourci pour les commandes mssql. Consultez [personnaliser les raccourcis].

## <a name="create-a-table"></a>Créer une table

1. Supprimez le contenu de la fenêtre d’éditeur de code.
   
1. Appuyez sur **Ctrl**+**MAJ**+**P** ou **F1** pour ouvrir la **Palette de commandes**. 
   
1. Type *sql* pour afficher le mssql commandes ou type *sqluse*, puis sélectionnez le **base de données MS SQL : use** commande.
   
1. Sélectionnez la nouvelle **TutorialDB** base de données. 
   
   ![Utiliser la base de données](./media/sql-server-linux-develop-use-vscode/vscode-use-database.png)   
   
1. Dans l’éditeur de code, tapez *sql* pour afficher les extraits de code, sélectionnez **sqlCreateTable**, puis appuyez sur **entrée**.
   
1. Dans l’extrait de code, tapez *employés* pour le nom de table et *dbo* pour le nom de schéma.
   
1. Créer les colonnes comme indiqué dans le code suivant :
   
   ```sql
   -- Create a new table called 'Employees' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Employees', 'U') IS NOT NULL
   DROP TABLE dbo.Employees
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Employees
   (
      EmployeesId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location   [NVARCHAR](50)  NOT NULL
   );
   GO
   ```
   
1. Appuyez sur **Ctrl**+**MAJ**+**E** pour créer la table.

## <a name="insert-and-query"></a>Insertion et requête

1. Ajoutez les instructions suivantes pour insérer quatre lignes dans la table **employees**. 

   ```sql
   -- Insert rows into table 'Employees'
   INSERT INTO Employees
      ([EmployeesId],[Name],[Location])
   VALUES
      ( 1, N'Jared', N'Australia'),
      ( 2, N'Nikita', N'India'),
      ( 3, N'Tom', N'Germany'),
      ( 4, N'Jake', N'United States')   
   GO   
   -- Query the total count of employees
   SELECT COUNT(*) as EmployeeCount FROM dbo.Employees;
   -- Query all employee information
   SELECT e.EmployeesId, e.Name, e.Location 
   FROM dbo.Employees as e
   GO
   ```
   
   > [!TIP]
   > En cours de frappe, utilisez T-SQL IntelliSense pour aider à terminer les instructions.
   >![T-SQL IntelliSense](./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png)   
   
1. Appuyez sur **Ctrl**+**MAJ**+**E** pour exécuter les commandes. Les deux ensembles de résultats s'affichent dans la fenêtre **résultats**. 
   
   ![Résultats](./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png)   

## <a name="view-and-save-the-result"></a>Afficher et enregistrer le résultat
   
1. Sélectionnez **vue** > **mise en page de l’éditeur** > **inverser la disposition** pour basculer vers une disposition de fractionnement vertical ou horizontal.
   
1. Sélectionnez le **résultats** et **Messages** en-têtes pour réduire et développer les panneaux de panneau.
   
   ![Activer/désactiver les en-têtes](./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png)   
   
   > [!TIP]
   > Vous pouvez personnaliser le comportement par défaut de l’extension mssql. Consultez [personnaliser les options d’extension].
   
1. Sélectionnez l’icône de grille agrandir sur la deuxième grille de résultats pour effectuer un zoom ces résultats.
   
   ![Optimiser la grille](./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png)   
   
   > [!NOTE]
   > L’icône d’agrandissement affiche quand votre script T-SQL génère deux ou plusieurs grilles de résultats.
   
1. Ouvrez le menu contextuel de grille en cliquant sur la grille. 
   
   ![Menu contextuel](./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png)   
   
1. Sélectionnez **sélectionner tout**.
   
1. Ouvrez le menu contextuel de grille à nouveau et sélectionnez **enregistrer en tant que JSON** pour enregistrer le résultat à un *.json* fichier.
   
1. Spécifiez un nom de fichier pour le fichier JSON. 
   
1. Vérifiez que le fichier JSON enregistre et s’ouvre dans Visual Studio Code.
   
   ![Enregistrer en tant que JSON](./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png)   

Si vous avez besoin enregistrer et exécuter des scripts SQL pour l’administration ou un projet de développement plus grande, plus tard, enregistrer les scripts avec un *.sql* extension.

## <a name="next-steps"></a>Étapes suivantes

Si vous débutez avec T-SQL, consultez [didacticiel : Écrire des instructions Transact-SQL] et [référence Transact-SQL (moteur de base de données)].

Pour plus d’informations sur l’utilisation ou faisant partie de l’extension mssql, consultez le [wiki de projet d’extension mssql].

Pour plus d’informations sur l’utilisation de Visual Studio Code, consultez le [documentation Visual Studio Code](https://code.visualstudio.com/docs).

[extension MSSQL pour Visual Studio Code]:https://aka.ms/mssql-marketplace
[Téléchargez et installez Visual Studio Code]:https://code.visualstudio.com/Download
[.Net Core instructions]:https://www.microsoft.com/net/core
[gérer les profils de connexion]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[recommandations de résolution des problèmes de connexion]:./sql-server-linux-troubleshooting-guide.md#connection
[personnaliser les raccourcis]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[Didacticiel : Écrire des instructions Transact-SQL]:https://docs.microsoft.com/sql/t-sql/tutorial-writing-transact-sql-statements
[Référence Transact-SQL (moteur de base de données)]:https://docs.microsoft.com/sql/t-sql/language-reference
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 Universal C Runtime]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[personnaliser les options d’extension]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[wiki de projet d’extension MSSQL]: https://github.com/Microsoft/vscode-mssql/wiki
