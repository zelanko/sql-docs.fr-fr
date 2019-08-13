---
title: Sauvegarder et restaurer une base de données
titleSuffix: Azure Data Studio
description: Découvrez comment sauvegarder et restaurer une base de données à l’aide d’Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 77679106577cd8f8374f932d8ddd22644beb63d8
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959103"
---
# <a name="backup-and-restore-databases-using-includename-sosincludesname-sos-shortmd"></a>Sauvegarder et restaurer des bases de données avec [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Dans ce didacticiel, vous apprendrez à utiliser [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour :
> [!div class="checklist"]
> * Sauvegarder une base de données 
> * Afficher l’état de la sauvegarde
> * Générer le script utilisé pour effectuer la sauvegarde
> * Restaurer une base de données
> * Afficher l’état de la tâche de restauration

## <a name="prerequisites"></a>Conditions préalables requises

Ce didacticiel nécessite la base de données *TutorialDB* de SQL Server. Pour créer la base de données *TutorialDB*, suivez un des démarrages rapides suivants :

- [Se connecter à et interroger SQL Server avec [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)

Ce didacticiel nécessite une connexion à une base de données SQL Server. Azure SQL Database a des sauvegardes automatisées, Azure Data Studio n’effectue pas de sauvegarde et de restauration d’Azure SQL Database. Pour plus d’informations, consultez [En savoir plus sur les sauvegardes automatiques de SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups).

## <a name="backup-a-database"></a>Sauvegarder une base de données

1. Ouvrez le tableau de bord de la base de données TutorialDB (Ouvrez la barre latérale **SERVEURS** (**CTRL+G**), développez **Bases de données**, cliquez avec le bouton droit sur **TutorialDB** et sélectionnez **Gérer**).

2. Ouvrez la boîte de dialogue **Sauvegarder la base de données** (cliquez sur **Sauvegarder** dans le widget **Tâches**).

   ![Widget Tâches](./media/tutorial-backup-restore-sql-server/tasks.png)

3. Ce didacticiel utilise les options de sauvegarde par défaut, aussi cliquez sur **Sauvegarder**.
   ![boîte de dialogue de sauvegarde](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

Après avoir cliqué sur **Sauvegarder**, la boîte de dialogue **Sauvegarder la base de données** disparaît et le processus de sauvegarde commence.

## <a name="view-the-backup-status-and-view-the-backup-script"></a>Afficher l’état de la sauvegarde et afficher le script de sauvegarde

1. Ouvrez la barre latérale **Historique des tâches** en cliquant sur l’icône d'horloge dans la *barre d’action* ou appuyez sur **CTRL+T**.

   ![Historique des tâches](./media/tutorial-backup-restore-sql-server/task-history.png)

2. Pour afficher le script de sauvegarde dans l’éditeur, cliquez avec le bouton droit sur **Sauvegarde de base de données réussie**, puis sélectionnez **Script**.

   ![script de sauvegarde](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>Restaurer une base de données à partir d'un fichier de sauvegarde


1. Ouvrez la barre latérale **SERVEURS** (**CTRL+G**), cliquez avec le bouton droit sur votre serveur, puis sélectionnez **Gérer**. 

2. Ouvrez la boîte de dialogue **Restaurer la base de données** (cliquez sur **Restaurer** dans le widget **Tâches**).

2. Sélectionnez **Fichier de sauvegarde** dans le champ **Restaurer à partir de**. 

3. Cliquez sur les points de suspension (...) dans le champ **Chemin du fichier de sauvegarde**, puis sélectionnez le fichier de sauvegarde le plus récent pour *TutorialDB*.

3. Saisissez **TutorialDB_Restored** dans le champ **Base de données cible** de la section **Destination** pour restaurer le fichier de sauvegarde dans une nouvelle base de données.

   ![restauration](./media/tutorial-backup-restore-sql-server/restore.png)

4. Cliquez sur **Restaurer**

5. Pour afficher l’état de l’opération de restauration, appuyez sur **CTRL+T** pour ouvrir la barre latérale **Historique des tâches**.

   ![restauration](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> * Sauvegarder une base de données 
> * Afficher l’état de la sauvegarde
> * Générer le script utilisé pour effectuer la sauvegarde
> * Restaurer une base de données
> * Afficher l’état de la tâche de restauration

