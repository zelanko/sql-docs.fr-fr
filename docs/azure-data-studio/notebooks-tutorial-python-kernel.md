---
title: Notebooks avec noyau Python dans Azure Data Studio
description: Ce tutoriel vous montre comment créer et exécuter un notebook Python.
author: garyericson
ms.author: garye
ms.reviewer: mikeray, alayu, maghan
ms.topic: tutorial
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 04/27/2020
ms.openlocfilehash: 8d0666c74f464535d2de08dd44e92c521cfcd73f
ms.sourcegitcommit: 4f4ca7075a73a7a4d7196dcb279c58e15c2daf37
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196791"
---
# <a name="create-and-run-a-python-notebook"></a>Créer et exécuter un notebook Python

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ce tutoriel montre comment créer et exécuter un notebook dans Azure Data Studio à l’aide du noyau Python.

## <a name="prerequisites"></a>Prérequis

- [Azure Data Studio installé](download-azure-data-studio.md)

## <a name="new-notebook"></a>Nouveau notebook

Les étapes suivantes montrent comment créer un fichier de notebook dans Azure Data Studio :

1. Ouvrez Azure Data Studio. Si vous êtes invité à vous connecter à un serveur SQL Server, vous pouvez le faire ou cliquer sur **Annuler**.

1. Sélectionnez **Nouveau notebook** dans le menu **Fichier**.

1. Sélectionnez **Python 3** comme **Noyau**.

   :::image type="content" source="media/notebook-tutorial-python/set-kernel-and-attach-to-python.png" alt-text="Définir le noyau":::

1. Si vous êtes invité à configurer Python, sélectionnez l’une des deux options suivantes dans **Configurer Python pour les notebooks** :

   - **Nouvelle installation de Python** pour installer une nouvelle copie de Python pour Azure Data Studio
   - **Utiliser l’installation existante de Python** pour spécifier le chemin à une installation existante de Python

## <a name="run-a-notebook-cell"></a>Exécuter une cellule de notebook

Vous pouvez créer des cellules contenant du code ou du texte. Une cellule de code peut être exécutée sur place. Dans ce cas, les résultats s’affichent dans le notebook une fois l’exécution de la cellule terminée. Les cellules de texte vous permettent d’entrecouper votre code d’une documentation mise en forme.

### <a name="code"></a>Code

Ajoutez une nouvelle cellule de code Python en sélectionnant la commande **+ Code** dans la barre d’outils.

:::image type="content" source="media/notebook-tutorial-python/notebook-toolbar-python.png" alt-text="Barre d’outils du notebook":::

Cet exemple effectue des opérations mathématiques simples.

```python
a = 1
b = 2
c = a/b
print(c)
```
Exécutez la cellule en cliquant sur le bouton de lecture situé à gauche de la cellule. Les résultats apparaissent ci-dessous.

:::image type="content" source="media/notebook-tutorial-python/run-notebook-cell-python.png" alt-text="Exécuter la cellule du notebook":::

### <a name="text"></a>Texte

Ajoutez une nouvelle cellule de texte en sélectionnant la commande **+ Texte** dans la barre d’outils.

:::image type="content" source="media/notebook-tutorial-python/notebook-toolbar-python-text.png" alt-text="Barre d’outils du notebook":::

La cellule passe en mode édition. Vous pouvez maintenant taper du code Markdown et voir l’aperçu en même temps.

:::image type="content" source="media/notebook-tutorial-python/notebook-markdown-cell-python.png" alt-text="Cellule Markdown":::

Si vous sélectionnez un élément en dehors de la cellule de texte, seul le texte Markdown apparaît.

:::image type="content" source="media/notebook-tutorial-python/notebook-markdown-preview-python.png" alt-text="Texte Markdown":::

## <a name="next-steps"></a>Étapes suivantes

Découvrez-en plus sur les notebooks :

- [Guide pratique pour utiliser des notebooks avec SQL Server](notebooks-guidance.md)

- [Créer et exécuter un notebook SQL Server](notebooks-tutorial-sql-kernel.md)

- [Comment gérer des notebooks dans Azure Data Studio](notebooks-manage-sql-server.md)
