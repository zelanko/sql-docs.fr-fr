---
title: Créer une extension Jupyter Notebook
description: Découvrir comment empaqueter des notebooks dans une extension à l’aide du générateur d’extensions
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: yualan
ms.author: alayu
ms.reviewer: alayu, maghan
ms.custom: ''
ms.date: 08/28/2020
ms.openlocfilehash: 52a38a8074814737a30cb2f31d22da922eb76901
ms.sourcegitcommit: b6ee0d434b3e42384b5d94f1585731fd7d0eff6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89288151"
---
# <a name="create-a-jupyter-notebook-extension"></a>Créer une extension Jupyter Notebook

Ce tutoriel montre comment créer une extension Azure Data Studio Notebooks. L’extension fournit un exemple Jupyter Notebook que vous pouvez ouvrir et exécuter dans Azure Data Studio.

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> - Créer un projet d’extension
> - Installer le générateur d’extensions
> - Créer votre extension de notebook
> - Exécuter votre extension
> - Empaqueter votre extension
> - Publier votre extension sur le marketplace

## <a name="apis-used"></a>API utilisées

- `azdata.nb.showNotebookDocument`

### <a name="extension-use-cases"></a>Cas d’usage d’extension

Il existe plusieurs raisons de créer une extension de notebook : 
- Partager une documentation interactive 
- Enregistrer ce notebook et pouvoir y accéder en permanence
- Indiquer des problèmes de codage à des utilisateurs pour qu’ils les suivent
- Versionner et suivre les mises à jour de notebooks

## <a name="prerequisites"></a>Prérequis

Azure Data Studio repose sur la même infrastructure que Visual Studio Code, ainsi les extensions pour Azure Data Studio sont générées à l’aide de Visual Studio Code. Pour commencer, vous avez besoin des composants suivants :

- [Node.js](https://nodejs.org) installé et disponible dans votre `$PATH`. Node. js comprend [npm](https://www.npmjs.com/), le gestionnaire de packages Node.js, qui est utilisé pour installer le générateur d’extensions.
- [Visual Studio Code](https://code.visualstudio.com) pour déboguer l’extension.
- Vérifiez que `azuredatastudio` se trouve dans votre chemin d’accès. Pour Windows, veillez à choisir l'option `Add to Path` dans setup.exe. Pour Mac ou Linux, exécutez l’option *Installer la commande 'azuredatastudio' dans CHEMIN D’ACCÈS*.

## <a name="install-the-extension-generator"></a>Installer le générateur d’extensions

Pour simplifier le processus de création d’extensions, nous avons créé un [générateur d’extensions](https://www.npmjs.com/package/generator-azuredatastudio) à l’aide de Yeoman. Pour l’installer, exécutez la commande suivante à partir de l’invite de commandes :

```console
`npm install -g yo generator-azuredatastudio`
```

## <a name="create-your-extension"></a>Créer votre extension

Pour créer une extension :

1. Lancez le générateur d’extensions avec la commande suivante :

   `yo azuredatastudio`

2. Choisissez **Nouveaux notebooks (individuels)** dans la liste des types d’extensions :

   :::image type="content" source="media/notebook-extension/notebook-extension-generator.png" alt-text="Générateur d’extensions de notebook":::

3. Suivez les étapes pour renseigner le nom de l’extension (pour ce tutoriel, utilisez **Test Notebook**), un nom d’éditeur (pour ce tutoriel, utilisez **Microsoft**) et ajoutez une description.

Vous avez maintenant un choix à faire : soit vous ajoutez des notebooks Jupyter que vous avez déjà créés, soit vous utilisez les exemples de notebooks que vous fournit le générateur.

Pour ce tutoriel, nous allons utiliser un exemple de notebook Python :

   :::image type="content" source="media/notebook-extension/notebook-sample-generator.png" alt-text="Sélectionner un exemple Python":::

Si vous avez des notebooks que vous voulez distribuer, faites la réponse correspondante et indiquez le chemin absolu de tous vos notebooks ou fichiers Markdown.

Les étapes précédentes permettent de créer un dossier contenant l’exemple de notebook. Ouvrez le dossier dans Visual Studio Code et vous êtes prêt à distribuer votre nouvelle extension de notebook !

## <a name="understanding-your-extension"></a>Comprendre votre extension

Voici ce à quoi votre projet devrait ressembler actuellement :

   :::image type="content" source="media/notebook-extension/notebook-file-structure-generator.png" alt-text="Structure de fichiers d’extension":::

Le fichier `vsc-extension-quickstart.md` sert de référence sur les fichiers importants. Le fichier `README.md` est l’emplacement auquel vous pouvez fournir de la documentation pour votre nouvelle extension. Remarquez les fichiers `package.json`, `notebook.ts` et `pySample.ipynb`.

S’il existe des fichiers ou dossiers que vous ne voulez pas publier, vous pouvez inclure leurs noms dans le fichier `.vscodeignore`.

Intéressons-nous au fichier `notebook.ts` pour comprendre à quoi sert notre extension nouvellement formée.

```javascript
// This function is called when you run the command `Launch Notebooks: Test Notebook` from
// command palette in Azure Data Studio. If you would like any additional functionality
// to occur when you launch the book, add to the activate function.
export function activate(context: vscode.ExtensionContext) {
    context.subscriptions.push(vscode.commands.registerCommand('launchNotebooks.test-notebook', () => {
        let notebooksToDisplay: Array<string> = processNotebooks();
        notebooksToDisplay.forEach(name => {
            azdata.nb.showNotebookDocument(vscode.Uri.file(name));
        });
    }));

    // Add other code here if you want to register another command
}
```

Il s’agit de la fonction principale dans `notebook.ts` qui est appelée chaque fois que nous exécutons l’extension par le biais de la commande, **Launch Notebooks : Test Notebook**. Nous créons notre commande à l’aide de l’API `vscode.commands.registerCommand`. La définition suivante à l’intérieur des accolades correspond au code exécuté chaque fois que nous appelons notre commande. Chaque notebook trouvé à partir de notre fonction `processNotebooks` est ouvert dans Azure Data Studio à l’aide de `azdata.nb.showNotebookDocument`. 

Le fichier `package.json` joue également un rôle important dans l’inscription de notre commande, **Launch Notebooks : Test Notebook**.

```json
"activationEvents": [
        "onCommand:launchNotebooks.test-notebook"
    ],
    "main": "./out/notebook.js",
    "contributes": {
        "commands": [
            {
                "command": "launchNotebooks.test-notebook",
                "title": "Launch Notebooks: Test Notebook"
            }
        ]
    }
```

Nous avons un événement d’activation pour la commande et nous avons également ajouté des points de contribution spécifiques. Ceux-ci apparaissent dans le marketplace d’extensions, où les extensions sont publiées, quand les utilisateurs examinent la vôtre. Quand vous ajoutez des commandes supplémentaires, veillez à les ajouter au champ `activationEvents`. Pour plus d’options, consultez [Événements d’activation](https://code.visualstudio.com/api/references/activation-events).

## <a name="package-your-extension"></a>Empaqueter votre extension

Pour partager votre extension avec d’autres personnes, vous devez l’empaqueter dans un fichier unique. Il peut être publié sur le marketplace d’extensions Azure Data Studio ou partagé avec votre équipe ou votre communauté. Pour ce faire, vous devez installer un autre package npm à partir de la ligne de commande :

```console
`npm install -g vsce`
```

Modifiez le fichier `README.md` à votre gré, puis accédez au répertoire de base de l’extension et exécutez `vsce package`. Vous pouvez éventuellement lier un référentiel à votre extension ou continuer sans référentiel. Pour en ajouter un, ajoutez une ligne similaire à votre fichier `package.json`.

```json
"repository": {
    "type": "git",
    "url": "https://github.com/laurajjiang/testnotebook.git"
}
```

Une fois cette opération effectuée, le fichier test-notebook-0.0.1.vsix a été créé et est prêt à être installé et partagé avec le monde entier !

## <a name="run-your-extension"></a>Exécuter votre extension

Pour exécuter et tester votre extension, ouvrez Azure Data Studio et ouvrez la palette de commandes (`Ctrl + Shift + P`). Recherchez la commande **Extensions : Installer à partir d’un VSIX** et accédez au dossier contenant votre nouvelle extension.

   :::image type="content" source="media/notebook-extension/install-vsix.png" alt-text="Installer VSIX":::

Celle-ci doit maintenant apparaître dans le panneau de votre extension dans Azure Data Studio. Rouvrez la palette de commandes et recherchez la nouvelle commande que nous avons créée avec notre extension, **Launch Book : Test Book**. Lors de son exécution, le Jupyter Book que nous avons empaqueté doit s’ouvrir avec notre extension.

   :::image type="content" source="media/notebook-extension/notebook-launch-ads.png" alt-text="Notebook-command":::

Félicitations ! Vous avez créé votre première extension Jupyter Notebook et vous pouvez maintenant la distribuer.

## <a name="publish-your-extension-to-the-marketplace"></a>Publier votre extension sur le marketplace

Le marketplace d’extensions Azure Data Studio n’est pas encore totalement implémenté. Pour publier, hébergez le fichier VSIX de l’extension quelque part (par exemple, une page GitHub) et envoyez une demande de tirage (pull request) qui met à jour [ce fichier JSON](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json) avec les informations de votre extension.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> - Créer un projet d’extension
> - Installer le générateur d’extensions - Créer votre extension de notebook
> - Créer votre extension
> - Empaqueter votre extension
> - Publier votre extension sur le marketplace

Nous espérons qu’après avoir lu cela, vous serez inspiré pour créer votre propre extension pour Azure Data Studio.

Si vous avez une idée mais que vous ne savez pas par où commencer, veuillez ouvrir un problème ou envoyer un tweet à l’équipe [azuredatastudio](https://twitter.com/azuredatastudio).

Vous pouvez toujours vous reporter au [guide pour les extensions Visual Studio Code](https://code.visualstudio.com/docs/extensions/overview), car il couvre toutes les API et tous les modèles existants.