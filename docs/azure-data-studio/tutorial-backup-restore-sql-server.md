---
title: Sauvegarde et restauration des bases de données
description: Suivez ce tutoriel pour découvrir comment sauvegarder et restaurer des bases de données avec Azure Data Studio.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu
ms.custom: seodec18
ms.date: 11/04/2019
ms.openlocfilehash: a7d3ca36634e449dd26dfdb0df75f09608d25f51
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283690"
---
# <a name="tutorial-backup-and-restore-databases-using-azure-data-studio"></a>Tutoriel : Sauvegarder et restaurer des bases de données à l’aide d’Azure Data Studio

Dans ce didacticiel, vous apprendrez à utiliser Azure Data Studio pour :
> [!div class="checklist"]
> * Sauvegarder une base de données 
> * Afficher l’état de la sauvegarde
> * Générer le script utilisé pour effectuer la sauvegarde
> * Restaurer une base de données
> * Afficher l’état de la tâche de restauration

## <a name="prerequisites"></a>Prérequis

Ce didacticiel nécessite la base de données *TutorialDB* de SQL Server. Pour créer la base de données *TutorialDB*, suivez un des démarrages rapides suivants :

* [Se connecter à et interroger SQL Server avec [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)

Ce didacticiel nécessite une connexion à une base de données SQL Server. Azure SQL Database proposant des sauvegardes automatisées, Azure Data Studio n’effectue pas de sauvegarde et de restauration d’Azure SQL Database. Pour plus d’informations, consultez [En savoir plus sur les sauvegardes automatiques de SQL Database](/azure/sql-database/sql-database-automated-backups).

## <a name="back-up-a-database"></a>Sauvegarder une base de données

1. Ouvrez le tableau de bord de la base de données TutorialDB (Ouvrez la barre latérale **SERVEURS** (**CTRL+G**), développez **Bases de données**, sélectionnez avec le bouton droit **TutorialDB** et sélectionnez **Gérer**).

2. Ouvrez la boîte de dialogue **Sauvegarder la base de données** (sélectionnez **Sauvegarder** dans le widget **Tâches**).

   ![Widget Tâches](./media/tutorial-backup-restore-sql-server/tasks.png)

3. Ce tutoriel utilise les options de sauvegarde par défaut, aussi sélectionnez **Sauvegarder**.
   ![boîte de dialogue de sauvegarde](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

Après avoir sélectionné **Sauvegarder**, la boîte de dialogue **Sauvegarder la base de données** disparaît et le processus de sauvegarde commence.

## <a name="view-the-backup-status-and-view-the-backup-script"></a>Afficher l’état de la sauvegarde et afficher le script de sauvegarde

1. Le volet **Historique des tâches** s’affiche ou appuyez sur **Ctrl+T**.

   ![Historique des tâches](./media/tutorial-backup-restore-sql-server/task-history.png)

2. Pour afficher le script de sauvegarde dans l’éditeur, sélectionnez avec le bouton droit **Sauvegarde de base de données réussie**, puis sélectionnez **Script**.

   ![script de sauvegarde](./media/tutorial-backup-restore-sql-server/task-script.png)

## <a name="restore-a-database-from-a-backup-file"></a>Restaurer une base de données à partir d'un fichier de sauvegarde

1. Ouvrez la barre latérale **SERVEURS** (**CTRL+G**), sélectionnez avec le bouton droit votre serveur, puis sélectionnez **Gérer**.

2. Ouvrez la boîte de dialogue **Restaurer la base de données** (sélectionnez **Restaurer** dans le widget **Tâches**).

   ![Restauration de tâches](media/tutorial-backup-restore-sql-server/tasks-restore.png)

3. Sélectionnez **Fichier de sauvegarde** dans le champ **Restaurer à partir de**.

4. Sélectionnez les points de suspension (...) dans le champ **Chemin du fichier de sauvegarde**, puis sélectionnez le fichier de sauvegarde le plus récent pour *TutorialDB*.

5. Saisissez **TutorialDB_Restored** dans le champ **Base de données cible** de la section **Destination** pour restaurer le fichier de sauvegarde dans une nouvelle base de données. Sélectionnez ensuite **Restaurer**.

   ![Restaurer la sauvegarde](./media/tutorial-backup-restore-sql-server/restore.png)

6. Pour afficher l’état de l’opération de restauration, appuyez sur **Ctrl+T** pour ouvrir **Historique des tâches**.

   ![Restauration de la tâche d’historique](./media/tutorial-backup-restore-sql-server/task-history-restore.png)