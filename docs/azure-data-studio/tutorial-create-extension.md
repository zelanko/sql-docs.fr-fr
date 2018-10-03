---
title: 'Didacticiel : Créer une extension pour Azure Data Studio | Microsoft Docs'
description: Ce didacticiel montre comment créer une extension pour Azure Data Studio.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: tutorial
author: kevcunnane
ms.author: kcunnane
manager: craigg
ms.openlocfilehash: 9124ced20d5b10bbb60cbfbda6b3e4c9a52a3a1f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038468"
---
# <a name="tutorial-create-an-azure-data-studio-extension"></a>Didacticiel : Créer une extension d’Azure Data Studio

Ce didacticiel montre comment créer une nouvelle extension Azure Data Studio. L’extension crée des combinaisons de touches SSMS familiers dans Azure Data Studio.

Au cours de ce didacticiel, vous découvrez comment :
> [!div class="checklist"]
> * Créez un projet d’extension
> * Installer le Générateur d’extension
> * Créer votre extension
> * Tester votre extension
> * Votre extension de package
> * Publier votre extension à la place de marché

## <a name="prerequisites"></a>Prérequis

Azure Data Studio repose sur la même infrastructure en tant que Visual Studio Code, donc les extensions pour Azure Data Studio sont créées à l’aide de Visual Studio Code. Pour commencer, vous devez les composants suivants :

- [Node.js](https://nodejs.org) installé et disponible dans votre `$PATH`. Node.js inclut [npm](https://www.npmjs.com/), le Gestionnaire de Package Node.js, qui est utilisé pour installer le Générateur d’extension.
- [Visual Studio Code](https://code.visualstudio.com) pour déboguer l’extension.
- Azure données Studio [d’extension de débogage](https://marketplace.visualstudio.com/items?itemName=ms-mssql.sqlops-debug).
- Vérifiez que sqlops est dans votre chemin d’accès. Pour Windows, veillez à choisir la `Add to Path` option dans setup.exe. Pour Mac ou Linux, exécutez le *installer 'sqlops' commande dans le chemin d’accès* option.
- Extension de débogage de SQL Operations Studio (facultatif). Cela vous permet de tester votre extension sans avoir à empaqueter et installez-le dans Azure Data Studio.


## <a name="install-the-extension-generator"></a>Installer le Générateur d’extension

Pour simplifier le processus de création d’extensions, nous avons créé un [Générateur d’extension](https://code.visualstudio.com/docs/extensions/yocode) à l’aide de Yeoman. Pour l’installer, exécutez la commande suivante à partir de l’invite de commandes :

`npm install -g yo generator-sqlops`

## <a name="create-your-extension"></a>Créer votre extension

Pour créer une extension :

1. Lancer le Générateur d’extension avec la commande suivante :

   `yo sqlops`

2. Choisissez **le nouveau** à partir de la liste des types d’extension :

   ![Générateur d’extension](./media/tutorial-create-extension/extension-generator.png)

3. Suivez les étapes pour renseigner le nom d’extension (pour ce didacticiel, utilisez **ssmskeymap**) et ajouter une description.

Les étapes précédentes crée un nouveau dossier. Ouvrez le dossier dans Visual Studio Code et que vous êtes prêt à créer votre propre extension de la combinaison de touches !


### <a name="add-a-keyboard-shortcut"></a>Ajouter un raccourci clavier

**Étape 1 : Rechercher les raccourcis à remplacer**

Maintenant que nous avons notre extension prête à l’emploi, ajoutez certains SSMS clavier raccourcis (ou combinaisons de touches) dans Azure Data Studio. J’ai utilisé [Fiche récapitulative de Andy Mallon](https://am2.co/2018/02/updated-cheat-sheet/) et liste de raccourcis clavier de RedGate d’inspiration.

Les choses primordiales que j’ai vu manquantes ont été :

- Exécuter une requête avec le plan d’exécution réel activé. Il s’agit de **Ctrl + M** dans SSMS et n’a pas une liaison dans Azure Data Studio.
- Avoir **CTRL + MAJ + E** comme un moyen 2nd de l’exécution d’une requête. Commentaires de l’utilisateur indiquent que c’était manquant.
- Avoir **ALT + F1** exécuter `sp_help`. Nous avons ajouté cela dans Azure Data Studio, mais étant donné que cette liaison était déjà en cours d’utilisation, nous avons mappé à **ALT + F2** à la place.
- Plein écran (**MAJ + ALT + ENTRÉE**).
- **F8** pour afficher **Explorateur d’objets** / **affichage serveurs**.

Il est facile de rechercher et remplacer ces combinaisons de touches. Exécutez *des raccourcis clavier Open* pour afficher le **raccourcis clavier** onglet dans Azure Data Studio, recherchez *requête* , puis choisissez **combinaison de touches de modification**. Une fois que vous avez terminé la modification de la combinaison de touches vous pouvez voir le mappage mis à jour dans le fichier keybindings.json (exécuter *des raccourcis clavier Open* pour l’afficher).

![raccourcis clavier](./media/tutorial-create-extension/keyboard-shortcuts.png)

![extension de KeyBindings.JSON](./media/tutorial-create-extension/keybindings-json.png)


**Étape 2 : Ajouter des raccourcis vers l’extension**

Pour ajouter des raccourcis vers l’extension, ouvrez le *package.json* fichier (dans l’extension) et remplacez le `contributes` section avec les éléments suivants :

```json
"contributes": {
  "keybindings": [
    {
      "key": "shift+cmd+e",
      "command": "runQueryKeyboardAction"
    },
    {
      "key": "ctrl+cmd+e",
      "command": "workbench.view.explorer"
    },
    {
      "key": "alt+f1",
      "command": "workbench.action.query.shortcut1"
    },
    {
      "key": "shift+alt+enter",
      "command": "workbench.action.toggleFullScreen"
    },
    {
      "key": "f8",
      "command": "workbench.view.connections"
    },
    {
      "key": "ctrl+m",
      "command": "runCurrentQueryWithActualPlanKeyboardAction"
    }
  ]
}
```

## <a name="test-your-extension"></a>Tester votre extension

Vérifiez `azuredatastudio` se trouve dans votre chemin d’accès en exécutant la commande d’installation azuredatastudio dans la commande de chemin d’accès dans Azure Data Studio.

Vérifiez que l’extension de débogage de Studio de données Azure est installée dans Visual Studio Code.

Sélectionnez **F5** pour lancer Azure Data Studio en mode débogage avec l’extension en cours d’exécution :

![installer l’extension](./media/tutorial-create-extension/install-extension.png)

![extension du test](./media/tutorial-create-extension/test-extension.png)

Keymaps étant une des extensions plus rapides pour créer, votre nouvelle extension doit maintenant être correctement actif et prêt à partager.

## <a name="package-your-extension"></a>Votre extension de package

Pour partager avec d’autres utilisateurs, vous devez empaqueter l’extension dans un seul fichier. Cela peut être publié à la place de marché Azure Data Studio extension ou simplement partagé entre votre équipe ou de la Communauté. Pour ce faire, vous devez installer un autre package npm à partir de la ligne de commande :

`npm install -g vsce`

Accédez au répertoire de base de l’extension et exécutez `vsce package`. J’ai dû ajouter deux lignes supplémentaires pour arrêter la *vsce* outil à partir de plaindre :

```json
"repository": {
    "type": "git",
    "url": "https://github.com/kevcunnane/ssmskeymap.git"
},
"bugs": {
    "url": "https://github.com/kevcunnane/ssmskeymap/issues"
},
```

Une fois que cela a été fait, mon fichier ssmskeymap-0.1.0.vsix a été créé et prêt à installer et partager avec tout le monde !

![installer l’extension](./media/tutorial-create-extension/extensions.png)


## <a name="publish-your-extension-to-the-marketplace"></a>Publier votre extension à la place de marché

La place de marché Azure Data Studio extension n’est pas totalement encore implémentée, mais le processus en cours est d’héberger l’extension VSIX quelque part (par exemple, une page de version de GitHub) puis soumettre une demande de tirage mise à jour [ce fichier JSON](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json) avec votre informations sur l’extension.


## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment :
> [!div class="checklist"]
> * Créez un projet d’extension
> * Installer le Générateur d’extension
> * Créer votre extension
> * Tester votre extension
> * Votre extension de package
> * Publier votre extension à la place de marché


Nous espérons qu’après avoir lu cette que vous serez inspiré pour créer votre propre extension pour Azure Data Studio. Nous prenons en charge du tableau de bord Insights (graphiques convivial qui s’exécutent sur votre serveur SQL Server), un nombre d’API spécifiques à SQL et un ensemble existant énorme de points d’extension héritées à partir de Visual Studio Code.

Si vous avez une idée mais que vous ne savez pas comment commencer, ouvrez un problème ou un tweet à l’équipe : [azuredatastudio](https://twitter.com/azuredatastudio).

Vous pouvez toujours consulter la [guide de l’extension Visual Studio Code](https://code.visualstudio.com/docs/extensions/overview) , car elle couvre toutes les API existantes et les modèles.


Pour apprendre à travailler avec T-SQL dans Azure Data Studio, suivez le didacticiel de l’éditeur T-SQL :

> [!div class="nextstepaction"]
> [Utiliser l’éditeur Transact-SQL pour créer des objets de base de données](tutorial-sql-editor.md).
