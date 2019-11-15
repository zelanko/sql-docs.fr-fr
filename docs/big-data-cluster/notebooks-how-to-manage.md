---
title: Gérer des notebooks dans Azure Data Studio
titleSuffix: SQL Server big data clusters
description: Découvrez comment gérer des notebooks dans Azure Data Studio. Cette gestion comprend l’ouverture des notebooks, leur enregistrement, ainsi que la modification de la connexion de votre cluster Big Data.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: fb081c84de1fc9548ef1ea1f19bb2e286d0be636
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844274"
---
# <a name="how-to-manage-notebooks-in-azure-data-studio"></a>Comment gérer des notebooks dans Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article vous explique comment ouvrir et enregistrer des fichiers de notebooks dans Azure Data Studio avec SQL Server. Il montre également comment modifier la connexion à votre cluster Big Data SQL Server.

## <a name="prerequisites"></a>Conditions préalables requises

Cet article part du principe que vous disposez déjà d’un notebook à utiliser dans Azure Data Studio. Si vous voulez créer un notebook, consultez [Guide pratique pour utiliser des notebooks dans SQL Server](notebooks-guidance.md). Pour utiliser des notebooks dans Azure Data Studio, vous devez respecter les prérequis suivants :

- [Déployer un cluster Big Data](quickstart-big-data-cluster-deploy.md)
- [Outils de Big Data SQL Server 2019](deploy-big-data-tools.md) :
   - **Azure Data Studio**
   - **Extension SQL Server 2019**
   - **kubectl**

## <a name="open-a-notebook"></a>Ouvrir un notebook

Il existe plusieurs façons d’ouvrir la boîte de dialogue **Ouvrir le notebook**. Vous pouvez utiliser le menu Fichier, le tableau de bord et la palette de commandes. Les sections suivantes décrivent chacune de ces méthodes.

### <a name="file-menu"></a>Menu Fichier

Sélectionnez **Fichier : Ouvrir** dans le menu Fichier (CTRL + O dans Windows) et (Cmd + O sur Mac).

![Ouvrir la boîte de dialogue Ouvrir un fichier en sélectionnant Fichier : Ouvrir](./media/notebooks-how-to-manage/open-file-1.png) 

### <a name="dashboard"></a>Tableau de bord

Cliquez sur **Ouvrir le notebook** dans le tableau de bord pour ouvrir la boîte de dialogue Fichier : Ouvrir.

![Ouvrir la boîte de dialogue Ouvrir un fichier en sélectionnant Ouvrir le notebook dans le tableau de bord](./media/notebooks-how-to-manage/open-file-2.png) 

### <a name="command-palette"></a>Palette de commandes

Utilisez la commande **Fichier : Ouvrir** à partir de la palette de commandes en appuyant sur les touches Ctrl+Maj+P (sur Windows) ou sur Cmd+Maj+P (sur Mac).

![Ouvrir la boîte de dialogue Ouvrir un fichier en entrant Fichier : Ouvrir dans la palette de commandes](./media/notebooks-how-to-manage/open-file-3.png)

## <a name="save-a-notebook"></a>Enregistrer un notebook

Il existe actuellement une seule façon d’enregistrer un notebook. Pour cela, vous devez sélectionner **Enregistrer** dans la barre d’outils du notebook.

![Enregistrer le fichier en cliquant sur Enregistrer dans la barre d’outils du notebook](./media/notebooks-how-to-manage/save-file-1.png)

> [!NOTE]
> Les méthodes suivantes ne permettent pas d’enregistrer les modifications apportées aux notebooks :
>
> - **Fichier : Enregistrer**, **Fichier : Enregistrer sous...** et **Fichier : Tout enregistrer** dans le menu Fichier.
> - **Fichier : Enregistrer** dans la palette de commandes.

## <a name="change-the-big-data-cluster"></a>Modifier le cluster Big Data

Pour modifier le cluster Big Data SQL Server d’un notebook :

1. Cliquez sur le menu **Attacher à** dans la barre d’outils du notebook.

   ![Cliquer sur le menu Attacher à dans la barre d’outils du notebook](./media/notebooks-how-to-manage/select-attach-to-1.png)

2. Cliquez sur un serveur dans le menu **Attacher à**.

   ![Sélectionner un serveur dans le menu Attacher à](./media/notebooks-how-to-manage/select-attach-to-2.png)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’utilisation des notebooks dans Azure Data Studio, consultez [Guide pratique pour utiliser des notebooks dans SQL Server 2019](notebooks-guidance.md).
