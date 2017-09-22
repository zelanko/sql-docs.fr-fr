---
title: "Installer des modèles d’apprentissage automatique préformé sur SQL Server | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: b52fcc1e4ac77df2968a4ea6cbd6e546ff1b74ac
ms.contentlocale: fr-fr
ms.lasthandoff: 09/19/2017

---
# <a name="install-pretrained-machine-learning-models-on-sql-server"></a>Installer préformé d’apprentissage des modèles sur SQL Server

Cette rubrique décrit comment ajouter modèles préformés à une instance de SQL Server qui a déjà des Services de R ou Machine Learning Services est installé.

Modèles préformés sont fournies avec la mise à jour pour Microsoft R Server (ou la mise à jour Microsoft Machine Learning Server). Pour plus d’informations sur la façon de mettre à niveau votre instance et obtenir la dernière version de Microsoft R, consultez [mettre à niveau les composants de R dans une instance de R Services](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

Vous pouvez installer ces modèles uniquement en exécutant le basé sur Windows programme d’installation distinct pour R Server.
Toutefois, il existe quelques étapes supplémentaires à utiliser lors de l’installation des modèles sur SQL Server. Cette rubrique décrit le processus.

## <a name="benefits-of-using-pretrained-models"></a>Avantages de l’utilisation de modèles préformés

Dont l’apprentissage des modèles ont été apportées pour prendre en charge des clients ayant besoin d’effectuer des tâches, telles que l’analyse des sentiments ou la personnalisation de l’image, mais n’ont pas les ressources pour obtenir des jeux de données volumineux ou de former un modèle complex disponibles. À l’aide de modèles dont l’apprentissage vous permet de commencer à utiliser text et image de traitement plus efficace.

Actuellement, les modèles qui sont disponibles sont des modèles de réseau neuronaux en profondeur (profonds DNN) pour la classification du sentiment analysis et image. Les quatre modèles préformés ont été formés sur CNTK. La configuration de chaque réseau était basée sur les implémentations de référence suivantes :

+ ResNet-18
+ ResNet à 50.
+ ResNet-101
+ AlexNet

Pour plus d’informations sur les réseaux profondeur résiduelles et leur implémentation à l’aide de CNTK, consultez les articles suivants :

+ [Algorithme d’aux chercheurs Microsoft définit ImageNet défi jalon](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft le Kit de ressources de calcul réseau offre la plus efficace deep distribuée apprentissage des performances de calcul](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="how-to-install-the-models-on-sql-server"></a>Comment installer les modèles sur SQL Server

   > [!NOTE]
   > 
   > Si vous utilisez le programme d’installation distinct basés sur Windows Installer Microsoft R Server ou mettre à niveau votre instance de SQL Server, les modèles préformés sont disponibles dans le programme d’installation. Consultez [installer R Server pour Windows](https://docs.microsoft.com/en-us/r-server/install/r-server-install-windows).
   > 
   > Certaines étapes supplémentaires peuvent être requises pour utiliser les modèles avec Microsoft R Server. Pour plus d’informations, consultez [comment installer et déployer apprentissage des modèles d’apprentissage automatique avec MicrosoftML](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models)

1. Les modèles préformés ne sont pas installés par défaut lorsque vous installez SQL Server ; Vous devez les ajouter à un utilitaire de ligne de commande d’installation en cours d’exécution après l’installation de SQL Server.

2. Ouvrez une invite de commandes avec élévation de privilèges et accédez au dossier d’installation d’amorçage pour SQL Server, lequel contient également le programme d’installation de Microsoft R.

    Dans une instance par défaut de SQL Server 2017 RC 1, il s’agit de la configuration :
    
    `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\SQL2017RC1\x64\`

3. Spécifiez le composant à installer et le dossier où les modèles préformés doivent être ajoutés à l’aide des arguments suivants :

  + À utiliser avec les modèles **R_SERVICES**

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir <SQL_DB_instance_folder>\R_SERVICES`

    Par exemple, pour permettre l’utilisation des modèles préformés à l’aide de R dans une instance par défaut de SQL Server 2017, vous exécuteriez cette instruction :

    `RSetup.exe /install /component MLM /version 9.2.0.22 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES"`

  + À utiliser avec les modèles **PYTHON_SERVICES**

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir <SQL_DB_instance_folder>\PYTHON_SERVICES`

    Par exemple, pour activer l’utilisation des modèles préformés à l’aide de Python, une instance par défaut de SQL Server 2017, vous exécuteriez cette instruction :

    `RSetup.exe /install /component MLM /version 9.2.0.22 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES"`

4. Le paramètre de version, les valeurs suivantes sont prises en charge :

    + Version release candidate 0 : **9.1.0.0**
    + Version release candidate 1 : **9.2.0.22**
    + Numéro de version finale (non publiée) : **9.2.0.100**

5. Si l’installation est réussie, les modèles suivants doivent être ajoutés à votre R\_SERVICES ou PYTHON\_dossiers SERVICES :

    - AlexNet_Updated.model
    - ImageNet1K_mean.xml
    - pretrained.Model
    - ResNet_101_Updated.model
    - ResNet_18_Updated.model
    - ResNet_50_Updated.model

## <a name="examples"></a>Exemples

Après avoir installé les modèles, vous pouvez utiliser les modèles en les appelant à partir du code R.

### <a name="image-featurization-example"></a>Exemple de personnalisation de la l’image

Le modèle préformé pour les images prend en charge la personnalisation des images que vous fournissez. Pour utiliser le modèle, vous appelez le **featurizeImage** transformer.

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
> 
> Il n’est pas possible de lire ou modifier le modèle préformé lui-même. Ce modèle particulier est basé sur [CNTK](https://docs.microsoft.com/cognitive-toolkit/) de modèle, mais a été compressée à l’aide d’un format natif pour des raisons de performances.

### <a name="text-analysis-example"></a>Exemple d’analyse de texte

Cet exemple illustre l’utilisation du modèle préformé pour la classification :

[Analyse des sentiments à l’aide du Générateur de fonctionnalités de texte](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

