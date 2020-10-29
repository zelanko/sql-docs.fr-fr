---
title: Installer des modèles pré-entraînés
description: Ajoutez des modèles préformés pour l’analyse des sentiments et la génération de fonctionnalités d’images à SQL Server Machine Learning Services (R ou Python) ou SQL Server R Services.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 07/30/2019
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6407ed2cd23b8fad1f63a1b670a4cce2ad54790c
ms.sourcegitcommit: ef20f39a17fd4395dd2dd37b8dd91b57328a751c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92793746"
---
# <a name="install-pre-trained-machine-learning-models-on-sql-server"></a>Installer des modèles Machine Learning préformés sur SQL Server
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Cet article explique comment utiliser PowerShell pour ajouter des modèles Machine Learning préentraînés gratuits pour l’ *analyse des sentiments* et la *génération de fonctionnalités d’images* à une instance SQL Server avec l’intégration R ou Python. Les modèles préformés sont générés par Microsoft et prêts à être utilisés. Ils sont d’ailleurs ajoutés à une instance suite à l’installation. Pour plus d’informations sur ces modèles, consultez la section [Ressources](#bkmk_resources) de cet article.

Une fois installés, les modèles préformés sont considérés comme des détails d’implémentation qui alimentent des fonctions spécifiques dans les bibliothèques MicrosoftML (R) et microsoftml (Python). Vous ne devez pas (et ne pouvez pas) afficher, personnaliser ou reformer les modèles. Vous ne pouvez pas non plus les traiter en tant que ressource indépendante dans du code personnalisé ou dans d’autres fonctions couplées. 

Pour utiliser les modèles préformés, appelez les fonctions indiquées dans le tableau suivant.

| Fonction R (MicrosoftML) | Fonction Python (MicrosoftML) | Usage |
|--------------------------|-------------------------------|-------|
| [getSentiment](/machine-learning-server/r-reference/microsoftml/getsentiment) | [get_sentiment](/machine-learning-server/python-reference/microsoftml/get-sentiment) | Génère un score de sentiment positif-négatif sur les entrées de texte. |
| [featurizeImage](/machine-learning-server/r-reference/microsoftml/featurizeimage) | [featurize_image](/machine-learning-server/python-reference/microsoftml/featurize-image) | Extrait des informations de texte à partir des entrées du fichier image. |

## <a name="prerequisites"></a>Prérequis

Les algorithmes d’apprentissage automatique nécessitent beaucoup de ressources de calcul. Nous vous recommandons 16 Go de RAM pour les charges de travail de taille petite à modérée, y compris l’exécution des procédures pas à pas du didacticiel à l’aide de tous les exemples de données.

Vous devez disposer de droits d’administrateur sur l’ordinateur et SQL Server pour ajouter des modèles préformés.

Les scripts externes doivent être activés, et le service SQL Server LaunchPad doit être en cours d’exécution. Les instructions d’installation fournissent les étapes nécessaires à l’activation et à la vérification de ces fonctionnalités. 

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Le [package MicrosoftML R](/machine-learning-server/r-reference/microsoftml/microsoftml-package) ou le [package MicrosoftML Python](/machine-learning-server/python-reference/microsoftml/microsoftml-package) contiennent les modèles préformés.

[SQL Server Machine Learning Services](sql-machine-learning-services-windows-install.md) contient les deux versions de langage de la bibliothèque Machine Learning ; cette condition préalable est donc remplie sans aucune autre action de votre part. Étant donné que les bibliothèques sont présentes, vous pouvez utiliser le script PowerShell décrit dans cet article pour ajouter les modèles préformés à ces bibliothèques.
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Le [package MicrosoftML R](/machine-learning-server/r-reference/microsoftml/microsoftml-package) contient les modèles préformés.

[SQL Server R Services](sql-r-services-windows-install.md), qui est R uniquement, n’inclut pas le [package MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) prêt à l’emploi. Pour ajouter MicrosoftML, vous devez effectuer une [mise à niveau du composant](../install/upgrade-r-and-python.md). L’un des avantages de la mise à niveau des composants est que vous pouvez ajouter simultanément les modèles préformés, ce qui rend l’exécution du script PowerShell inutile. Toutefois, si vous avez déjà effectué la mise à niveau, mais que vous avez omis d’ajouter les modèles préformés, vous pouvez exécuter le script PowerShell comme décrit dans cet article. Il fonctionne pour les deux versions de SQL Server. Avant cela, vérifiez que la bibliothèque MicrosoftML existe dans `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`.
::: moniker-end

<a name="file-location"></a>

## <a name="check-whether-pre-trained-models-are-installed"></a>Vérifier si des modèles préformés sont installés

Les chemins d’installation des modèles R et Python sont les suivants :

+ Pour R : `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64`

+ Pour Python : `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs`

Les noms de fichiers de modèles sont répertoriés ci-dessous :

+ AlexNet\_Updated.model
+ ImageNet1K\_mean.xml
+ pretrained.model
+ ResNet\_101\_Updated.model
+ ResNet\_18\_Updated.model
+ ResNet\_50\_Updated.model

Si les modèles sont déjà installés, passez directement à [l’étape de validation](#verify) pour confirmer la disponibilité.

## <a name="download-the-installation-script"></a>Télécharger le script d’installation

Cliquez sur [https://aka.ms/mlm4sql](https://aka.ms/mlm4sql) pour télécharger le fichier **Install-MLModels.ps1** .

## <a name="execute-with-elevated-privileges"></a>Exécuter avec des privilèges élevés

1. Démarrez PowerShell. Dans la barre des tâches, cliquez avec le bouton droit sur l’icône de programme PowerShell, puis sélectionnez **Exécuter en tant qu’administrateur** .
2. Entrez un chemin d’accès complet au fichier de script de script d’installation et incluez le nom de l’instance. En partant du principe que vous utilisez le dossier Téléchargements et une instance par défaut, la commande peut ressembler à ce qui suit :

   ```powershell
   PS C:\WINDOWS\system32> C:\Users\<user-name>\Downloads\Install-MLModels.ps1 MSSQLSERVER
   ```

**Sortie**

Sur une instance par défaut SQL Server Machine Learning Services connectée à Internet avec R et Python, vous devez voir des messages identiques à ce qui suit.

   ```powershell
   MSSQL14.MSSQLSERVER
        Verifying R models [9.2.0.24]
        Downloading R models [C:\Users\<user-name>\AppData\Local\Temp]
        Installing R models [C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\]
        Verifying Python models [9.2.0.24]
        Installing Python models [C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\]
   PS C:\WINDOWS\system32>
   ```

<a name="verify"> </a>

## <a name="verify-installation"></a>Vérifier l'installation

Tout d’abord, recherchez les nouveaux fichiers dans le [dossier mxlibs](#file-location). Ensuite, exécutez le code de démonstration pour confirmer que les modèles sont installés et fonctionnels. 

### <a name="r-verification-steps"></a>Étapes de vérification pour R

1. Démarrez **RGUI. EXE** dans C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64.

2. Collez le script R suivant à l’invite de commandes.

    ```R
    # Create the data
    CustomerReviews <- data.frame(Review = c(
    "I really did not like the taste of it",
    "It was surprisingly quite good!",
    "I will never ever ever go to that place again!!"),
    stringsAsFactors = FALSE)

    # Get the sentiment scores
    sentimentScores <- rxFeaturize(data = CustomerReviews, 
                                    mlTransforms = getSentiment(vars = list(SentimentScore = "Review")))

    # Let's translate the score to something more meaningful
    sentimentScores$PredictedRating <- ifelse(sentimentScores$SentimentScore > 0.6, 
                                            "AWESOMENESS", "BLAH")

    # Let's look at the results
    sentimentScores
    ```

3. Appuyez sur Entrée pour afficher les scores de sentiment. La sortie doit ressembler à ce qui suit :

    ```R
    > sentimentScores
                                            Review SentimentScore
    1           I really did not like the taste of it      0.4617899
    2                 It was surprisingly quite good!      0.9601924
    3 I will never ever ever go to that place again!!      0.3103435
    PredictedRating
    1            BLAH
    2     AWESOMENESS
    3            BLAH
    ```

### <a name="python-verification-steps"></a>Étapes de vérification pour Python

1. Démarrez **Python.exe** dans C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES.

2. Collez le script Python suivant à l’invite de commandes

    ```python
    import numpy
    import pandas
    from microsoftml import rx_logistic_regression, rx_featurize, rx_predict, get_sentiment

    # Create the data
    customer_reviews = pandas.DataFrame(data=dict(review=[
                "I really did not like the taste of it",
                "It was surprisingly quite good!",
                "I will never ever ever go to that place again!!"]))
                
    # Get the sentiment scores
    sentiment_scores = rx_featurize(
        data=customer_reviews,
        ml_transforms=[get_sentiment(cols=dict(scores="review"))])
        
    # Let's translate the score to something more meaningful
    sentiment_scores["eval"] = sentiment_scores.scores.apply(
                lambda score: "AWESOMENESS" if score > 0.6 else "BLAH")
    print(sentiment_scores)
    ```

3. Appuyez sur Entrée pour imprimer les scores. La sortie doit ressembler à ce qui suit :

    ```python
    >>> print(sentiment_scores)
                                                review    scores         eval
    0            I really did not like the taste of it  0.461790         BLAH
    1                  It was surprisingly quite good!  0.960192  AWESOMENESS
    2  I will never ever ever go to that place again!!  0.310344         BLAH
    >>>
    ```

> [!NOTE]
> Si les scripts de démonstration échouent, vérifiez d’abord l’emplacement du fichier. Sur les systèmes dotés de plusieurs instances de SQL Server, ou pour les instances qui s’exécutent côte à côte avec des versions autonomes, il est possible que le script d’installation ne lise pas correctement l’environnement et place les fichiers au mauvais emplacement. En général, la copie manuelle des fichiers dans le dossier mxlib approprié résout le problème.

## <a name="examples-using-pre-trained-models"></a>Exemples utilisant des modèles préformés

Le lien suivant inclut un exemple de code appelant les modèles préformés.

+ [Exemple de code : Analyse des sentiments à l’aide d’un générateur de fonctionnalités de texte](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

<a name="bkmk_resources"></a> 

## <a name="research-and-resources"></a>Recherche et ressources

Actuellement, les modèles qui sont disponibles sont les modèles de réseau neuronal profond pour l’analyse des sentiments et la classification des images. Tous les modèles préformés ont été formés à l’aide du Microsoft [Computation Network Toolkit](https://cntk.ai/Features/Index.html) ou **CNTK** .

La configuration de chaque réseau reposait sur les implémentations de référence suivantes :

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

Pour plus d’informations sur les algorithmes utilisés dans ces modèles Deep Learning et sur la façon dont ils sont implémentés et formés à l’aide de CNTK, consultez les articles suivants :

+ [Microsoft Researchers’ Algorithm Sets ImageNet Challenge Milestone](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/) (L’algorithme des chercheurs de Microsoft établit le jalon du challenge ImageNet)

+ [Microsoft Computational Network Toolkit offers most efficient distributed deep learning computational performance](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/) (Microsoft Computational Network Toolkit offre des performances de calcul Deep Learning distribuées optimisées)

## <a name="see-also"></a>Voir aussi

+ [Services de Machine Learning SQL Server](sql-machine-learning-services-windows-install.md)
+ [Mettre à niveau les composants Machine Learning (R et Python) dans les instances de SQL Server](../install/upgrade-r-and-python.md)
+ [MicrosoftML package for R](/machine-learning-server/r-reference/microsoftml/microsoftml-package) (Package MicrosoftML pour R)
+ [microsoftml package for Python](/machine-learning-server/python-reference/microsoftml/microsoftml-package) (Package microsoftml pour Python)
