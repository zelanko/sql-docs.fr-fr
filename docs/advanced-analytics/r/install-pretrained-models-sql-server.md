---
title: "Installer des modèles d’apprentissage automatique préformé sur SQL Server | Documents Microsoft"
ms.date: 11/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 46f8039a6c3ec6f592d2516463f802bda81249f1
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="install-pretrained-machine-learning-models-on-sql-server"></a>Installer préformé d’apprentissage des modèles sur SQL Server

Cet article décrit comment ajouter modèles préformés à une instance de SQL Server qui a déjà des Services de R ou Machine Learning Services est installé.

L’option d’installation des modèles préformés est disponible lorsque vous utilisez le programme d’installation Windows distinct pour Microsoft R Server ou serveur de Machine Learning. Vous pouvez utiliser ce programme d’installation pour obtenir uniquement les modèles préformés, ou vous pouvez l’utiliser pour [mettre à niveau les composants d’apprentissage automatique](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md) dans une instance de SQL Server 2016 ou SQL Server 2017.

Une fois que vous avez téléchargé les modèles préformés en exécutant le programme d’installation, il existe quelques étapes supplémentaires pour configurer les modèles pour une utilisation avec SQL Server. Cet article décrit le processus.

Pour obtenir un exemple montrant comment utiliser les modèles préformés avec des données SQL Server, consultez le blog par l’équipe SQL Server Machine Learning : 

+ [Analyse des sentiments avec Python dans Machine Learning Services SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/)

## <a name="benefits-of-using-pretrained-models"></a>Avantages de l’utilisation de modèles préformés

Ces modèles dont l’apprentissage ont été créés pour aider les clients qui ont besoin effectuer des tâches telles que la personnalisation de la sentiment analysis ou image, mais qui n’ont pas les ressources pour obtenir des jeux de données volumineux ou de former un modèle complex. À l’aide de modèles dont l’apprentissage vous permet de commencer à utiliser text et image traiter efficacement.

Actuellement, les modèles qui sont disponibles sont des modèles de réseau neuronaux en profondeur (profonds DNN) pour la classification du sentiment analysis et image. Tous les modèles préformés ont été formés à l’aide de Microsoft [boîte à outils de calcul réseau](https://cntk.ai/Features/Index.html), ou **CNTK**.

La configuration de chaque réseau était basée sur les implémentations de référence suivantes :

+ ResNet-18
+ ResNet à 50.
+ ResNet-101
+ AlexNet

Pour plus d’informations sur ces modèles, consultez [préentraîné apprentissage des modèles pour la détection de sentiment analysis et image](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)

Pour plus d’informations sur les réseaux de formation approfondie et leur implémentation à l’aide de CNTK, consultez les articles suivants :

+ [Algorithme d’aux chercheurs Microsoft définit ImageNet défi jalon](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft le Kit de ressources de calcul réseau offre la plus efficace deep distribuée apprentissage des performances de calcul](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="how-to-install-the-models-on-sql-server"></a>Comment installer les modèles sur SQL Server

1. Exécutez distinct basés sur Windows installer pour l’apprentissage d’ordinateur serveur. Pour les emplacements de téléchargement, consultez :

    + [Installer le serveur d’apprentissage pour Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
    + [Installer R Server 9.1 pour Windows](https://docs.microsoft.com/r-server/install/r-server-install-windows)

2. La sélection des fonctionnalités à installer dépend de si vous simplement les modèles de mise en route, ou effectuer d’autres mises à jour à l’aide du programme d’installation.
 
    + S’il s’agit d’une nouvelle installation du serveur de Machine Learning, et vous ne souhaitez pas apporter d’autres modifications aux composants R ou Python, sélectionnez **uniquement** l’option préformé modèles. Acceptez toutes les invites, y compris les contrats de licence.

    + Pour mettre à niveau les composants de R ou Python en même temps, sélectionnez la langue (R, Python ou les deux) que vous souhaitez mettre à jour et sélectionnez l’option préformé modèles. Sélectionnez une ou plusieurs instances pour appliquer ces modifications.

    + Si vous avez précédemment installé le serveur Machine Learning et mis à jour des composants de R ou Python à l’aide de l’option de liaison, laissez toutes les sélections précédentes **étant**, puis sélectionnez les options de modèles préformé. Ne désélectionnez pas les options précédemment sélectionnées ; Si vous procédez ainsi, le programme d’installation supprime les composants.

3. Lors de l’installation est terminée, ouvrez une invite de commandes Windows **en tant qu’administrateur**et accédez au dossier d’installation d’amorçage pour SQL Server, lequel contient également le programme d’installation de Microsoft R. Dans une instance par défaut de SQL Server 2017, le dossier serait :
    
    `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\SQL2017\x64\`

4. Exécutez RSetup.exe et indiquer le composant à installer, la version et le dossier contenant les fichiers de source de modèle, en utilisant les arguments de ligne de commande indiqués dans les exemples suivants :

    + À utiliser avec les modèles **R_SERVICES**:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<SQL_DB_instance_folder>\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    Par exemple, pour activer l’utilisation de la version la plus récente des modèles préformés pour R, dans une instance par défaut de SQL Server 2017, vous exécuteriez cette instruction :

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    Sur une instance nommée, la commande serait quelque chose comme ceci :

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + Pour utiliser des modèles préformés avec R Server (autonome) ou Machine Learning Server (autonome) :

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "~\R_SERVER\library\MicrosoftML\mxLibs\x64"`

    Par exemple, pour activer l’utilisation de la version la plus récente des modèles préformés pour R, dans une installation par défaut du serveur R avec SQL Server 2016, vous exécuteriez cette instruction :

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir ‘C:\Program Files\Microsoft SQL Server\130\R_SERVER\library\MicrosoftML\mxLibs\"`
    
    + Utiliser des modèles préformés avec **PYTHON_SERVICES**:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<SQL_DB_instance_folder>\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    Par exemple, pour activer l’utilisation de la version la plus récente des modèles préformés pour Python, dans une instance par défaut de SQL Server 2017, vous exécuteriez cette instruction :

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    Sur une instance nommée, la commande serait quelque chose comme ceci :

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + Pour utiliser Python pretrained modèles avec Machine Learning Server (autonome) :

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<sql_folder>\PYTHON_SERVER\site-packages\microsoftml\mxLibs"`

    Par exemple, en supposant que d’une installation par défaut de la Machine Learning Server (autonome) à l’aide du programme d’installation de SQL Server 2017, exécutez cette instruction :

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER\Lib\site-packages\microsoftml\mxLibs"`

5. Les valeurs suivantes sont prises en charge pour le paramètre de version :

    + Version release candidate 0 : **9.1.0.0**
    + Version release candidate 1 : **9.2.0.22**
    + RTM : **9.2.0.100**
    + Mise à jour cumulative 1 : **9.2.0.24**

6. Si l’installation est réussie, les modèles suivants doivent être ajoutés à votre R\_SERVICES ou PYTHON\_dossiers SERVICES :

    - AlexNet\_Updated.model
    - ImageNet1K\_mean.xml
    - pretrained.Model
    - ResNet\_101\_Updated.model
    - ResNet\_18\_Updated.model
    - ResNet\_50\_Updated.model


> [!NOTE]
> 
> Si le chemin d’accès au fichier de modèle est trop long, vous pouvez obtenir une erreur lorsque vous appelez le fichier de modèle à partir de code Python. Il s’agit d’une limitation de l’implémentation actuelle de Python. Ce problème sera résolu dans une version de service à venir.

## <a name="examples"></a>Exemples

Après avoir installé les modèles, vous pouvez utiliser les modèles en les appelant à partir de votre code.

### <a name="image-featurization-example"></a>Exemple de personnalisation de la l’image

Le modèle préformé pour les images prend en charge la personnalisation des images que vous fournissez. Ce modèle spécifique a été formé à l’aide de [CNTK](https://docs.microsoft.com/cognitive-toolkit/). 

Pour utiliser le modèle, vous appelez le **featurizeImage** transformer.

+ [featurizeImage : transformer de personnalisation de la Machine Learning Image](https://docs.microsoft.com/r-server/r-reference/microsoftml/featurizeimage)

Dans cet exemple, consultez le deuxième bloc de code. L’image est chargée, redimensionnée et les fonctionnalités par le modèle de profonds DNN préformé à convolution. La sortie du Générateur de fonctionnalités profonds DNN est ensuite utilisée pour former un modèle linéaire pour la classification d’image.

L’image doit être redimensionnée pour satisfaire les exigences du modèle formé : les images utilisées pour l’apprentissage ont été 224 x 224 px. Si vous utilisez un modèle AlexNet, l’image devait être modifiée et 227 x 227 px.

```R
 model <- rxFastLinear(
     Label ~ Features,
     data = train,
     mlTransforms = list(
         loadImage(vars = list(Features = "Path")),
         resizeImage(vars = "Features", width = 224, height = 224), 
         extractPixels(vars = "Features"),
         featurizeImage(var = "Features")
         ),
     mlTransformVars = "Path")
```

> [!NOTE]
> Il n’est pas possible de lire ou modifier les modèles préformés, car elles sont compressées à l’aide d’un format natif pour améliorer les performances.

### <a name="text-analysis-example"></a>Exemple d’analyse de texte

Consultez l’exemple suivant pour une démonstration de l’utilisation du modèle de personnalisation de la texte préformé pour la classification de texte :

[Analyse des sentiments à l’aide du Générateur de fonctionnalités de texte](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)
