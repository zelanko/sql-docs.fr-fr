---
title: Gérer un notebook SQL Server
description: Découvrez comment gérer des notebooks dans Azure Data Studio. Cette gestion comprend l’ouverture des notebooks, leur enregistrement, ainsi que la modification de la connexion de votre cluster Big Data.
author: markingmyname
ms.author: maghan
ms.reviewer: achatter, alayu, mikeray
ms.metadata: seo-lt-2019
ms.topic: conceptual
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 03/30/2020
ms.openlocfilehash: 9b071a9d1b9e770e1443e5df539208baa4399a30
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531592"
---
# <a name="how-to-manage-notebooks-in-azure-data-studio"></a>Comment gérer des notebooks dans Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article vous explique comment ouvrir et enregistrer des fichiers de notebooks dans Azure Data Studio avec SQL Server. Il montre également comment changer la connexion à votre serveur SQL Server.

## <a name="open-a-notebook"></a>Ouvrir un notebook

Il existe plusieurs façons d’ouvrir la boîte de dialogue **Ouvrir le notebook**. Vous pouvez utiliser le menu Fichier, le tableau de bord et la palette de commandes. Les sections suivantes décrivent chacune de ces méthodes.

### <a name="file-menu"></a>Menu Fichier

Sélectionnez **Fichier : Ouvrir** dans le menu Fichier (CTRL + O dans Windows) et (Cmd + O sur Mac).

![Ouvrir la boîte de dialogue Ouvrir un fichier en sélectionnant Fichier : Ouvrir](./media/notebooks-manage-sql-server/open-file-1.png)

### <a name="dashboard"></a>tableau de bord

Cliquez sur **Ouvrir le notebook** dans le tableau de bord pour ouvrir la boîte de dialogue Fichier : Ouvrir.

![Ouvrir la boîte de dialogue Ouvrir un fichier en sélectionnant Ouvrir le notebook dans le tableau de bord](./media/notebooks-manage-sql-server/open-file-2.png) 

### <a name="command-palette"></a>Palette de commandes

Utilisez la commande **Fichier : Ouvrir** à partir de la palette de commandes en appuyant sur les touches Ctrl+Maj+P (sur Windows) ou sur Cmd+Maj+P (sur Mac).

![Ouvrir la boîte de dialogue Ouvrir un fichier en entrant File: Open dans la palette de commandes](./media/notebooks-manage-sql-server/open-file-3.png)

## <a name="save-a-notebook"></a>Enregistrer un notebook

Il existe actuellement une seule façon d’enregistrer un notebook. Sélectionnez **Enregistrer** dans la barre d’outils du notebook.

![Enregistrer le fichier en sélectionnant Enregistrer dans la barre d’outils du notebook](./media/notebooks-manage-sql-server/save-file-1.png)

> [!NOTE]
> Les méthodes suivantes ne permettent pas d’enregistrer les modifications apportées aux notebooks :
>
> - **Fichier : Enregistrer**, **Fichier : Enregistrer sous...** et **Fichier : Tout enregistrer** dans le menu Fichier.
> - **Fichier : Enregistrer** dans la palette de commandes.

## <a name="change-the-connection"></a>Changer la connexion

Pour changer la connexion pour un notebook :

1. Sélectionnez le menu **Attacher à** dans la barre d’outils du notebook, puis sélectionnez **Changer la connexion**.

   ![Cliquer sur le menu Attacher à dans la barre d’outils du notebook](./media/notebooks-manage-sql-server/select-attach-to-1.png)

2. Vous pouvez maintenant sélectionner un serveur de connexion récent ou entrer de nouveaux détails de connexion pour vous connecter.

   ![Sélectionner un serveur dans le menu Attacher à](./media/notebooks-manage-sql-server/select-attach-to-2.png)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’utilisation des notebooks dans Azure Data Studio, consultez [Guide pratique pour utiliser des notebooks dans SQL Server 2019](notebooks-guidance.md).
