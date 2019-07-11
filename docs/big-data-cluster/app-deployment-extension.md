---
title: Extension de déploiement d’application
titleSuffix: SQL Server big data clusters
description: Déployer un script Python ou R en tant qu’application sur un cluster de données volumineux de SQL Server 2019 (version préliminaire).
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
manager: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ba56ebb90d09866b7860c5f29dd2a26cf525fd9b
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729305"
---
# <a name="how-to-use-vs-code-to-deploy-applications-to-sql-server-big-data-clusters"></a>Comment utiliser VS Code pour déployer des applications sur les clusters de données volumineuses de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit comment déployer des applications sur un cluster de données volumineuses de SQL Server à l’aide de Visual Studio Code avec l’extension de déploiement de l’application. Cette fonctionnalité a été introduite dans CTP 2.3. 

## <a name="prerequisites"></a>Prérequis

- [Visual Studio Code](https://code.visualstudio.com/).
- [Cluster de données volumineux de SQL Server](big-data-cluster-overview.md) CTP 2.3 ou version ultérieure.

## <a name="capabilities"></a>Fonctionnalités

Cette extension prend en charge les tâches suivantes dans Visual Studio Code :

- S’authentifier avec un cluster de données volumineux de SQL Server.
- Récupérer un modèle d’application à partir du référentiel GitHub pour le déploiement des runtimes pris en charge.
- Gérer les modèles d’application en cours dans l’espace de travail de l’utilisateur.
- Déployer une application via une spécification de format YAML.
- Gérer les applications déployées au sein du cluster de données volumineux de SQL Server.
- Afficher toutes les applications que vous avez déployées dans la barre latérale avec des informations supplémentaires.
- Générer une spécification d’exécution pour utiliser l’application ou de supprimer l’application à partir du cluster.
- Consommer des applications déployées via une spécification d’exécution YAML.

Les sections suivantes prendre le processus d’installation et fournit une vue d’ensemble du fonctionne de l’extension. 

### <a name="install"></a>Installation

Tout d’abord installer l’extension de déploiement d’applications dans VS Code :

1. Télécharger [Extension déployer d’application](https://aka.ms/app-deploy-vscode) pour installer l’extension dans le cadre de Visual Studio Code.

1. Lancez VS Code et accédez au volet Extensions.

1. Cliquez sur le `…` menu contextuel en haut de la barre latérale et sélectionnez `Install from vsix`.

   ![Installer l’extension VSIX](media/vs-extension/install_vsix.png)

1. Rechercher le `sqlservbdc-app-deploy.vsix` fichier téléchargé et choisissez qui installer.

Une fois que l’application de cluster de données volumineuses de SQL Server déployé extension a été installée, vous êtes invité à recharger le Code de Visual Studio. Vous devez maintenant voir l’Explorateur d’application SQL Server BDC dans la barre latérale de VS Code.

### <a name="app-explorer"></a>Explorateur de l’application

Cliquez sur l’extension dans la barre latérale pour charger un panneau latéral affichant l’Explorateur de l’application. La capture d’écran exemple suivante de l’Explorateur de l’application n’affiche aucune des applications ou des spécifications d’application disponibles :

<img src="media/vs-extension/app_explorer.png" width=350px></img>
<!--![App Explorer](media/vs-extension/app_explorer.png)-->

#### <a name="new-connection"></a>Nouvelle connexion

Pour vous connecter au point de terminaison de cluster, utilisez une des méthodes suivantes :

- Cliquez sur la barre d’état en bas qui indique que `SQL Server BDC Disconnected`.
- Ou cliquez sur le `New Connection` bouton en haut avec la flèche pointant sur une voie d’accès.

   ![Nouvelle connexion](media/vs-extension/connect_to_cluster.png)

VS Code vous invite à entrer le point de terminaison approprié, le nom d’utilisateur et le mot de passe. Si les informations d’identification correctes et de terminaison d’application donnés, VS Code avertit que vous avez été connecté au cluster et vous verrez les applications déployées renseignées dans la barre latérale. Si vous êtes connecté, votre point de terminaison et le nom d’utilisateur seront enregistrés dans `./sqldbc` dans le cadre de votre profil utilisateur. Aucun mot de passe ou les jetons ne seront jamais enregistrées. Quand vous vous connectez à nouveau, l’invite de remplir au préalable avec votre hôte enregistré et le nom d’utilisateur, mais nécessitent toujours à entrer un mot de passe. Si vous souhaitez vous connecter à un point de terminaison de cluster différent, cliquez sur le `New Connection` à nouveau. La connexion se ferme automatiquement si vous fermez VS Code ou si vous ouvrez un autre espace de travail et vous devrez vous reconnecter.

### <a name="app-template"></a>Modèle d’application

Pour déployer une nouvelle application à partir d’un de nos modèles, cliquez sur le `New App Template` bouton sur le `App Specifications` volet, où vous demandera le nom, le runtime et ce qu’emplacement que vous souhaitez placer la nouvelle application dans sur votre ordinateur local. Il est recommandé que vous placez dans votre espace de travail VS Code actuel afin que vous pouvez utiliser toutes les fonctionnalités de l’extension, mais vous pouvez le placer n’importe où dans votre système de fichiers local.

![Nouveau modèle d’application](media/vs-extension/new_app_template.png)

Une fois terminé, un nouveau modèle d’application est généré automatiquement pour vous à l’emplacement spécifié et le déploiement `spec.yaml` s’ouvre dans votre espace de travail. Si le répertoire que vous avez sélectionné est dans votre espace de travail, vous devez également voir il apparaît sous le `App Specifications` volet :

![Modèle d’application chargé](media/vs-extension/loading_app_template.png)

Le modèle est une simple `Hello World` application est disposée comme suit :

- **spec.yaml**
   - Indique le cluster comment déployer votre application
- **run-spec.yaml**
   - Indique le cluster Comment voulez-vous appeler votre application
- **handler.py**
   - Il s’agit votre fichier de code source tel que spécifié par `src` dans `spec.yaml`
   - Il a une fonction appelée `handler` qui est considéré comme le `entrypoint` de l’application, comme indiqué dans `spec.yaml`. Il prend une entrée de chaîne appelée `msg` et retourne une sortie de chaîne appelée `out`. Elles sont spécifiées dans `inputs` et `outputs` de la `spec.yaml`.

Si vous ne souhaitez pas un modèle généré automatiquement et que vous préférez simplement un `spec.yaml` pour le déploiement d’une application que vous avez déjà créé, cliquez sur le `New Deploy Spec` situé en regard du `New App Template` bouton et passer à travers le même processus, mais vous recevrez simplement le `spec.yaml`, que vous pouvez modifier la façon dont vous choisissez.

### <a name="deploy-app"></a>Déploiement d’une application

Vous pouvez déployer instantanément de cette application à travers l’objectif du code `Deploy App` dans le `spec.yaml` ou appuyez sur le bouton de dossier éclair à côté du `spec.yaml` fichier dans le menu de spécifications de l’application. L’extension sera compresser tous les fichiers dans le répertoire où votre `spec.yaml` se trouve et déployer votre application dans le cluster. 

>[!NOTE]
>Vérifiez que tous vos fichiers d’application sont dans le même répertoire que votre `spec.yaml`. Le `spec.yaml` doit être au niveau racine de votre répertoire de code d’application source. 

![Déployer le bouton de l’application](media/vs-extension/deploy_app_lightning.png)

![Déployer l’application CodeLens](media/vs-extension/deploy_app_codelens.png)

Vous serez averti lorsque l’application est prête pour la consommation en fonction de l’état de l’application dans la barre latérale :

![Application déployée](media/vs-extension/app_deploy.png)

![Barre latérale de prêt application](media/vs-extension/app_ready_side_bar.png)

![Notification de prêt de l’application](media/vs-extension/app_ready_notification.png)

Dans le volet, vous serez en mesure de voir les opérations suivantes disponibles pour vous :

Vous pouvez afficher toutes les applications que vous avez déployé dans la barre latérale avec les informations suivantes :

- state
- version
- paramètres d'entrée
- Paramètres de sortie
- liens
  - swagger
  - détails

Si vous cliquez sur `Links`, vous verrez que vous pouvez accéder à la `swagger.json` de votre application déployée, afin que vous puissiez écrire vos propres clients qui appellent votre application :

![swagger](media/vs-extension/swagger.png)

Consultez [consommer des applications sur des clusters de données volumineuses](big-data-cluster-consume-apps.md) pour plus d’informations.

### <a name="app-run"></a>Exécution de l’application

Une fois que l’application est prête, appelez l’application avec le `run-spec.yaml` qui a été attribuée comme partie du modèle d’application :

![Exécuter des spécifications](media/vs-extension/run_spec.png)

Spécifiez toute chaîne que vous souhaitez à la place de `hello` et exécutez à nouveau via le lien de lentilles de code ou le bouton d’éclair dans la barre latérale à côté du `run-spec.yaml`. Si vous n’avez pas une spécification de l’exécution pour une raison quelconque, générer un à partir de l’application déployée dans le cluster :

![Obtenir les spécifications d’exécution](media/vs-extension/get_run_spec.png)

Une fois que vous en avez pas et que vous l’avez modifié à votre convenance, exécutez-le. VS Code retourne les commentaires appropriés lors de l’exécution de l’application est terminée :

![Sortie de l’application](media/vs-extension/app_output.png)

Comme vous pouvez le voir ci-dessus, la sortie est fournie dans une table temporaire `.json` fichier dans votre espace de travail. Si vous souhaitez conserver cette sortie, n’hésitez pas à l’enregistrer, dans le cas contraire, il sera supprimé de clôture. Si votre application ne comporte aucune sortie pour imprimer dans un fichier, vous n’obtiendrez le `Successful App Run` notification en bas. Si vous n’avez pas d’une exécution réussie, vous recevrez un message d’erreur qui vous aideront à déterminer quel est le problème.

Lorsque vous exécutez une application, il existe plusieurs façons pour passer des paramètres :

Vous pouvez spécifier toutes les entrées requises via un `.json`, qui est :

- `inputs: ./example.json`

Lors de l’appel d’une application déployée, si tous les paramètres d’entrée sont innées vers l’application ou d’un utilisateur spécifié et que donné le paramètre d’entrée n’est pas une primitive, comme un tableau, le vecteur, la trame de données, spécifiez un JSON complexe, etc. le type de paramètre directement en ligne lorsque appel de l’application, autrement dit :

- vecteur
    - `inputs:`
        - `x: [1, 2, 3]`
- Matrix
    - `inputs:`
        - `x: [[A,B,C],[1,2,3]]`
- Object
    - `inputs:`
        - `x: {A: 1, B: 2, C: 3}`

Ou donner une chaîne sous la forme d’un chemin d’accès de fichier relatif ou absolu à un `.txt`, `.json`, ou `.csv` qui donne l’entrée nécessaire dans le format que votre application a besoin. L’analyse de fichier est basé sur `Node.js Path library`, où un chemin d’accès de fichier est défini comme un `string that contains a / or \ character`.

Si le paramètre d’entrée n’est pas fourni en fonction des besoins, un message d’erreur approprié s’affichera avec le chemin d’accès fichier incorrect si un chemin d’accès du fichier de chaîne a été spécifié ou si ce paramètre n’est pas valide. La responsabilité est donnée le créateur de l’application pour vous assurer qu’ils comprennent les paramètres qu’ils définissent.

Pour supprimer une application, cliquez simplement sur la Corbeille peut bouton en regard de l’application dans le `Deployed Apps` volet latéral.

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment intégrer des applications déployées sur SQL Server clusters de données volumineuses dans vos propres applications à [consommer des applications sur des clusters de données volumineuses](big-data-cluster-consume-apps.md) pour plus d’informations. Vous pouvez également faire référence aux exemples supplémentaires au [exemples de déploiement d’applications](https://aka.ms/sql-app-deploy) à essayer avec l’extension.

Pour plus d’informations sur les clusters de données volumineuses de SQL Server, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).


Notre objectif est de rendre cette extension utile pour vous et nous nous vous remercions des commentaires. Merci de les envoyer à [ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] team](https://aka.ms/sqlfeedback).
