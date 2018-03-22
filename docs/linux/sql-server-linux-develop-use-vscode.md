---
title: "Utiliser l’extension de mssql de Code Visual Studio pour SQL Server | Documents Microsoft"
description: "Ce didacticiel montre comment utiliser l’extension mssql pour le Code de Visual Studio. Cette extension vous permet de modifier et exécuter des scripts Transact-SQL dans le Code de Visual Studio."
author: erickangMSFT
ms.author: erickang
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.technology: database-engine
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: 
ms.workload: Active
ms.openlocfilehash: 41bfb66db6f16d9e7ca8829568798a2aa57316da
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-for-sql-server"></a>Utilisez le Code de Visual Studio pour créer et exécuter des scripts Transact-SQL pour SQL Server

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Cette rubrique montre comment utiliser l'extension **mssql** pour Visual Studio Code afin de développer des bases de données SQL Server.

Visual Studio Code est un éditeur de code graphique pour Linux, macOS et Windows, qui prend en charge les extensions. [ **L’extension mssql** pour VS Code] vous permet de vous connecter à SQL Server, d'effectuer des requêtes via Transact-SQL (T-SQL) et d'afficher les résultats.

## <a name="install-vs-code"></a>Installer Visual Studio Code
1. Si vous n’avez pas déjà installé Visual Studio Code, [télécharger et installer VS Code] sur votre ordinateur.

2. Démarrez Visual Studio Code.

## <a name="install-the-mssql-extension"></a>Installer l’extension mssql
Les étapes suivantes expliquent comment installer l’extension mssql. 

1. Appuyez sur **CTRL + MAJ + P** (ou **F1**) pour ouvrir la Palette de commandes dans Visual Studio Code. 

2. Sélectionnez **Installer l’extension** et tapez **mssql**. 
   > [!TIP] 
   > Pour macOS, le **CMD** clé est équivalente à **CTRL** clé sous Linux et Windows.

2. Cliquez sur Installer **mssql**. 
   
   <img src="./media/sql-server-linux-develop-use-vscode/vscode-extension.png" alt="Install the extension" style="width: 600px;"/>

3. L'extension  **mssql** prend jusqu'à une minute pour s'installer. Patientez jusqu'à ce que l’invite vous indique qu’il est correctement installé.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-install-success-notification.png" alt="Installation success notification" style="width: 600px;"/>

   > [!NOTE]
   > 	Pour macOS, vous devez installer OpenSSL. Il s’agit d’un prérequis pour .Net Core qui est lui-même utilisé par l’extension mssql. Suivez les **étapes d'installation préalables** dans les instructions de [.Net Core]. Vous pouvez également exécuter les commandes suivantes dans votre terminal macOS. 
   >
   >   ```bash
   >   brew update
   >   brew install openssl
   >   ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
   >   ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
   >   ```
   
   > [!NOTE]
   > Pour Windows 8.1, Windows Server 2012 ou une version inférieure, vous devez télécharger et installer le [Windows 10 universelles C Runtime]. Téléchargez et ouvrez le fichier zip. Puis exécutez le programme d’installation (fichiers .msu) ciblant la configuration actuelle du système d’exploitation.

## <a name="create-or-open-a-sql-file"></a>Créez ou ouvrez un fichier SQL

L'extension **mssql** permet d'activer les commandes mssql et T-SQL IntelliSense dans l’éditeur quand le mode de langage est **SQL**. 

1. Appuyez sur **Ctrl + N**. Visual Studio Code ouvre un nouveau fichier de « Texte brut » par défaut. 

2. Appuyez sur **CTRL + K, M** et modifiez le mode de langage à **SQL**. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png" alt="SQL language mode" style="width: 500px;" />

3. Vous pouvez également ouvrir un fichier existant avec l’extension de fichier .sql. Le mode de langage est automatiquement initialisé à **SQL** pour les fichiers ayant l’extension .sql.  

## <a name="connect-to-sql-server"></a>Se connecter à SQL Server

Les étapes suivantes montrent comment se connecter à SQL Server avec Visual Studio Code.

1. Dans Visual Studio Code, appuyez sur **Ctrl + Maj + P** (ou **F1**) pour ouvrir la palette de commandes. 

2. Tapez **sql** pour afficher les commandes mssql.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-commands.png" alt="mssql commands" style="width: 500px;" />

3. Sélectionnez la commande **MS SQL: Connect**. Vous pouvez simplement taper **sqlcon** et appuyer sur **Entrée**.

4. Sélectionnez **créer le profil de connexion**. Cette opération crée un profil de connexion pour votre instance de SQL Server.

5. Suivez les invites pour spécifier les propriétés de connexion pour le profil de connexion. Après avoir spécifié chacune des valeurs, appuyez sur **Entrée** pour continuer. 

   Le tableau suivant décrit les propriétés de profil de connexion.

   | Paramètre |  Description |
   |-----|-----|
   | **Nom du serveur** | Le nom de l’instance SQL Server. Pour ce didacticiel, utilisez **localhost** pour se connecter à l’instance locale de SQL Server sur votre ordinateur. Si vous vous connectez à un serveur SQL distant, entrez le nom de l’ordinateur SQL Server cible ou son adresse IP. |
   | **[Facultatif] Nom de la base de données** | Il s’agit de la base de données que vous souhaitez utiliser. Pour les besoins de ce didacticiel, ne spécifiez pas de base de données et appuyez sur **Entrée** pour continuer. | 
   | **Nom d'utilisateur** | Entrez le nom d’un utilisateur ayant accès à une base de données sur le serveur. Pour ce didacticiel, utilisez la valeur par défaut **SA** compte créé lors de l’installation de SQL Server. |
   | **Mot de passe (connexion SQL)** | Entrez le mot de passe de l'utilisateur spécifié. | 
   | **Enregistrer le mot de passe ?** | Tapez **Oui** pour enregistrer le mot de passe. Si vous tapez **Non**, vous serez invité à entrer le mot de passe chaque fois que le profil de connexion sera utilisé. | 
   | **[Facultatif] Entrez un nom pour ce profil** | Le nom du profil de connexion. Par exemple, vous pouvez nommer le profil **localhost profil**. 

   > [!Tip] 
   > Vous pouvez créer et modifier des profils de connexion dans le fichier de paramètres utilisateur (settings.json). Ouvrez le fichier de paramètres en sélectionnant **préférences** , puis **paramètres utilisateur** dans le menu Visual Studio Code. Pour plus d’informations, consultez [gérer les profils de connexion].

6. Appuyez sur la **ÉCHAP** touche pour fermer le message d’information qui vous informe que le profil est créé et connecté.

   > [!TIP]
   > Si vous obtenez un échec de connexion, essayez d’abord de diagnostiquer le problème à l'aide du message d’erreur affiché dans le volet **Sortie** de Visual Studio Code (sélectionnez **Sortie** dans le menu **Afficher**). Examinez ensuite les [recommandations en matière de résolution des problèmes de connexion]. 

7. Vérifiez votre connexion dans la barre d’état.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png" alt="Connection status" style="width: 500px;" />

## <a name="create-a-database"></a>création d'une base de données ;

1. Dans l’éditeur, tapez **sql** pour afficher une liste des extraits de code modifiable. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png" alt="SQL snippets" style="width: 500px;" />

2. Sélectionnez **sqlCreateDatabase**.

3. Dans l’extrait de code, tapez **TutorialDB** pour le nom de la base de données.

   ```sql
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
   
4. Appuyez sur **CTRL + MAJ + E** pour exécuter les commandes Transact-SQL. Afficher les résultats dans la fenêtre de requête.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-create-database-messages.png" alt="create database messages" style="width: 500px;" />

   > [!TIP]
   > Vous pouvez personnaliser les combinaisons de touches de raccourci pour les commandes d’extension mssql. Consultez [personnaliser des raccourcis].

## <a name="create-a-table"></a>Créer une table

1. Supprimez le contenu de la fenêtre d’éditeur.

2. Appuyez sur **F1** pour afficher la Palette de commandes.

3. Tapez **sql** dans la palette de commandes pour afficher les commandes SQL ou tapez **sqluse** pour la commande **MS SQL:Use Database**. 

4. Cliquez sur **MS SQL:Use Database**, puis sélectionnez la base de données TutorialDB. Le contexte passe alors à la base de données créée dans la section précédente.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-use-database.png" alt="use database" style="width: 500px;" />

3. Dans l’éditeur, tapez **sql** pour afficher les extraits de code, puis sélectionnez **sqlCreateTable** et appuyez sur **entrez**.

4. Dans l’extrait de code, tapez **employés** pour le nom de table.

5. Appuyez sur **Tab**, puis tapez **dbo** comme nom de schéma. 

   > [!NOTE]
   > Après avoir ajouté l’extrait, vous devez taper les noms de la table et du schéma sans faire passer le focus hors de l’éditeur Visual Studio Code. 

6. Modifier le nom de colonne pour **Column1** à **nom** et **Column2** à **emplacement**.

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

7. Appuyez sur **CTRL + MAJ + E** pour créer la table.

## <a name="insert-and-query"></a>Insertion et requête

1. Ajoutez les instructions suivantes pour insérer quatre lignes dans la table **Employees**. Ensuite, sélectionnez toutes les lignes. 

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
   > En cours de frappe, utilisez l’aide de T-SQL IntelliSense.
   >   <img src="./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png" alt="TSQL IntelliSense" style="width: 500px;" />

2. Appuyez sur **Ctrl + Maj + E** pour exécuter les commandes. Les résultats de l'exécution des deux requêtes s'affichent dans la fenêtre **Résultats**. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png" alt="Results" style="width: 300px;" />

## <a name="view-and-save-the-result"></a>Afficher et enregistrer le résultat

1. Dans le menu **Afficher**, sélectionnez **Activer/désactiver la disposition du groupe d'éditeurs** pour passer à une disposition fractionnée verticalement ou horizontalement.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-split.png" alt="Vertical split" style="width: 500px;" />

2. Cliquez sur le **résultats** et **Messages** en-tête du Panneau de configuration pour réduire et développer le panneau de configuration.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png" alt="Toggle Messages" style="width: 500px;" />

   > [!TIP]
   > Vous pouvez personnaliser le comportement par défaut de l’extension mssql. Consultez [personnaliser les options d’extension].

2. Cliquez sur l’icône de grille agrandir sur la deuxième grille de résultats pour effectuer un zoom.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png" alt="Maximize grid" style="width: 500px;" />

   > [!NOTE]
   > L’icône Agrandir s’affiche lorsque votre script T-SQL possède deux ou plusieurs grilles de résultats.

3. Ouvrez le menu contextuel de grille avec le bouton droit de la souris sur une grille. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png" alt="Context menu" style="width: 500px;" />

4. Sélectionnez **sélectionner tout**.

5. Ouvrez le menu contextuel de grille et sélectionnez **enregistrer en tant que JSON** pour enregistrer le résultat dans un fichier .json.

6. Spécifiez un nom de fichier pour ce fichier JSON. Dans le cadre de ce didacticiel, tapez **employees.json**.

7. Vérifiez que le fichier JSON est enregistré et ouvert dans Visual Studio Code.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png" alt="Save as Json" style="width: 500px;" />

## <a name="next-steps"></a>Étapes suivantes

Dans un scénario réel, vous pouvez créer un script pour l'enregistrer et l'exécuter plus tard (à des fins d’administration ou dans le cadre d’un projet de développement plus important). Dans ce cas, vous pouvez enregistrer le script avec une extension **.sql**. 

Si vous utilisez T-SQL, consultez [didacticiel : écriture d’instructions Transact-SQL] et [de référence Transact-SQL (moteur de base de données)].

Pour plus d’informations sur l’utilisation ou pour contribuer à l’extension mssql, consultez [le Wiki de projet d’extension mssql]. 

Pour plus d’informations sur l’utilisation de Visual Studio Code, consultez la [documentation de Visual Studio Code](https://code.visualstudio.com/docs). 

[**mssql** extension VS Code]:https://aka.ms/mssql-marketplace
[télécharger et installer VS Code]:https://code.visualstudio.com/Download
[.Net des instructions de base]:https://www.microsoft.com/net/core
[gérer les profils de connexion]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[recommandations en matière de résolution des problèmes de connexion]:./sql-server-linux-troubleshooting-guide.md#connection
[personnaliser des raccourcis]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[didacticiel : écriture d’instructions Transact-SQL]:https://msdn.microsoft.com/library/ms365303.aspx
[de référence Transact-SQL (moteur de base de données)]:https://msdn.microsoft.com/library/bb510741.aspx
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 universelles C Runtime]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[personnaliser les options d’extension]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[le wiki de projet d’extension mssql]: https://github.com/Microsoft/vscode-mssql/wiki
