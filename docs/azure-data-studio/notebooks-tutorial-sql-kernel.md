---
title: Notebooks avec noyau SQL dans Azure Data Studio
description: Ce tutoriel vous montre comment créer et exécuter un notebook SQL Server.
author: markingmyname
ms.author: maghan
ms.reviewer: mikeray, alayu
ms.topic: conceptual
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 03/30/2020
ms.openlocfilehash: 70136c114fe1d4e9421400eff5f171a70289098c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82178690"
---
# <a name="create-and-run-a-sql-server-notebook"></a>Créer et exécuter un notebook SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce tutoriel montre comment créer et exécuter un notebook dans Azure Data Studio à l’aide de SQL Server.

## <a name="prerequisites"></a>Prérequis

- [Azure Data Studio installé](download-azure-data-studio.md)
- SQL Server installé
  - [Windows](../database-engine/install-windows/install-sql-server.md)
  - [Linux](../linux/sql-server-linux-setup.md)

## <a name="new-notebook"></a>Nouveau notebook

Les étapes suivantes montrent comment créer un fichier de notebook dans Azure Data Studio :

1. Dans Azure Data Studio, connectez-vous à votre serveur SQL Server.

2. Effectuez la sélection sous **Connexions** dans la fenêtre **Serveurs**. Sélectionnez ensuite **Nouveau notebook**.

   ![Ouvrir un notebook](media/notebook-tutorial/azure-data-studio-open-notebook.png)

3. Attendez que **Noyau** et le contexte cible (**Attacher à**) soient remplis. Vérifiez que **Noyau** indique **SQL**, puis définissez **Attacher à** avec votre serveur SQL Server (dans ce cas, son *localhost*).

   ![Définir Noyau et Attacher à](media/notebook-tutorial/set-kernel-and-attach-to.png)

## <a name="run-a-notebook-cell"></a>Exécuter une cellule de notebook

Vous pouvez exécuter chaque cellule de notebook en appuyant sur le bouton de lecture situé à gauche de la cellule. Les résultats sont affichés dans le notebook après la fin de l’exécution de la cellule.

### <a name="code"></a>Code

Ajoutez une nouvelle cellule de code en sélectionnant la commande **+ Code** dans la barre d’outils.

![Barre d’outils du notebook](media/notebooks-guidance/notebook-toolbar.png)

Cet exemple crée une base de données.

```sql
USE master
GO

   -- Drop the database if it already exists
IF  EXISTS (
        SELECT name
        FROM sys.databases
        WHERE name = N'TestNotebookDB'
   )
DROP DATABASE TestNotebookDB
GO

-- Create the database
CREATE DATABASE TestNotebookDB
GO
```

   ![Exécuter la cellule de notebook](media/notebook-tutorial/run-notebook-cell.png)

Si vous exécutez un script qui retourne un résultat, vous pouvez enregistrer ce résultat dans différents formats.

- Enregistrer au format CSV
- Enregistrer au format Excel
- Enregistrer au format JSON
- Enregistrer au format XML

Dans ce cas, nous retournons le résultat de [PI](../t-sql/functions/pi-transact-sql.md).

```sql
SELECT PI() AS PI;
GO
```

![Exécuter la cellule de notebook](media/notebook-tutorial/run-notebook-cell-2.png)

### <a name="text"></a>Texte

Ajoutez une nouvelle cellule de texte en sélectionnant la commande **+ Texte** dans la barre d’outils.

![Barre d’outils du notebook](media/notebooks-guidance/notebook-toolbar.png)

La cellule passe en mode édition. Entrez maintenant du code Markdown : vous voyez l’aperçu en même temps.

![Cellule Markdown](media/notebooks-guidance/notebook-markdown-cell.png)

Si vous sélectionnez un élément en dehors de la cellule de texte, le texte Markdown apparaît.

![Texte Markdown](media/notebooks-guidance/notebook-markdown-preview.png)

## <a name="next-steps"></a>Étapes suivantes

Découvrez-en plus sur les notebooks :

- [Guide pratique pour utiliser des notebooks avec SQL Server](notebooks-guidance.md)

- [Comment gérer des notebooks dans Azure Data Studio](notebooks-manage-sql-server.md)

- [Exécuter un exemple de notebook avec Spark](../big-data-cluster/notebooks-tutorial-spark.md)