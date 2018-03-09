---
title: "Sauvegarder et restaurer une base de données à l’aide des opérations de SQL Studio (version préliminaire) | Documents Microsoft"
description: "Découvrez comment sauvegarder et restaurer une base de données à l’aide des opérations de SQL Studio (version préliminaire)"
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 46ef55aa54275e356eff9674aac10a27b36d758e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="backup-and-restore-using-includename-sosincludesname-sos-shortmd"></a>Sauvegarde et restauration à l’aide[!INCLUDE[name-sos](../includes/name-sos-short.md)]

Dans ce didacticiel, vous apprenez à utiliser [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour :
> [!div class="checklist"]
> * Sauvegarde une base de données 
> * Afficher l’état de sauvegarde
> * Générer le script utilisé pour effectuer la sauvegarde
> * Restaurer une base de données
> * Afficher l’état de la tâche de restauration

## <a name="prerequisites"></a>Prerequisites

Ce didacticiel nécessite SQL Server *TutorialDB*. Pour créer le *TutorialDB* de base de données, effectuez l’une des Démarrages rapides suivants :

- [Se connecter et interroger à l’aide de SQL Server[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)


## <a name="backup-a-database"></a>Sauvegarde une base de données

1. Ouvrir le tableau de bord de base de données TutorialDB (ouvrez le **serveurs** barre latérale (**CTRL + G**), développez **bases de données**, avec le bouton droit **TutorialDB**, Sélectionnez **gérer**). 

2. Ouvrez le **base de données de sauvegarde** boîte de dialogue (cliquez sur **sauvegarde** sur la **tâches** widget).

   ![Widget de tâches](./media/tutorial-backup-restore-sql-server/tasks.png)

3. Ce didacticiel utilise les options de sauvegarde par défaut, cliquez sur **sauvegarde**.
   ![boîte de dialogue de sauvegarde](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

Après avoir cliqué sur **sauvegarde**, le **base de données de sauvegarde** disparaît de la boîte de dialogue et le processus de sauvegarde commence.

## <a name="view-the-backup-status-and-view-the-backup-script"></a>Afficher l’état de sauvegarde et le script de sauvegarde

1. Ouvrez le **l’historique des tâches** encadré en cliquant sur l’icône d’horloge sur le *barre d’Action* ou appuyez sur **CTRL + T**.

   ![Historique des tâches](./media/tutorial-backup-restore-sql-server/task-history.png)

2. Pour afficher le script de sauvegarde dans l’éditeur, avec le bouton droit **sauvegarde de base de données a réussi** et sélectionnez **Script**.

   ![script de sauvegarde](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>Restaurer une base de données à partir d’un fichier de sauvegarde


1. Ouvrez le **serveurs** barre latérale (**CTRL + G**), avec le bouton droit de votre serveur, puis sélectionnez **gérer**. 

2. Ouvrez le **restauration de base de données** boîte de dialogue (cliquez sur **restaurer** sur la **tâches** widget).

2. Sélectionnez **le fichier de sauvegarde** dans les **restaurer à partir de** champ. 

3. Cliquez sur le bouton de sélection (...) dans le **chemin d’accès du fichier de sauvegarde** champ et sélectionnez le dernier fichier de sauvegarde pour *TutorialDB*.

3. Type **TutorialDB_Restored** dans les **base de données cible** champ dans le **Destination** section pour restaurer le fichier de sauvegarde pour une base de données.

   ![restauration](./media/tutorial-backup-restore-sql-server/restore.png)

4. Cliquez sur **restaurer**

5. Pour afficher l’état de l’opération de restauration, cliquez sur **CTRL + T** pour ouvrir le **l’historique des tâches** barre latérale.

   ![restauration](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


Dans ce didacticiel, vous avez appris comment :
> [!div class="checklist"]
> * Sauvegarde une base de données 
> * Afficher l’état de sauvegarde
> * Générer le script utilisé pour effectuer la sauvegarde
> * Restaurer une base de données
> * Afficher l’état de la tâche de restauration

