---
title: "Utiliser l’extension mssql de Visual Studio Code | Documents Microsoft"
description: "Cette rubrique montre comment utiliser l'extension mssql pour Visual Studio Code pour développer des bases de données SQL Server. Cette extension vous permet de modifier et exécuter des scripts Transact-SQL dans Visual Studio Code."
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
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-for-sql-server"></a>Utilisez Visual Studio Code pour créer et exécuter des scripts Transact-SQL pour SQL Server

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Cette rubrique montre comment utiliser l'extension **mssql** pour Visual Studio Code (VS Code) pour développer des bases de données SQL Server.

Visual Studio Code est un éditeur de code graphique pour Linux, MacOS et Windows qui supporte les extensions. [L'extension **mssql** pour VS Code] vous permet de vous connecter à SQL Server, d'effectuer une requête avec Transact-SQL (T-SQL) et d'afficher les résultats.

## <a name="install-vs-code"></a>Installer Visual Studio Code
1. Si vous n'avez pas encore installé Visual Studio Code, [téléchargez et installez VS Code] sur votre ordinateur.

2. Démarrez Visual Studio Code.

## <a name="install-the-mssql-extension"></a>Installer l’extension mssql
Les étapes suivantes expliquent comment installer l’extension mssql. 

1. Appuyez sur **CTRL + MAJ + P** (ou **F1**) pour ouvrir la Palette de commandes dans le Visual Studio Code. 

2. Sélectionnez **installer une Extension** et écrivez **mssql**.
   > [!TIP] 
   > Pour macOS, la touche **CMD** est équivalente à **CTRL** sous Linux et Windows.

2. Cliquez sur Installer **mssql**. 
   
   <img src="./media/sql-server-linux-develop-use-vscode/vscode-extension.png" alt="Install the extension" style="width: 600px;"/>

3. L'installation de l'extension **mssql** prend jusqu' à une minute. Attendez l'invite qui vous indique qu'il a été installé avec succès.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-install-success-notification.png" alt="Installation success notification" style="width: 600px;"/>

   > [!NOTE]
   > Pour MacOS, vous devez installer OpenSSL. C'est un pré-requis pour .Net Core utilisé par l'extension mssql. Suivez les étapes préalables à l'installation** décrites dans les [instructions .Net Core]. Vous pouvez également exécuter les commandes suivantes dans votre Terminal MacOS.
   >
   >   ```bash
   >   brew update
   >   brew install openssl
   >   ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
   >   ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
   >   ```
   
   > [!NOTE]
   > Pour les Windows 8.1, Windows Server 2012 ou plus anciennes, vous devez télécharger et installer le [Windows 10 Universal C Runtime]. Téléchargez et ouvrez le fichier zip. Ensuite, exécutez le programme d'installation (fichier. msu) en ciblant la configuration actuelle de votre système d'exploitation.

## <a name="create-or-open-a-sql-file"></a>Créez ou ouvrez un fichier SQL

L'extension **mssql** active les commandes mssql et l'IntelliSense T-SQL dans l'éditeur lorsque le mode langue est réglé sur SQL.

1. Appuyez sur **CTRL + N**. Visual Studio Code ouvre un nouveau fichier de "Texte brut" par défaut. 

2. Appuyez sur **CTRL + K, M** et modifiez le mode de langage à **SQL**. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png" alt="SQL language mode" style="width: 500px;" />

3. Vous pouvez également ouvrir un fichier existant avec l’extension de fichier .sql. Le mode de langage est automatiquement **SQL** pour les fichiers ayant l’extension .sql.  

## <a name="connect-to-sql-server"></a>Se connecter à SQL Server

Les étapes suivantes montrent comment se connecter à SQL Server avec le Visual Studio Code.

1. Dans le Visual Studio Code, appuyez sur **CTRL + MAJ + P** (ou **F1**) pour ouvrir la Palette de commandes.

2. Ecrivez **sql** pour afficher les commandes mssql.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-commands.png" alt="mssql commands" style="width: 500px;" />
   

3. Sélectionnez la commande **MS SQL: Connect**. Vous pouvez simplement taper **sqlcon** et appuyez sur **entrée**.

4. Sélectionnez **créer le profil de connexion**. Cette opération crée un profil de connexion pour votre instance de SQL Server.

5. Suivez les invites pour spécifier les propriétés de connexion du nouveau profil de connexion. Après avoir spécifié chaque valeur, appuyez sur **entrée** pour continuer.

   Le tableau suivant décrit les propriétés de profil de connexion.

   | Paramètre |  Description |
   |-----|-----|
   | **Nom du serveur** | Le nom de l'instance SQL Server. Pour ce tutoriel, utilisez **localhost** pour vous connecter à l'instance SQL Server locale de votre machine. Si vous vous connectez à un serveur SQL distant, entrez le nom de la machine SQL Server cible ou son adresse IP. |
   | **[Facultatif] Nom de la base de données** | La base de données que vous voulez utiliser. Pour les besoins de ce tutoriel, ne spécifiez pas de base de données et appuyez sur **entrée** pour continuer. |
   | **Nom d'utilisateur** | Entrez le nom d'un utilisateur ayant accès à une base de données sur le serveur. Pour ce tutoriel, utilisez le compte **SA** créé par défaut lors de l'installation de SQL Server. |
   | **Mot de passe (connexion SQL)** | Entrez le mot de passe de l'utilisateur spécifié. | 
   | **Enregistrer le mot de passe ?** | Tapez **Oui** pour enregistrer le mot de passe. Sinon, tapez **Non** pour demander le mot de passe chaque fois que le profil de connexion est utilisé. |
   | **[Facultatif] Entrez un nom pour ce profil** | Nom du profil de connexion. Par exemple, vous pouvez nommer le profile **profile local** . 

   > [!Tip] 
   > Vous pouvez créer et modifier des profils de connexion dans le fichier de paramètres utilisateur (settings.json). Ouvrez le fichier de paramètres en sélectionnant **préférences** , puis **paramètres utilisateur** dans le menu Visual Studio Code. Pour plus d’informations, consultez [gérer les profils de connexion].

6. Appuyez sur la touche **ÉCHAP** pour fermer le message d’information qui vous informe que le profil est créé et connecté.

   > [!TIP]
   > Si vous obtenez un échec de connexion, essayez d'abord de diagnostiquer le problème à partir du message d'erreur dans le panneau Output du VS Code (sélectionnez **Sortie** dans le menu **Vue**). Passez ensuite en revue les [recommandations de dépannage des connexions].

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

3. Type **sql** dans la Palette de commandes pour afficher les commandes SQL ou un type **sqluse** pour **MS SQL : Use Database** commande.

4. Cliquez sur **MS SQL:Use Database**, puis sélectionnez la base de données **TutorialDB**. Cela modifie le contexte de la nouvelle base de données créée dans la section précédente.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-use-database.png" alt="use database" style="width: 500px;" />

3. Dans l’éditeur, tapez **sql** pour afficher les extraits de code, puis sélectionnez **sqlCreateTable** et appuyez sur **entrez**.

4. Dans l’extrait de code, tapez **employees** pour le nom de table.

5. Appuyez sur l'**onglet**, puis tapez **dbo** comme nom de schéma.

   > [!NOTE]
   > Après avoir ajouté l’extrait de code, vous devez écrire les noms des tables et des schemas sans faire sortir le focus hors de l’éditeur de Visual Studio Code.

6. Modifier le nom de colonne **Column1** en **nom** et **Column2** en **emplacement**.

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

1. Ajoutez les instructions suivantes pour insérer quatre lignes dans la table **employees**. Puis sélectionnez toutes les lignes.

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
   > Pendant que vous tapez, utilisez l'aide de l'IntelliSense T-SQL.
   >   <img src="./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png" alt="TSQL IntelliSense" style="width: 500px;" />

2. Appuyez sur **CTRL + MAJ + E** pour exécuter les commandes. Les deux ensembles de résultats s'affichent dans la fenêtre  **résultats**. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png" alt="Results" style="width: 300px;" />

## <a name="view-and-save-the-result"></a>Afficher et enregistrer le résultat

1. Dans le menu **vue**, sélectionnez **Toggle Editor Group Layout** pour basculer en présentation vertical ou horizontal.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-split.png" alt="Vertical split" style="width: 500px;" />

2. Cliquez sur l'en-tête du panneau **Résultats** et **Messages** pour réduire et développer le panneau.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png" alt="Toggle Messages" style="width: 500px;" />

   > [!TIP]
   > Vous pouvez personnaliser le comportement par défaut de l’extension mssql. Consultez [personnaliser les options d’extension].

2. Cliquez sur l'icône de la grille de maximisation sur la deuxième grille de résultat pour zoomer.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png" alt="Maximize grid" style="width: 500px;" />

   > [!NOTE]
   > L’icône Agrandir s’affiche lorsque votre script T-SQL possède deux ou plusieurs grilles de résultats.

3. Ouvrez le menu contextuel de la grille à l'aide du bouton droit de la souris sur une grille.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png" alt="Context menu" style="width: 500px;" />

4. Sélectionnez **sélectionner tout**.

5. Ouvrez le menu contextuel de grille et sélectionnez **enregistrer en tant que JSON** pour enregistrer le résultat dans un fichier .json.

6. Spécifiez un nom de fichier JSON. Pour ce didacticiel, tapez **employees.json**.

7. Vérifiez que le fichier JSON est enregistré et ouvert dans Visual Studio Code.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png" alt="Save as Json" style="width: 500px;" />

## <a name="next-steps"></a>Étapes suivantes

Dans un scénario réel, vous pouvez créer un script que vous devrez sauvegarder et exécuter plus tard (soit pour l'administration, soit dans le cadre d'un projet de développement plus vaste). Dans ce cas, vous pouvez sauvegarder le script avec une extension **.sql**.

Si vous utilisez T-SQL, consultez [didacticiel : écriture d’instructions Transact-SQL] et [de référence Transact-SQL (moteur de base de données)].

Pour plus d’informations sur l’utilisation ou qui ont contribué à l’extension mssql, consultez [le wiki de projet d’extension mssql].

Pour plus d’informations sur l’utilisation de Code de Visual Studio, consultez le [documentation de Visual Studio Code](https://code.visualstudio.com/docs).

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
