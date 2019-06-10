---
title: Sauvegarder et restaurer une base de données
titleSuffix: Azure Data Studio
description: Découvrez comment sauvegarder et restaurer une base de données à l’aide d’Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 93f38f8e703aabc765d3badc91393eb130081c99
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797973"
---
# <a name="backup-and-restore-databases-using-includename-sosincludesname-sos-shortmd"></a>Sauvegarde et restauration de bases de données à l’aide de [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Dans ce didacticiel, vous allez apprendre à utiliser [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour :
> [!div class="checklist"]
> * Sauvegarde une base de données 
> * Afficher l’état de sauvegarde
> * Générer le script utilisé pour effectuer la sauvegarde
> * Restaurer une base de données
> * Afficher l’état de la tâche de restauration

## <a name="prerequisites"></a>Prerequisites

Ce didacticiel requiert le serveur SQL Server *TutorialDB*. Pour créer le *TutorialDB* de base de données, effectuez l’une des Démarrages rapides suivants :

- [Se connecter et interroger à l’aide de SQL Server [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)

Ce didacticiel requiert la connexion à une base de données SQL Server. Base de données SQL Azure a automatisé des sauvegardes, Azure Data Studio ne pas effectuer de sauvegarde de base de données SQL Azure et de restauration. Pour plus d’informations, consultez [en savoir plus sur les sauvegardes automatiques de base de données SQL](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups).

## <a name="backup-a-database"></a>Sauvegarde une base de données

1. Ouvrez le tableau de bord de base de données TutorialDB (ouvrir le **serveurs** encadré (**CTRL + G**), développez **bases de données**, avec le bouton droit **TutorialDB**, Sélectionnez **gérer**).

2. Ouvrez le **Backup database** boîte de dialogue (cliquez sur **sauvegarde** sur le **tâches** widget).

   ![Widget de tâches](./media/tutorial-backup-restore-sql-server/tasks.png)

3. Ce didacticiel utilise les options de sauvegarde par défaut, cliquez sur **sauvegarde**.
   ![boîte de dialogue de sauvegarde](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

Après avoir cliqué sur **sauvegarde**, le **Backup database** disparaît de la boîte de dialogue et commence le processus de sauvegarde.

## <a name="view-the-backup-status-and-view-the-backup-script"></a>Afficher l’état de sauvegarde et le script de sauvegarde

1. Ouvrez le **l’historique des tâches** encadré en cliquant sur l’icône d’horloge sur le *barre d’Action* ou appuyez sur **CTRL + T**.

   ![Historique des tâches](./media/tutorial-backup-restore-sql-server/task-history.png)

2. Pour afficher le script de sauvegarde dans l’éditeur, avec le bouton droit **sauvegarde de base de données a réussi** et sélectionnez **Script**.

   ![script de sauvegarde](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>Restaurer une base de données à partir d’un fichier de sauvegarde


1. Ouvrez le **serveurs** encadré (**CTRL + G**), cliquez sur votre serveur, puis sélectionnez **gérer**. 

2. Ouvrez le **restauration de base de données** boîte de dialogue (cliquez sur **restaurer** sur le **tâches** widget).

2. Sélectionnez **le fichier de sauvegarde** dans le **restaurer à partir de** champ. 

3. Cliquez sur les points de suspension (...) dans le **chemin d’accès du fichier de sauvegarde** champ, puis sélectionnez le dernier fichier de sauvegarde pour *TutorialDB*.

3. Type **TutorialDB_Restored** dans le **base de données cible** champ dans le **Destination** section pour restaurer le fichier de sauvegarde à une base de données.

   ![restauration](./media/tutorial-backup-restore-sql-server/restore.png)

4. Cliquez sur **restaurer**

5. Pour afficher l’état de l’opération de restauration, appuyez sur **CTRL + T** pour ouvrir le **l’historique des tâches** encadré.

   ![restauration](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> * Sauvegarde une base de données 
> * Afficher l’état de sauvegarde
> * Générer le script utilisé pour effectuer la sauvegarde
> * Restaurer une base de données
> * Afficher l’état de la tâche de restauration

