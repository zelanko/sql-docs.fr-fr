---
title: "Développer et déployer SQL Server databases pour Linux | Documents Microsoft"
description: 
author: erickangMSFT
ms.author: erickang
manager: jroth
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1e924704-e07c-4a8b-b243-8c1dd8cff0d3
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 05cc425e6411734b0cc300a9e3587fa2196893ab
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="use-visual-studio-to-create-databases-for-sql-server-on-linux"></a>Utilisez Visual Studio pour créer des bases de données pour SQL Server sur Linux 

SQL Server Data Tools (SSDT), Visual Studio se transforme en un environnement de gestion (DLM) du cycle de vie de développement et de base de données puissantes, pour SQL Server sur Linux. Vous pouvez développer, créer, tester et publier votre base de données à partir d’un projet de contrôle de code source, tout comme vous développez votre code d’application.

## <a name="install-visual-studio-and-sql-server-data-tools"></a>Installer Visual Studio et SQL Server Data Tools

1. Si vous n’avez pas déjà installé Visual Studio sur votre ordinateur Windows, [télécharger et installer Visual Studio]. Si vous n’avez pas une licence de Visual Studio, Visual Studio Community edition est un IDE gratuit et complet pour les étudiants, les développeurs open source et individuels.

2. Pendant l’installation de Visual Studio, sélectionnez **personnalisé** pour le **choisir le type d’installation** option. Cliquez sur **Suivant**.

3. Sélectionnez **Microsoft SQL Server Data Tools**, **Git pour Windows**, et **GitHub Extension pour Visual Studio** dans la liste de sélection de fonctionnalité.

    <img src="./media/sql-server-linux-develop-use-ssdt/ssdt-setup.png" alt="ssdt setup" style="width: 400px;"/>

4. Continuer et terminer l’installation de Visual Studio. Il peut prendre quelques minutes.

## <a name="upgrade-sql-server-data-tools-to-ssdt-170-rc-release"></a>Mise à niveau de SQL Server Data Tools vers la version RC de 17,0 SSDT

SQL Server 2017 RC2 sur Linux est prise en charge par SSDT version 17,0 RC ou version ultérieure.

1. [Téléchargez et installez SSDT 17,0 RC2].

## <a name="create-a-new-database-project-in-source-control"></a>Créer un nouveau projet de base de données dans le contrôle de code source

1. Lancez Visual Studio.

2. Sélectionnez **Team Explorer** sur la **vue** menu. 

3. Cliquez sur **nouveau** dans **référentiel Git Local** section sur le **Connect** page.

    <img src="./media/sql-server-linux-develop-use-ssdt/git-repository.png" alt="local repository" style="width: 300px;"/>

3. Cliquez sur **Créer**. Une fois le référentiel Git local est créé, double-cliquez sur **SSDTRepo**.

4. Cliquez sur **nouveau** dans les **Solutions** section. Sélectionnez **SQL Server** sous **autres langages** nœud dans le **nouveau projet** boîte de dialogue.

    <img src="./media/sql-server-linux-develop-use-ssdt/new-project.png" alt="local repository" style="width: 480px;"/>

5. Tapez dans **TutorialDB** pour le nom et cliquez sur **OK** pour créer un nouveau projet de base de données.

## <a name="create-a-new-table-in-the-database-project"></a>Créer une nouvelle table dans le projet de base de données

1. Sélectionnez **l’Explorateur de solutions** sur la **vue** menu.

2. Ouvrez le menu de projet de base de données en cliquant sur **TutorialDB** dans l’Explorateur de solutions.

3. Sélectionnez **Table** sous **ajouter**.

    <img src="./media/sql-server-linux-develop-use-ssdt/create-table.png" alt="create table" style="width: 480px;"/>

4. À l’aide du Concepteur de tables, ajouter deux colonnes, nom `nvarchar(50)` et l’emplacement `nvarchar(50)`, comme illustré dans l’image. SSDT génère le `CREATE TABLE` de script que vous ajoutez les colonnes dans le concepteur.

    <img src="./media/sql-server-linux-develop-use-ssdt/add-columns.png" alt="add columns" style="width: 480px;"/>

5. Enregistrer le **Table1.sql** fichier.

## <a name="build-and-validate-the-database"></a>Générer et valider la base de données

1. Ouvrez le menu de projet de base de données sur **TutorialDB** et sélectionnez **Build**. SSDT compile les fichiers de code source .sql dans votre projet et crée un fichier de package (dacpac) d’Application de couche données. Cela permet de publier une base de données à votre instance de SQL Server 2017 sur Linux. 

    <img src="./media/sql-server-linux-develop-use-ssdt/build.png" alt="add columns" style="width: 400px;"/>

2. Archiver le message de réussite du build **sortie** fenêtre dans Visual Studio. 

## <a name="publish-the-database-to-sql-server-2017-instance-on-linux"></a>Publier la base de données à l’instance de SQL Server 2017 sur Linux

1. Ouvrez le menu de projet de base de données sur **TutorialDB** et sélectionnez **publier**.

2. Cliquez sur **modifier** pour sélectionner votre instance de SQL Server sur Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-dialog.png" alt="publish dialog" style="width: 480px;"/>

3. Dans la boîte de dialogue de connexion, tapez le nom d’hôte ou adresse IP de votre instance de SQL Server sur Linux, nom d’utilisateur et mot de passe.

    <img src="./media/sql-server-linux-develop-use-ssdt/connection-dialog.png" alt="connection dialog" style="width: 400px;"/>

4. Cliquez sur le **publier** bouton dans la boîte de dialogue Publier.

5. Vérifier l’état de la publication dans le **opérations des outils de données** fenêtre.

6. Cliquez sur **vue Reulst** ou **afficher le Script** pour afficher les détails de la Microsoft Azure à publier les résultats sur votre serveur SQL Server sur Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-result.png" alt="publish result" style="width: 480px;"/>

Vous avez créé une base de données sur l’instance SQL Server sur Linux et appris les notions de base du développement d’une base de données avec un projet de base de données de contrôle de code source.

## <a name="next-steps"></a>Étapes suivantes

Si vous utilisez T-SQL, consultez [didacticiel : écriture d’instructions Transact-SQL] et [de référence Transact-SQL (moteur de base de données)].

Pour plus d’informations sur le développement d’une base de données avec les outils de données SQL, consultez [documents de MSDN SSDT]

[télécharger et installer Visual Studio]:https://www.visualstudio.com/downloads/
[Téléchargez et installez SSDT 17,0 RC2]:https://aka.ms/ssdt-download
[documents de MSDN SSDT]: https://msdn.microsoft.com/en-us/library/hh272686(v=vs.103).aspx
[didacticiel : écriture d’instructions Transact-SQL]:https://msdn.microsoft.com/library/ms365303.aspx
[de référence Transact-SQL (moteur de base de données)]:https://msdn.microsoft.com/library/bb510741.aspx




