---
title: Développer et déployer SQL Server databases pour Linux | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1e924704-e07c-4a8b-b243-8c1dd8cff0d3
ms.custom: sql-linux
ms.openlocfilehash: 874fd8948d4098e9003fb2c54e1feb8b5cbbe4e3
ms.sourcegitcommit: 134a91ed1a59b9d57cb1e98eb1eae24f118da51e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2019
ms.locfileid: "52750361"
---
# <a name="use-visual-studio-to-create-databases-for-sql-server-on-linux"></a>Utiliser Visual Studio pour créer des bases de données pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server Data Tools (SSDT) transforme Visual Studio en un puissant environnement de développement et de gestion du cycle de vie des bases de données (DLM) pour SQL Server sous Linux. Vous pouvez développer, construire, tester et publier votre base de données à partir d'un projet de contrôle de code source, tout comme vous développez votre code d'application.

## <a name="install-visual-studio-and-sql-server-data-tools"></a>Installer Visual Studio et SQL Server Data Tools

1. Si vous n'avez pas encore installé Visual Studio sur votre ordinateur Windows, [téléchargez et installez Visual Studio]. Si vous n'avez pas de licence Visual Studio, Visual Studio Community Edition est un IDE gratuit et complet pour les étudiants, les développeurs open-source et les développeurs individuels.

2. Pendant l’installation de Visual Studio, sélectionnez **personnalisé** pour **choisir le type d’installation**. Cliquez sur **Suivant**.

3. Sélectionnez **Microsoft SQL Server Data Tools**, **Git pour Windows** et **GitHub Extension pour Visual Studio** dans la liste de sélection des fonctionnalités.

    <img src="./media/sql-server-linux-develop-use-ssdt/ssdt-setup.png" alt="ssdt setup" style="width: 400px;"/>

4. Cela peut prendre quelques minutes. Cela peut prendre quelques minutes.

## <a name="upgrade-sql-server-data-tools-to-ssdt-170-rc-release"></a>Mise à niveau des outils SQL Server Data Tools vers la version SSDT 17.0 RC

SQL Server sur Linux est pris en charge par SSDT version 17.0 RC ou version ultérieure.

* [Téléchargez et installez SSDT 17.0 RC2](https://go.microsoft.com/fwlink/?linkid=837939).

## <a name="create-a-new-database-project-in-source-control"></a>Créer un nouveau projet de base de données dans le contrôle de code source

1. Lancez Visual Studio.

2. Sélectionnez **Team Explorer** dans le menu **Affichage**. 

3. Cliquez sur **Nouveau** dans la section **Dépôt Git local** sur la page **Connexion**.

    <img src="./media/sql-server-linux-develop-use-ssdt/git-repository.png" alt="local repository" style="width: 300px;"/>

3. Cliquez sur **Créer**. Une fois que le dépôt Git local est créé, double-cliquez sur **SSDTRepo**.

4. Cliquez sur **nouveau** dans la section des **Solutions**. Sélectionnez **SQL Server** sous la rubrique **autres langages** dans la boîte de dialogue **nouveau projet**.

    <img src="./media/sql-server-linux-develop-use-ssdt/new-project.png" alt="local repository" style="width: 480px;"/>

5. Entrez **TutorialDB** pour le nom et cliquez sur **OK** pour créer un nouveau projet de base de données.

## <a name="create-a-new-table-in-the-database-project"></a>Créez une nouvelle table dans le projet de base de données

1. Sélectionnez **l’Explorateur de solutions** sur le menu **Affichage**.

2. Ouvrez le menu du projet de la base de données en cliquant avec le bouton droit de la souris sur **TutorialDB** dans l'explorateur de solutions.

3. Sélectionnez **Table** sous **ajouter**.

    <img src="./media/sql-server-linux-develop-use-ssdt/create-table.png" alt="create table" style="width: 480px;"/>

4. En utilisant le concepteur de table, ajoutez deux colonnes, Name `nvarchar(50)` et Location `nvarchar(50)`, comme illustré dans l'image. SSDT génère le script `CREATE TABLE` lorsque vous ajoutez les colonnes dans le designer.

    <img src="./media/sql-server-linux-develop-use-ssdt/add-columns.png" alt="add columns" style="width: 480px;"/>

5. Enregistrez le fichier **Table1.sql**.

## <a name="build-and-validate-the-database"></a>Générer et valider la base de données

1. Ouvrez le menu du projet de la base de données sur **TutorialDB** et sélectionnez **Build**. SSDT compile les fichiers de code source. sql dans votre projet et crée un fichier de type Data-tier Application Package (dacpac). Cela peut être utilisé pour publier une base de données à votre instance de SQL Server sur Linux. 

    <img src="./media/sql-server-linux-develop-use-ssdt/build.png" alt="add columns" style="width: 400px;"/>

2. Vérifiez le message de réussite de la génération dans la fenêtre **Sortie** de Visual Studio. 

## <a name="publish-the-database-to-sql-server-instance-on-linux"></a>Publier la base de données à l’instance de SQL Server sur Linux

1. Ouvrez le menu de projet de base de données sur **TutorialDB** et sélectionnez **publier**.

2. Cliquez sur **modifier** pour sélectionner votre instance de SQL Server sur Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-dialog.png" alt="publish dialog" style="width: 480px;"/>

3. Dans la boîte de dialogue de connexion, tapez le nom d’hôte ou adresse IP de votre instance de SQL Server sur Linux, le nom d’utilisateur et le mot de passe.

    <img src="./media/sql-server-linux-develop-use-ssdt/connection-dialog.png" alt="connection dialog" style="width: 400px;"/>

4. Cliquez sur le bouton **publier**, dans la boîte de dialogue Publier.

5. Vérifiez l’état de la publication dans la fenêtre **opérations des outils de données**.

6. Cliquez sur **afficher les résultats** ou **afficher le Script** pour afficher les détails de la base de données à publier les résultats sur votre serveur SQL Server sur Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-result.png" alt="publish result" style="width: 480px;"/>

Vous avez créé une base de données sur l'instance SQL Server sur Linux et vous avez appris les bases du développement d'une base de données avec un projet de base de données avec contrôle du code source.

## <a name="next-steps"></a>Étapes suivantes

Si vous débutez avec T-SQL, consultez [didacticiel : Écriture d’instructions Transact-SQL] et [référence Transact-SQL (moteur de base de données)].

Pour plus d’informations sur le développement d’une base de données avec les outils de données SQL, consultez [Documents MSDN SSDT]

[Téléchargez et installez Visual Studio]:https://www.visualstudio.com/downloads/
[Download and Install SSDT]:https://aka.ms/ssdt-download
[Documents MSDN SSDT]: https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx
[Didacticiel : Écriture d’instructions Transact-SQL]:https://msdn.microsoft.com/library/ms365303.aspx
[Référence Transact-SQL (moteur de base de données)]:https://msdn.microsoft.com/library/bb510741.aspx
