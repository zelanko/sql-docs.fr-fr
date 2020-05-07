---
title: Guide pratique pour gérer un notebook
description: Découvrez comment gérer des notebooks dans Azure Data Studio. Comprend l’ouverture des notebooks, leur enregistrement ainsi que la modification de votre connexion SQL ou noyau Python.
author: markingmyname
ms.author: maghan
ms.reviewer: achatter, alayu, mikeray
ms.metadata: seo-lt-2019
ms.topic: conceptual
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 04/27/2020
ms.openlocfilehash: 435290bd45e79c835ba134bb732f1672dc31c2cf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82178697"
---
# <a name="how-to-manage-notebooks-in-azure-data-studio"></a>Comment gérer des notebooks dans Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment ouvrir et enregistrer des fichiers de notebooks dans Azure Data Studio. Il montre également comment modifier la connexion à votre serveur SQL Server ou noyau Python.

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

## <a name="change-the-sql-connection"></a>Changer la connexion SQL

Pour changer la connexion SQL pour un notebook :

1. Sélectionnez le menu **Attacher à** dans la barre d’outils du notebook, puis sélectionnez **Changer la connexion**.

   ![Cliquer sur le menu Attacher à dans la barre d’outils du notebook](./media/notebooks-manage-sql-server/select-attach-to-1.png)

2. Vous pouvez maintenant sélectionner un serveur de connexion récent ou entrer de nouveaux détails de connexion pour vous connecter.

   ![Sélectionner un serveur dans le menu Attacher à](./media/notebooks-manage-sql-server/select-attach-to-2.png)

## <a name="change-the-python-kernel"></a>Changer le noyau Python

La première fois que vous ouvrez Azure Data Studio, la page **Configurer Python pour les notebooks** s’affiche. Vous pouvez sélectionner l’une des options suivantes :

- **Nouvelle installation de Python** pour installer une nouvelle copie de Python pour Azure Data Studio
- **Utiliser l’installation existante de Python** pour indiquer à Azure Data Studio le chemin à une installation existante de Python

Pour voir l’emplacement et la version du noyau Python actif, créez une cellule de code et exécutez les commandes Python suivantes :

```python
import os
import sys
print(sys.version_info)
print(os.path.dirname(sys.executable))
```

Pour passer à une autre installation de Python :

1. Dans le menu **Fichier**, sélectionnez **Préférences**, puis **Paramètres**.
1. Faites défiler jusqu’à **Configuration de notebook** sous **Extensions**.
1. Sous **Utiliser l’installation existante de Python**, décochez l’option « Chemin local d’une installation précédente de Python utilisée par Notebooks ».
1. Redémarrez Azure Data Studio.

Quand la page **Configurer Python pour Notebooks** s’ouvre, vous pouvez choisir de créer une installation Python ou de spécifier un chemin à une installation existante.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les notebooks SQL dans Azure Data Studio, consultez [Guide pratique pour utiliser des notebooks dans SQL Server 2019](notebooks-guidance.md).
