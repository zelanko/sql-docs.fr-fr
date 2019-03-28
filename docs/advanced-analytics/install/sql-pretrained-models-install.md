---
title: Installer PRÉFORMÉE modèles machine learning - SQL Server Machine Learning
description: Ajouter des modèles préentraînés pour une caractérisation sentiment analysis et l’image à SQL Server 2017 Machine Learning Services (R ou Python) ou SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/18/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 168898c08fb24af655ff5429e2a7fa028ea37405
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512296"
---
# <a name="install-pre-trained-machine-learning-models-on-sql-server"></a>Installer PRÉFORMÉE modèles machine learning sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment utiliser Powershell pour ajouter gratuit pour les modèles d’apprentissage préformé *analyse des sentiments* et *image caractérisation* à une instance du moteur de base de données SQL Server avec R ou Python intégration. Les modèles préentraînés sont générés par Microsoft et prêt à l’emploi, ajouté à une instance du moteur de base de données comme une tâche de post-installation. Pour plus d’informations sur ces modèles, consultez le [ressources](#bkmk_resources) section de cet article.

Une fois installé, les modèles préentraînés sont considérés comme un détail d’implémentation qui alimentent des fonctions spécifiques de MicrosoftML (R) et de bibliothèques de microsoftml (Python). Vous ne doivent pas (et ne peut pas) permet d’afficher, personnaliser ou reformer les modèles, ni pourrez vous les traiter comme une ressource indépendante dans du code personnalisé ou associés d’autres fonctions. 

Pour utiliser les modèles préformés, appelez les fonctions répertoriées dans le tableau suivant.

| Fonction R (MicrosoftML) | Fonction Python (microsoftml) | Utilisation |
|--------------------------|-------------------------------|-------|
| [getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | [get_sentiment](https://docs.microsoft.com//machine-learning-server/python-reference/microsoftml/get-sentiment) | Génère le score de sentiment de positif en négatif sur les entrées de texte. [En savoir plus](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/).|
| [featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | [featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Extrait les informations de texte à partir des entrées de fichier image. [En savoir plus](https://blogs.msdn.microsoft.com/mlserver/2017/04/12/image-featurization-with-a-pre-trained-deep-neural-network-model/). |

## <a name="prerequisites"></a>Prérequis

Algorithmes d’apprentissage automatique sont intensifs. Nous vous recommandons 16 Go de RAM pour les charges de travail de faible à modérée, y compris la saisie de procédures pas à pas du didacticiel à l’aide de tous les exemples de données.

Vous devez disposer des droits d’administrateur sur l’ordinateur et SQL Server pour ajouter des modèles préentraînés.

Scripts externes doivent être activées et le service SQL Server LaunchPad doit être en cours d’exécution. Instructions d’installation fournissent les étapes pour l’activation et la vérification de ces fonctionnalités. 

[Package MicrosoftML R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) ou [microsoftml le package Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) contiennent les modèles préformés.

+ [SQL Server 2017 Machine Learning Services](sql-machine-learning-services-windows-install.md) inclut les deux versions de langue de la bibliothèque d’apprentissage, donc cette condition préalable est remplie avec aucune action supplémentaire de votre part. Étant donné que les bibliothèques sont présents, vous pouvez utiliser le script PowerShell décrit dans cet article pour ajouter les modèles préformés à ces bibliothèques.

+ [SQL Server 2016 R Services](sql-r-services-windows-install.md), qui est R uniquement, n’inclut pas [package MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) prêts à l’emploi. Pour ajouter MicrosoftML, vous devez effectuer un [mise à niveau du composant](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). L’un des avantages de la mise à niveau du composant sont que vous pouvez ajouter simultanément les modèles préentraînés, ce qui permet d’exécuter le script PowerShell inutile. Toutefois, si vous avez déjà mis à niveau mais que vous manqué Ajout les modèles préentraînés votre première tentative, vous pouvez exécuter le script PowerShell comme décrit dans cet article. Il fonctionne pour les deux versions de SQL Server. Avant de procéder, vérifiez que la bibliothèque de MicrosoftML existe à C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library.


<a name="file-location"></a>

## <a name="check-whether-pre-trained-models-are-installed"></a>Vérifiez si les modèles préentraînés sont installés

Les chemins d’accès de l’installation pour les modèles R et Python sont les suivantes :

+ Pour r : `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64`

+ Pour Python : `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs`

Les noms de fichiers de modèle sont répertoriées ci-dessous :

+ AlexNet\_Updated.model
+ ImageNet1K\_mean.xml
+ pretrained.model
+ ResNet\_101\_Updated.model
+ ResNet\_18\_Updated.model
+ ResNet\_50\_Updated.model

Si les modèles sont déjà installés, passez directement à la [étape de validation](#verify) pour confirmer la disponibilité.

## <a name="download-the-installation-script"></a>Télécharger le script d’installation

Cliquez sur [ https://aka.ms/mlm4sql ](https://aka.ms/mlm4sql) pour télécharger le fichier **Install-MLModels.ps1**.

## <a name="execute-with-elevated-privileges"></a>Exécuter avec des privilèges élevés

1. Démarrez PowerShell. Dans la barre des tâches, cliquez sur l’icône de programme PowerShell et sélectionnez **exécuter en tant qu’administrateur**.
2. Entrez un chemin d’accès complet au fichier de script d’installation et inclure le nom de l’instance. En supposant que le dossier Téléchargements et une instance par défaut, la commande peut ressembler à ceci :

   ```powershell
   PS C:\WINDOWS\system32> C:\Users\<user-name>\Downloads\Install-MLModels.ps1 MSSQLSERVER
   ```

**Output**

Sur une connecté à internet SQL Server 2017 Machine Learning instance par défaut avec R et Python, vous devez voir des messages semblables à ce qui suit.

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

Vérifiez tout d’abord, pour les nouveaux fichiers dans le [mxlibs dossier](#file-location). Ensuite, exécutez le code de démonstration pour vérifier que les modèles sont installés et opérationnels. 

### <a name="r-verification-steps"></a>Étapes de vérification de R

1. Démarrer **RGUI. EXE** à C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\bin\x64.

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

3. Appuyez sur ENTRÉE pour afficher les scores de sentiments. Sortie doit se présenter comme suit :

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

1. Démarrer **Python.exe** à C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES.

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

3. Appuyez sur ENTRÉE pour imprimer les scores. Sortie doit se présenter comme suit :

    ```python
    >>> print(sentiment_scores)
                                                review    scores         eval
    0            I really did not like the taste of it  0.461790         BLAH
    1                  It was surprisingly quite good!  0.960192  AWESOMENESS
    2  I will never ever ever go to that place again!!  0.310344         BLAH
    >>>
    ```

> [!NOTE]
> Si les scripts de démonstration échouent, vérifiez d’abord l’emplacement du fichier. Sur les systèmes disposant de plusieurs instances de SQL Server, ou pour les instances qui s’exécutent côte à côte avec les versions autonomes, il est possible pour le script d’installation mal lire l’environnement et de placer les fichiers dans un emplacement incorrect. En règle générale, la copie manuellement des fichiers dans le dossier correct mxlib résout le problème.

## <a name="examples-using-pre-trained-models"></a>Exemples d’utilisation de modèles préentraînés

Les liens suivants comportent des procédures pas à pas et des exemples de code appelant des modèles préformés.

+ [Analyse des sentiments avec Python dans SQL Server Machine Learning Services](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/)

+ [Personnalisation d’image avec un modèle de réseau de neurones profond préformé](https://blogs.msdn.microsoft.com/mlserver/2017/04/12/image-featurization-with-a-pre-trained-deep-neural-network-model/)

  Le modèle préformé pour les images prend en charge la personnalisation d’images que vous fournissez. Pour utiliser le modèle, vous appelez le **featurizeImage** transformer. L’image est chargée, redimensionné et caractérisées par le modèle formé. La sortie de la préapprentissage de réseau de neurones profond est ensuite utilisée pour former un modèle linéaire pour la classification d’images. Pour utiliser ce modèle, toutes les images doivent être redimensionnés pour répondre aux exigences du modèle formé. Par exemple, si vous utilisez un modèle AlexNet, l’image doit être redimensionnée à 227 x 227 px.

+ [Exemple de code : Analyse des sentiments à l’aide de texte Préapprentissage](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

<a name="bkmk_resources"></a> 

## <a name="research-and-resources"></a>Recherche et ressources

Actuellement, les modèles qui sont disponibles sont les modèles de réseaux de neurones profonds (DNN) pour la classification du sentiment analysis et image. Tous les modèles préformés ont été formés à l’aide de Microsoft [calcul Network Toolkit](https://cntk.ai/Features/Index.html), ou **CNTK**.

La configuration de chaque réseau était basée sur les implémentations de référence suivantes :

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

Pour plus d’informations sur les algorithmes utilisés dans ces modèles d’apprentissage profond et la façon dont elles sont implémentées et formé à l’aide de CNTK, consultez les articles suivants :

+ [Algorithme de chercheurs de Microsoft définit ImageNet défi jalon](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft Computational Network Toolkit offre la plus efficace des performances de calcul dlvm distribuée](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="see-also"></a>Voir aussi

+ [SQL Server 2016 R Services](sql-r-services-windows-install.md)
+ [SQL Server 2017 Machine Learning Services](sql-machine-learning-services-windows-install.md)
+ [Mettre à niveau les composants R et Python dans les instances SQL Server](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
+ [Package MicrosoftML pour R](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)
+ [package microsoftml pour Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)
