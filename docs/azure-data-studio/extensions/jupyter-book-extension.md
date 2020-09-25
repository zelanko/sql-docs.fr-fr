---
title: Créer une extension Jupyter Book
description: Découvrir comment créer un package Jupyter Book dans une extension à l’aide du générateur d’extensions
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: yualan
ms.author: alayu
ms.reviewer: alayu, maghan
ms.custom: ''
ms.date: 08/28/2020
ms.openlocfilehash: a781affee2db40dbd7636c25712ca622c881650e
ms.sourcegitcommit: 8f062015c2a033f5a0d805ee4adabbe15e7c8f94
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91226836"
---
# <a name="create-a-jupyter-book-extension"></a>Créer une extension Jupyter Book

Ce tutoriel montre comment créer une extension Azure Data Studio Jupyter Book. L’extension fournit un exemple Jupyter Book que vous pouvez ouvrir et exécuter dans Azure Data Studio. 

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> - Créer un projet d’extension
> - Installer le générateur d’extensions
> - Créer votre extension Jupyter Book
> - Exécuter votre extension
> - Empaqueter votre extension
> - Publier votre extension sur le marketplace

## <a name="apis-used"></a>API utilisées

- `bookTreeView.openBook`

### <a name="extension-use-cases"></a>Cas d’usage d’extension

Il existe plusieurs raisons de créer une extension Jupyter Book :

- Partager une documentation interactive organisée et divisée en sections
- Partager un notebook complet (semblable à un livre électronique, mais distribué par le biais d’Azure Data Studio)
- Versionner et suivre les mises à jour de Jupyter Book

La principale différence entre une extension Jupyter Book et une extension de notebook est que la première vous fournit une organisation. Des dizaines de notebooks peuvent être répartis dans les différents chapitres d’un livre, mais l’extension des notebooks a pour but de fournir un petit nombre de notebooks individuels.

## <a name="prerequisites"></a>Prérequis

Azure Data Studio repose sur la même infrastructure que Visual Studio Code, ainsi les extensions pour Azure Data Studio sont générées à l’aide de Visual Studio Code. Pour commencer, vous avez besoin des composants suivants :

- [Node.js](https://nodejs.org) installé et disponible dans votre `$PATH`. Node. js comprend [npm](https://www.npmjs.com/), le gestionnaire de packages Node.js, qui est utilisé pour installer le générateur d’extensions.
- [Visual Studio Code](https://code.visualstudio.com) pour apporter des modifications à votre extension et la déboguer.
- Vérifiez que `azuredatastudio` se trouve dans votre chemin d’accès. Pour Windows, veillez à choisir l'option `Add to Path` dans setup.exe. Pour Mac ou Linux, exécutez l’option *Installer la commande 'azuredatastudio' dans CHEMIN D’ACCÈS*.

## <a name="install-the-extension-generator"></a>Installer le générateur d’extensions

Pour simplifier le processus de création d’extensions, nous avons créé un [générateur d’extensions](https://www.npmjs.com/package/generator-azuredatastudio) à l’aide de Yeoman. Pour l’installer, exécutez la commande suivante à partir de l’invite de commandes :

```console
`npm install -g yo generator-azuredatastudio`
```

## <a name="create-your-extension"></a>Créer votre extension

Pour créer une extension :

1. Lancez le générateur d’extensions avec la commande suivante :

   `yo azuredatastudio`

2. Choisissez **Nouveau Jupyter Book** dans la liste des types d’extensions :

   :::image type="content" source="media/jupyter-book-extension/jupyter-book-extension-generator.png" alt-text="Générateur d’extensions":::

3. Suivez les étapes pour renseigner le nom de l’extension (pour ce tutoriel, utilisez **Test Book**), un nom d’éditeur (pour ce tutoriel, utilisez **Microsoft**) et ajoutez une description.

Vous choisissez de fournir un Jupyter Book existant, d’utiliser un exemple fourni ou de créer un Jupyter Book. Ces trois options sont présentées ci-dessous.

### <a name="providing-an-existing-book"></a>Fournir un livre existant

Si vous voulez fournir un livre que vous avez déjà créé, indiquez le chemin absolu du dossier dans lequel se trouve son contenu. Vous pouvez alors commencer à vous familiariser avec l’extension et sa distribution.

:::image type="content" source="media/jupyter-book-extension/jupyter-book-existing-book.png" alt-text="Livre existant":::

### <a name="using-the-sample-book"></a>Utilisation de l’exemple de livre

Si vous n’avez pas de livre ou notebooks existants, vous pouvez utiliser l’exemple fourni dans le générateur.

:::image type="content" source="media/jupyter-book-extension/jupyter-book-sample-path.png" alt-text="Exemple de Jupyter Book":::

L’exemple de livre montre à quoi ressemble un Jupyter Book simple. Pour en savoir plus sur la personnalisation d’un Jupyter Book, consultez la section suivante sur la création d’un livre avec des notebooks existants.

### <a name="creating-a-new-book"></a>Création d’un livre

Si vous avez des notebooks que vous souhaitez empaqueter dans un Jupyter Book, c’est possible. Le générateur vous demande si vous voulez des chapitres dans votre livre et, le cas échéant, leur nombre et leurs titres. Vous pouvez voir à quoi ressemble le processus de sélection ci-dessous. Utilisez la barre d’espace pour sélectionner les notebooks à placer dans chaque chapitre.

:::image type="content" source="media/jupyter-book-extension/jupyter-book-create-book.png" alt-text="Créer un Jupyter Book":::

Les étapes précédentes permettent de créer un dossier contenant votre nouveau Jupyter Book. Ouvrez le dossier dans Visual Studio Code et vous êtes prêt à distribuer votre extension Jupyter Book !

## <a name="understanding-your-extension"></a>Comprendre votre extension

Voici ce à quoi votre projet devrait ressembler actuellement :

   :::image type="content" source="media/jupyter-book-extension/jupyter-book-file-structure-generator.png" alt-text="Structure de fichiers d’extension":::

Le fichier `vsc-extension-quickstart.md` sert de référence sur les fichiers importants. Le fichier `README.md` est l’emplacement auquel vous pouvez fournir de la documentation pour votre nouvelle extension. Remarquez les fichiers `package.json`, `jupyter-book.ts`, `content` et `toc.yml`. Le dossier `content` contient tous les fichiers Markdown et fichiers de notebook. Le fichier `toc.yml` structure votre Jupyter Book. Il est généré automatiquement si vous avez choisi de créer un Jupyter Book personnalisé par le biais du générateur d’extensions.

Si vous aviez créé un livre à l’aide du générateur et choisi d’utiliser des chapitres dans votre livre, votre structure de dossiers serait légèrement différente. Au lieu d’avoir vos fichiers Markdown et Jupyter Notebook dans le dossier `content`, vous auriez des sous-dossiers correspondant aux titres que vous avez choisis pour vos chapitres. 

S’il existe des fichiers ou dossiers que vous ne voulez pas publier, vous pouvez inclure leurs noms dans le fichier `.vscodeignore`.

Intéressons-nous au fichier `jupyter-book.ts` pour comprendre à quoi sert notre extension nouvellement formée.

```javascript
// This function is called when you run the command `Launch Book: Test Book` from
// command palette in Azure Data Studio. If you would like any additional functionality
// to occur when you launch the book, add to the activate function.
export function activate(context: vscode.ExtensionContext) {
    context.subscriptions.push(vscode.commands.registerCommand('launchBook.test-book', () => {
        processNotebooks();
    }));

    // Add other code here if you want to register another command
}
```

La fonction `activate` est l’action principale de votre extension. Toutes les commandes à inscrire doivent apparaître à l’intérieur de la fonction `activate`, de la même façon que notre commande `launchBook.test-book`. À l’intérieur de la fonction `processNotebooks`, nous trouvons notre dossier d’extension qui contient notre Jupyter Book et nous appelons `bookTreeView.openBook` en utilisant le dossier de notre extension comme paramètre. 

Le fichier `package.json` joue également un rôle important dans l’inscription de la commande de notre extension :

```json
"activationEvents": [
        "onCommand:launchBook.test-book"
    ],
    "main": "./out/notebook.js",
    "contributes": {
        "commands": [
            {
                "command": "launchBook.test-book",
                "title": "Launch Book: Test Book"
            }
        ]
    }
```

L’événement d’activation, `onCommand`, déclenche la fonction que nous avons inscrite lors de l’appel de la commande. Il existe quelques autres événements d’activation possibles pour une personnalisation accrue. Pour plus d’informations, consultez [Événements d’activation](https://code.visualstudio.com/api/references/activation-events).

## <a name="package-your-extension"></a>Empaqueter votre extension

Pour partager votre extension avec d’autres personnes, vous avez besoin de l’empaqueter dans un fichier unique. Ce fichier peut être publié sur le marketplace d’extensions Azure Data Studio ou partagé avec votre équipe ou votre communauté. Pour ce faire, vous devez installer un autre package npm à partir de la ligne de commande :

```console
`npm install -g vsce`
```

Modifiez le fichier `README.md` à votre gré, puis accédez au répertoire de base de l’extension et exécutez `vsce package`. Vous pouvez éventuellement lier un référentiel à votre extension ou continuer sans référentiel. Pour en ajouter un, ajoutez une ligne similaire à votre fichier `package.json`.

```json
"repository": {
    "type": "git",
    "url": "https://github.com/laurajjiang/testbook.git"
}
```

Une fois ces lignes ajoutées, le fichier test-book-0.0.1.vsix est créé et prêt à être installé dans Azure Data Studio.

## <a name="run-your-extension"></a>Exécuter votre extension

Pour exécuter et tester votre extension, ouvrez Azure Data Studio et ouvrez la palette de commandes (`Ctrl + Shift + P`). Recherchez la commande **Extensions : Installer à partir d’un VSIX** et accédez au dossier contenant votre nouvelle extension. Celle-ci doit maintenant apparaître dans le panneau de votre extension dans Azure Data Studio.

   :::image type="content" source="media/jupyter-book-extension/install-vsix.png" alt-text="Installer VSIX":::

Rouvrez la palette de commandes et recherchez la commande que nous avons inscrite, **Launch Book : Test Notebook**. Lors de son exécution, le Jupyter Book que nous avons empaqueté doit s’ouvrir avec notre extension.

   :::image type="content" source="media/jupyter-book-extension/jupyter-book-launch-ads.png" alt-text="Notebook-command":::

Félicitations ! Vous avez créé votre première extension Jupyter Book et vous pouvez maintenant la distribuer. Pour plus d’informations sur Jupyter Book, consultez [Books with Jupyter](https://jupyterbook.org/intro.html).

## <a name="publish-your-extension-to-the-marketplace"></a>Publier votre extension sur le marketplace

Le marketplace d’extensions Azure Data Studio n’est pas encore totalement implémenté. Pour publier, hébergez le fichier VSIX de l’extension quelque part (par exemple, une page GitHub) et envoyez une demande de tirage (pull request) qui met à jour [ce fichier JSON](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json) avec les informations de votre extension.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> - Créer un projet d’extension
> - Installer le générateur d’extensions
> - Créer votre extension Jupyter Book
> - Empaqueter votre extension
> - Publier votre extension sur le marketplace

Nous espérons que la lecture de cet article sur Jupyter Book vous aura donné envie de partager vos idées avec la communauté Azure Data Studio. 

Si vous avez une idée mais que vous ne savez pas par où commencer, ouvrez un problème ou envoyer un tweet à l’équipe [azuredatastudio](https://twitter.com/azuredatastudio).

Vous pouvez toujours vous reporter au [guide pour les extensions Visual Studio Code](https://code.visualstudio.com/docs/extensions/overview), car il couvre toutes les API et tous les modèles existants.
