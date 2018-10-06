---
title: Comment gérer des ordinateurs portables dans Azure Data Studio | Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: ca756c81dcf54f42cb46be4b0f412ce9630814af
ms.sourcegitcommit: 4832ae7557a142f361fbf0a4e2d85945dbf8fff6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48796251"
---
# <a name="how-to-manage-notebooks-in-azure-data-studio"></a>Comment gérer des ordinateurs portables dans Azure Data Studio

Cet article vous montre comment ouvrir et enregistrer des fichiers de bloc-notes dans Azure Data Studio avec la version préliminaire de SQL Server 2019. Il montre également comment modifier votre connexion à votre cluster de données volumineuses de SQL Server.

## <a name="prerequisites"></a>Prérequis

Cet article suppose que vous disposez déjà d’un bloc-notes que vous souhaitez utiliser dans Azure Data Studio. Si vous souhaitez créer un bloc-notes, consultez [comment utiliser des blocs-notes en version préliminaire de SQL Server 2019](notebooks-guidance.md). Pour utiliser des blocs-notes dans Azure Data Studio, vous devez respecter les conditions préalables suivantes :

- [Installer les derniers outils de données volumineuses pour la version préliminaire de SQL Server 2019](deploy-big-data-tools.md).
- [Déployer un cluster de données volumineuses](quickstart-big-data-cluster-deploy.md).

## <a name="open-a-notebook"></a>Ouvrez un bloc-notes

Il existe plusieurs manières d’ouvrir le **ouvrir le bloc-notes** boîte de dialogue. Vous pouvez utiliser le menu fichier, le tableau de bord et la Palette de commandes. Les sections suivantes décrivent chaque méthode.

### <a name="file-menu"></a>Menu fichier

Sélectionnez **ouvrir le fichier** dans le menu fichier Ctrl + O (dans Windows) et Cmd + O (Mac).

![Ouvrez la boîte de dialogue Ouvrir un fichier en sélectionnant Ouvrir le fichier](./media/notebooks-how-to-manage/open-file-1.png) 

### <a name="dashboard"></a>Tableau de bord

Cliquez sur **ouvrir le bloc-notes** dans le tableau de bord pour ouvrir la boîte de dialogue d’ouverture de fichier.

![Ouvrez la boîte de dialogue Ouvrir un fichier en sélectionnant Ouvrir le bloc-notes dans le tableau de bord](./media/notebooks-how-to-manage/open-file-2.png) 

### <a name="command-palette"></a>Palette de commandes

Utilisez la commande **fichier : ouvrez** à partir de la palette de commandes en tapant Ctrl + Maj + P (dans Windows) et Cmd + Maj + P (sur Mac).

![Ouvrez la boîte de dialogue Ouvrir un fichier en entrant File:Open dans la palette de commandes](./media/notebooks-how-to-manage/open-file-3.png)

## <a name="save-a-notebook"></a>Enregistrez un bloc-notes

Il existe actuellement une méthode pour enregistrer un bloc-notes. Vous devez sélectionner **enregistrer** à partir de la barre d’outils du bloc-notes.

![Enregistrez le fichier en cliquant sur Enregistrer dans la barre d’outils du bloc-notes](./media/notebooks-how-to-manage/save-file-1.png)

> [!NOTE]
> Actuellement les méthodes suivantes n’enregistrement pas les modifications sur les ordinateurs portables :
>
> - **Enregistrement de fichiers**, **fichier Enregistrer sous...**  et **fichier Enregistrer tout** commandes dans le menu fichier.
> - **Fichier : L’enregistrement** commandes entrées dans la palette de commandes.

## <a name="change-the-big-data-cluster"></a>Modifiez le cluster de données volumineuses

Pour modifier le cluster de données volumineuses de SQL Server d’un ordinateur portable :

1. Cliquez sur le **attacher à** menu à partir de la barre d’outils du bloc-notes.

   ![Cliquez sur l’attachement au menu dans la barre d’outils du bloc-notes](./media/notebooks-how-to-manage/select-attach-to-1.png)

2. Cliquez sur un serveur à partir de la **attacher à** menu.

   ![Sélectionnez un serveur à partir de l’attachement au menu](./media/notebooks-how-to-manage/select-attach-to-2.png)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les blocs-notes dans Azure Data Studio, consultez [comment utiliser des blocs-notes en version préliminaire de SQL Server 2019](notebooks-guidance.md).