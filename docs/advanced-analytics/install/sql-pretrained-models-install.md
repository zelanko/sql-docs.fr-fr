---
title: Installer des modèles de Machine Learning pré-formés
description: Ajoutez des modèles préformés pour l’analyse des sentiments et l’image caractérisation pour SQL Server 2017 Machine Learning Services (R ou python) ou SQL Server 2016 R services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: f89e638b6b9486b17974a04af6076e6c7154fa88
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470349"
---
# <a name="install-pre-trained-machine-learning-models-on-sql-server"></a>Installer des modèles de Machine Learning pré-formés sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment utiliser PowerShell pour ajouter des modèles de Machine Learning pré-formés gratuits pour l' *analyse des sentiments* et des *caractérisation d’images* à une instance SQL Server avec intégration de R ou python. Les modèles préformés sont générés par Microsoft et prêts à être utilisés, ajoutés à une instance en tant que tâche après l’installation. Pour plus d’informations sur ces modèles, consultez la section [ressources](#bkmk_resources) de cet article.

Une fois installés, les modèles préformés sont considérés comme des détails d’implémentation qui alimentent des fonctions spécifiques dans les bibliothèques MicrosoftML (R) et MicrosoftML (Python). Vous ne devez pas (et ne pouvez pas) afficher, personnaliser ou reformer les modèles. vous ne pouvez pas non plus les traiter en tant que ressource indépendante dans du code personnalisé ou dans d’autres fonctions couplées. 

Pour utiliser les modèles préformés, appelez les fonctions indiquées dans le tableau suivant.

| Fonction R (MicrosoftML) | Fonction Python (microsoftml) | Utilisation |
|--------------------------|-------------------------------|-------|
| [getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | [get_sentiment](https://docs.microsoft.com//machine-learning-server/python-reference/microsoftml/get-sentiment) | Génère un score de sentiment positif positif sur les entrées de texte. |
| [featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | [featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Extrait des informations de texte à partir des entrées du fichier image. |

## <a name="prerequisites"></a>Prérequis

Les algorithmes d’apprentissage automatique nécessitent beaucoup de ressources de calcul. Nous vous recommandons 16 Go de RAM pour les charges de travail de faible à modéré, y compris l’achèvement des procédures pas à pas du didacticiel utilisant tous les exemples de données.

Vous devez disposer de droits d’administrateur sur l’ordinateur et SQL Server pour ajouter des modèles préformés.

Les scripts externes doivent être activés et SQL Server Service LaunchPad doit être en cours d’exécution. Les instructions d’installation fournissent les étapes nécessaires à l’activation et à la vérification de ces fonctionnalités. 

Le package [MicrosoftML R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) ou le [package Python MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) contiennent les modèles préformés.

+ [SQL Server 2017 machine learning services](sql-machine-learning-services-windows-install.md) contient les deux versions linguistiques de la bibliothèque machine learning, ce prérequis est donc respecté sans aucune autre action de votre part. Étant donné que les bibliothèques sont présentes, vous pouvez utiliser le script PowerShell décrit dans cet article pour ajouter les modèles préformés à ces bibliothèques.

+ [SQL Server 2016 r services](sql-r-services-windows-install.md), qui est r uniquement, n’inclut pas le [package MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) prêt à l’emploi. Pour ajouter MicrosoftML, vous devez effectuer une [mise à niveau de composant](../install/upgrade-r-and-python.md). L’un des avantages de la mise à niveau des composants est que vous pouvez ajouter simultanément les modèles préformés, ce qui rend l’exécution du script PowerShell inutile. Toutefois, si vous avez déjà effectué la mise à niveau, mais que vous n’avez pas ajouté les modèles préformés pour la première fois, vous pouvez exécuter le script PowerShell comme décrit dans cet article. Il fonctionne pour les deux versions de SQL Server. Avant cela, vérifiez que la bibliothèque MicrosoftML existe dans C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library.


<a name="file-location"></a>

## <a name="check-whether-pre-trained-models-are-installed"></a>Vérifier si des modèles préformés sont installés

Les chemins d’installation des modèles R et Python sont les suivants:

+ Pour R:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64`

+ Pour Python:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs`

Les noms de fichiers de modèles sont répertoriés ci-dessous:

+ AlexNet\_mis à jour. Model
+ ImageNet1K\_mean.xml
+ préformation. modèle
+ ResNet\_101\_mis à jour. Model
+ ResNet\_18\_mis à jour. modèle
+ ResNet\_50\_mis à jour. Model

Si les modèles sont déjà installés, passez directement à l' [étape de validation](#verify) pour confirmer la disponibilité.

## <a name="download-the-installation-script"></a>Télécharger le script d’installation

Cliquez [https://aka.ms/mlm4sql](https://aka.ms/mlm4sql) pour télécharger le fichier **install-MLModels. ps1**.

## <a name="execute-with-elevated-privileges"></a>Exécuter avec des privilèges élevés

1. Démarrez PowerShell. Dans la barre des tâches, cliquez avec le bouton droit sur l’icône du programme PowerShell et sélectionnez **exécuter en tant qu’administrateur**.
2. Entrez un chemin d’accès complet au fichier de script d’installation et incluez le nom de l’instance. En supposant que le dossier téléchargements et une instance par défaut, la commande peut se présenter comme suit:

   ```powershell
   PS C:\WINDOWS\system32> C:\Users\<user-name>\Downloads\Install-MLModels.ps1 MSSQLSERVER
   ```

**Sortie**

Sur une instance par défaut connectée à Internet SQL Server 2017 Machine Learning avec R et Python, vous devez voir des messages similaires à ce qui suit.

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

Commencez par Rechercher les nouveaux fichiers dans le [dossier mxlibs](#file-location). Ensuite, exécutez le code de démonstration pour confirmer que les modèles sont installés et fonctionnels. 

### <a name="r-verification-steps"></a>Étapes de vérification R

1. Démarrez **RGUI. EXE** dans C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\bin\x64.

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

3. Appuyez sur entrée pour afficher les scores de sentiment. La sortie doit être la suivante:

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

### <a name="python-verification-steps"></a>Étapes de vérification de Python

1. Démarrez **Python. exe** à l’emplacement C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES.

2. Collez le script Python suivant à l’invite de commandes.

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

3. Appuyez sur entrée pour imprimer les scores. La sortie doit être la suivante:

    ```python
    >>> print(sentiment_scores)
                                                review    scores         eval
    0            I really did not like the taste of it  0.461790         BLAH
    1                  It was surprisingly quite good!  0.960192  AWESOMENESS
    2  I will never ever ever go to that place again!!  0.310344         BLAH
    >>>
    ```

> [!NOTE]
> Si les scripts de démonstration échouent, vérifiez d’abord l’emplacement du fichier. Sur les systèmes dotés de plusieurs instances de SQL Server, ou pour les instances qui s’exécutent côte à côte avec des versions autonomes, il est possible pour le script d’installation de mal lire l’environnement et de placer les fichiers à un emplacement incorrect. En général, la copie manuelle des fichiers dans le dossier mxlib correct résout le problème.

## <a name="examples-using-pre-trained-models"></a>Exemples utilisant des modèles préformés

Le lien suivant inclut un exemple de code appelant les modèles préformés.

+ [Exemple de code: Analyse des sentiments à l’aide de Caractériseur comptage de texte](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

<a name="bkmk_resources"></a> 

## <a name="research-and-resources"></a>Recherche et ressources

Actuellement, les modèles qui sont disponibles sont les modèles DNN (Deep Neural Network) pour l’analyse des sentiments et la classification des images. Tous les modèles préformés ont été formés à l’aide de la [boîte à outils Network Computing](https://cntk.ai/Features/Index.html)de Microsoft, ou **CNTK**.

La configuration de chaque réseau repose sur les implémentations de référence suivantes:

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

Pour plus d’informations sur les algorithmes utilisés dans ces modèles d’apprentissage profond et sur la façon dont ils sont implémentés et formés à l’aide de CNTK, consultez les articles suivants:

+ [Étape majeure du Challenge des ImageNet Microsoft chercheurs](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft calculation Network Toolkit offre des performances de calcul d’apprentissage profond distribuées les plus efficaces](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="see-also"></a>Voir aussi

+ [SQL Server 2016 R services](sql-r-services-windows-install.md)
+ [SQL Server 2017 Machine Learning Services](sql-machine-learning-services-windows-install.md)
+ [Mettre à niveau les composants R et Python dans des instances SQL Server](../install/upgrade-r-and-python.md)
+ [Package MicrosoftML pour R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)
+ [package microsoftml pour Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)
