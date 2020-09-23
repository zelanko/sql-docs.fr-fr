---
title: Créer une extension de tableau de bord
description: Ce tutoriel montre comment créer une extension de tableau de bord pour ajouter des fonctionnalités personnalisées à Azure Data Studio.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: yualan
ms.author: alayu
ms.reviewer: alayu, maghan
ms.custom: ''
ms.date: 08/28/2020
ms.openlocfilehash: 835b1fd4687dc5fd86afe300d7c6ed56dc2ed6ea
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91111641"
---
# <a name="create-an-azure-data-studio-dashboard-extension"></a>Créer une extension de tableau de bord Azure Data Studio

Ce tutoriel montre comment créer une **extension de tableau de bord Azure Data Studio**. L’extension donne un tableau de bord de connexion Azure Data Studio. Vous pouvez donc étendre les fonctionnalités d’Azure Data Studio d’une manière facilement visible pour les utilisateurs.

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> - Installer le générateur d’extensions
> - Créer votre extension
> - Contribuer au tableau de bord dans votre extension
> - Tester votre extension
> - Empaqueter votre extension
> - Publier votre extension sur le marketplace

## <a name="prerequisites"></a>Prérequis

Azure Data Studio repose sur la même infrastructure que Visual Studio Code, ainsi les extensions pour Azure Data Studio sont générées à l’aide de Visual Studio Code. Pour commencer, vous avez besoin des composants suivants :

- [Node.js](https://nodejs.org) installé et disponible dans votre `$PATH`. Node. js comprend [npm](https://www.npmjs.com/), le gestionnaire de packages Node.js, qui est utilisé pour installer le générateur d’extensions.
- [Visual Studio Code](https://code.visualstudio.com) pour déboguer l’extension.
- [L’extension de débogage](https://marketplace.visualstudio.com/items?itemName=ms-mssql.sqlops-debug) d’Azure Data Studio (facultatif). Cela vous permet de tester votre extension sans avoir à l’empaqueter et l’installer dans Azure Data Studio.
- Vérifiez que `azuredatastudio` se trouve dans votre chemin d’accès. Pour Windows, veillez à choisir l'option `Add to Path` dans setup.exe. Pour Mac ou Linux, exécutez l’option *Installer la commande 'azuredatastudio' dans CHEMIN D’ACCÈS*.

## <a name="install-the-extension-generator"></a>Installer le générateur d’extensions

Pour simplifier le processus de création d’extensions, nous avons créé un [générateur d’extensions](https://code.visualstudio.com/docs/extensions/yocode) à l’aide de Yeoman. Pour l’installer, exécutez la commande suivante à partir de l’invite de commandes :

```console
`npm install -g yo generator-azuredatastudio`
```

## <a name="create-your-dashboard-extension"></a>Créer votre extension de tableau de bord

### <a name="introduction-to-the-dashboard"></a>Présentation du tableau de bord

Le tableau de bord de connexion Azure Data Studio est un outil puissant qui récapitule et donne des informations sur les connexions d’un utilisateur.

Il existe deux variantes du tableau de bord : le « tableau de bord du serveur » qui récapitule l’ensemble du serveur et le « tableau de bord de la base de données » qui récapitule une base de données individuelle. Pour y accéder, vous pouvez cliquer avec le bouton droit sur un serveur ou une base de données dans le viewlet Connexions d’Azure Data Studio, puis cliquer sur **Gérer** :

:::image type="content" source="media/dashboard-extension/dashboard-summary.gif" alt-text="Présentation des tableaux de bord":::

Il existe 3 points de contribution clés pour les extensions permettant d’ajouter des fonctionnalités au tableau de bord :

1. **Onglet du tableau de bord complet** : Onglet distinct dans le tableau de bord pour votre extension. Peut être ajouté à un tableau de bord de serveur ou de base de données. Personnalisable avec des widgets, une barre d’outils et une section de navigation.
2. **Actions de la page d’accueil** : Boutons d’action situés en haut de la barre d’outils de connexion.
3. **Widgets** : Graphiques qui s’exécutent sur votre serveur SQL Server.

:::image type="content" source="media/dashboard-extension/dashboard-contrib-points.png" alt-text="Points de contribution":::

### <a name="run-the-extension-generator"></a>Exécuter le générateur d’extensions

Pour créer une extension :

1. Lancez le générateur d’extensions avec la commande suivante :

   `yo azuredatastudio`

2. Choisissez **Nouveau tableau de bord** dans la liste des types d’extension.

3. Renseignez les invites comme indiqué ci-dessous. Une extension qui fournit un onglet au tableau de bord du serveur est ainsi créée.

:::image type="content" source="media/dashboard-extension/dashboard-generator.png" alt-text="Générateur d’extensions":::

Le nombre d’invites étant élevé, voici un peu plus d’informations sur ce que signifie chaque question :

:::image type="content" source="media/dashboard-extension/dashboard-flowchart.png" alt-text="Organigramme des tableaux de bord":::

L’exécution des étapes précédentes crée un dossier. Ouvrez le dossier dans Visual Studio Code et vous êtes prêt à créer votre propre extension de tableau de bord !

### <a name="run-the-extension"></a>Exécuter l’extension

Voyons ce que nous obtenons avec le modèle de tableau de bord en exécutant l’extension. Avant l’exécution, vérifiez que l’**extension de débogage Azure Data Studio** est installée dans Visual Studio Code.

Appuyez sur **F5** dans VS Code pour lancer Azure Data Studio en mode débogage avec l’extension en cours d’exécution. Ensuite, vous pouvez voir comment ce modèle par défaut contribue au tableau de bord.

Nous allons ensuite voir comment modifier ce tableau de bord par défaut.

### <a name="develop-the-dashboard"></a>Développer le tableau de bord

Le fichier le plus important pour bien démarrer avec le développement d’extensions est `package.json`. Il s’agit du fichier manifeste, dans lequel les contributions du tableau de bord sont inscrites. Remarquez les sections `dashboard.tabs`, `dashboard.insights` et `dashboard.containers`.

Voici quelques modifications à essayer :

- Expérimentez les d’insights, notamment « bar », « horizontalBar », « timeSeries ».
- Écrivez vos propres requêtes pour les exécuter sur votre connexion SQL Server.
- Reportez-vous à ce [tutoriel](../tutorial-qds-sql-server.md) ou à [celui-ci](../tutorial-table-space-sql-server.md) pour découvrir des tutoriels sur des insights spécifiques.

## <a name="package-your-extension"></a>Empaqueter votre extension

Pour partager votre extension avec d’autres personnes, vous devez l’empaqueter dans un fichier unique. Il peut être publié sur le marketplace d’extensions Azure Data Studio ou partagé avec votre équipe ou votre communauté. Pour ce faire, vous devez installer un autre package npm à partir de la ligne de commande :

```console
`npm install -g vsce`
```

Modifiez le fichier `README.md` à votre gré, puis accédez au répertoire de base de l’extension et exécutez `vsce package`. Vous pouvez éventuellement lier un référentiel à votre extension ou continuer sans référentiel. Pour en ajouter un, ajoutez une ligne similaire à votre fichier `package.json`.

```json
"repository": {
    "type": "git",
    "url": "https://github.com/anjalia/my-test-extension.git"
}
```

Une fois ces lignes ajoutées, un fichier my-test-extension-0.0.1.vsix est créé et prêt à être installé dans Azure Data Studio.

:::image type="content" source="media/dashboard-extension/install-vsix.png" alt-text="Installer vsix":::

## <a name="publish-your-extension-to-the-marketplace"></a>Publier votre extension sur le marketplace

Le marketplace d’extensions Azure Data Studio n’est pas encore totalement implémenté, mais le processus actuel consiste à héberger l’extension VSIX quelque part (par exemple une page de publication GitHub), puis à envoyer une demande de tirage mettant à jour [ce fichier JSON](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json) avec vos informations sur l’extension.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
> - Installer le générateur d’extensions
> - Créer votre extension
> - Contribuer au tableau de bord dans votre extension
> - Tester votre extension
> - Empaqueter votre extension
> - Publier votre extension sur le marketplace

Nous espérons qu’après avoir lu cela, vous serez inspiré pour créer votre propre extension pour Azure Data Studio. Nous prenons en charge les insights de tableau de bord (de jolis graphiques qui s’exécutent sur SQL Server), un certain nombre d’API spécifiques à SQL et un ensemble de points d’extension existants hérités de Visual Studio Code.

Si vous avez une idée mais que vous ne savez pas par où commencer, veuillez ouvrir un problème ou envoyer un tweet à l’équipe [azuredatastudio](https://twitter.com/azuredatastudio).

Vous pouvez toujours vous reporter au [guide pour les extensions Visual Studio Code](https://code.visualstudio.com/docs/extensions/overview), car il couvre toutes les API et tous les modèles existants.

Pour savoir comment utiliser T-SQL dans Azure Data Studio, suivez le didacticiel de l’éditeur T-SQL :

> [!div class="nextstepaction"]
> [Utiliser l’éditeur Transact-SQL pour créer des objets de base de données](../tutorial-sql-editor.md).
