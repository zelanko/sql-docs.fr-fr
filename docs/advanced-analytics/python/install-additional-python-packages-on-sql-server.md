---
title: Installer de nouveaux packages de langage Python
description: Ajoutez de nouveaux packages Python à SQL Server 2017 Machine Learning Services (dans la base de données) et Machine Learning Server (autonome).
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/16/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: fc8c7148369ec1a501106e573e195a8f0b7f060a
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470259"
---
# <a name="install-new-python-packages-on-sql-server"></a>Installer de nouveaux packages Python sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment installer de nouveaux packages Python sur une instance de SQL Server 2017 Machine Learning Services. En général, le processus d’installation de nouveaux packages est semblable à celui d’un environnement python standard. Toutefois, certaines étapes supplémentaires sont requises si le serveur n’a pas de connexion Internet.

Pour plus d’informations sur l’emplacement des packages et les chemins d’installation, consultez obtenir des informations sur les [packages R ou python](../package-management/installed-package-information.md).

## <a name="prerequisites"></a>Prérequis

+ [SQL Server 2017 machine learning services (en base de données)](../install/sql-machine-learning-services-windows-install.md) avec l’option de langage Python. 

+ Les packages doivent être conformes à python 3,5 et s’exécuter sur Windows. 

+ L’accès administratif au serveur est requis pour installer des packages.

## <a name="considerations"></a>Observations

Avant d’ajouter des packages, déterminez si le package est adapté à l’environnement de SQL Server. En général, un serveur de base de données est une ressource partagée qui prend en charge plusieurs charges de travail. Si vous ajoutez des packages qui placent une pression de calcul trop importante sur le serveur, les performances en seront affectées. 

En outre, certains packages python populaires (comme les fioles) effectuent des tâches, telles que le développement Web, qui sont mieux adaptées à un environnement autonome. Nous vous recommandons d’utiliser python dans la base de données pour les tâches qui bénéficient d’une intégration étroite avec le moteur de base de données, par exemple Machine Learning, plutôt que des tâches qui interrogent simplement la base de données.

Les serveurs de base de données sont souvent verrouillés. Dans de nombreux cas, l’accès à Internet est entièrement bloqué. Pour les packages avec une longue liste de dépendances, vous devez identifier ces dépendances à l’avance et les installer manuellement.

## <a name="add-a-new-python-package"></a>Ajouter un nouveau package Python

Pour cet exemple, nous partons du principe que vous souhaitez installer un nouveau package directement sur l’ordinateur SQL Server.

L’installation du package est par instance. Si vous avez plusieurs instances de Machine Learning Services, vous devez ajouter le package à chacun d’eux.

Le package installé dans cet exemple est [CNTK](https://docs.microsoft.com/cognitive-toolkit/), une infrastructure d’apprentissage approfondi de Microsoft qui prend en charge la personnalisation, la formation et le partage de différents types de réseaux neuronaux.

### <a name="step-1-download-the-windows-version-of-the-python-package"></a>Étape 1. Télécharger la version Windows du package Python

+ Si vous installez des packages Python sur un serveur sans accès à Internet, vous devez télécharger le fichier WHL sur un autre ordinateur, puis le copier sur le serveur.

    Par exemple, sur un ordinateur distinct, vous pouvez télécharger le fichier WHL à partir de [https://cntk.ai/PythonWheel/CPU-Only](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl)ce site, puis copier le `cntk-2.1-cp35-cp35m-win_amd64.whl` fichier dans un dossier local sur l’ordinateur SQL Server.

+ SQL Server 2017 utilise python 3,5. 

> [!IMPORTANT]
> Assurez-vous que vous disposez de la version Windows du package. Si le fichier se termine par. gz, il ne s’agit probablement pas de la bonne version.

Cette page contient des téléchargements pour plusieurs plateformes et pour plusieurs versions de Python: [Configurer CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>Étape 2. Ouvrir une invite de commandes python

Localisez l’emplacement de la bibliothèque python par défaut utilisé par SQL Server. Si vous avez installé plusieurs instances, recherchez le dossier PYTHON_SERVICE pour l’instance où vous souhaitez ajouter le package.

Par exemple, si Machine Learning Services a été installé à l’aide des valeurs par défaut et que Machine Learning est activé sur l’instance par défaut, le chemin d’accès est le suivant:

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Ouvrez l’invite de commandes python associée à l’instance.

> [!TIP]
> Pour un débogage et des tests ultérieurs, vous souhaiterez peut-être configurer un environnement python spécifique à la bibliothèque d’instances.

### <a name="step-3-install-the-package-using-pip"></a>Étape 3. Installer le package à l’aide de PIP

+ Si vous êtes habitué à utiliser la ligne de commande Python, utilisez PIP. exe pour installer de nouveaux packages. Vous pouvez trouver le  programme d’installation PIP `Scripts` dans le sous-dossier. 

  SQL Server programme d’installation n’ajoute pas de scripts au chemin d’accès système. Si vous recevez une erreur qui `pip` n’est pas reconnue en tant que commande interne ou externe, vous pouvez ajouter le dossier scripts à la variable path dans Windows.

  Le chemin d’accès complet du dossier **scripts** dans une installation par défaut est le suivant:

    C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts

+ Si vous utilisez Visual Studio 2017 ou Visual Studio 2015 avec les extensions Python, vous pouvez exécuter `pip install` à partir de la fenêtre **environnements python** . Cliquez sur **packages**, puis dans la zone de texte, indiquez le nom ou l’emplacement du package à installer. Vous n’avez pas besoin `pip install`de taper. elle est remplie automatiquement pour vous. 

    - Si l’ordinateur a accès à Internet, indiquez le nom du package ou l’URL d’un package et d’une version spécifiques. 
    
    Par exemple, pour installer la version de CNTK prise en charge pour Windows et Python 3,5, spécifiez l’URL de téléchargement:`https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - Si l’ordinateur n’a pas accès à Internet, vous devez télécharger le fichier WHL avant de commencer l’installation. Ensuite, spécifiez le chemin d’accès et le nom du fichier local. Par exemple, collez le chemin d’accès et le fichier suivants pour installer le fichier WHL téléchargé à partir du site:`"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

Vous pouvez être invité à élever les autorisations pour terminer l’installation.

À mesure que l’installation progresse, vous pouvez voir les messages d’État dans la fenêtre d’invite de commandes:

```python
pip install https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
Collecting cntk==2.1 from https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
  Downloading https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl (34.1MB)
    100% |################################| 34.1MB 13kB/s
...
Installing collected packages: cntk
Successfully installed cntk-2.1
```


### <a name="step-4-load-the-package-or-its-functions-as-part-of-your-script"></a>Étape 4. Charger le package ou ses fonctions dans le cadre de votre script

Une fois l’installation terminée, vous pouvez commencer immédiatement à utiliser le package comme décrit à l’étape suivante.

Pour obtenir des exemples d’apprentissage profond à l’aide de CNTK, consultez les didacticiels suivants: [API Python pour CNTK](https://cntk.ai/pythondocs/tutorials.html)

Pour utiliser les fonctions du package dans votre script, insérez l’instruction `import <package_name>` standard dans les lignes initiales du script:

```python
import numpy as np
import cntk as cntk
cntk._version_
```

## <a name="list-installed-packages-using-conda"></a>Répertorier les packages installés à l’aide de Conda

Il existe différentes façons d’obtenir la liste des packages installés. Par exemple, vous pouvez afficher les packages installés dans les fenêtres **environnements python** de Visual Studio.

Si vous utilisez la ligne de commande Python, vous pouvez utiliser **PIP** ou le gestionnaire  de package Conda, inclus dans l’environnement Anaconda python ajouté par le programme d’installation de SQL Server.

1. Accédez à C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts

1. Cliquez avec le bouton droit sur **Conda. exe** > **exécuter en tant qu’administrateur**, puis entrez `conda list` pour retourner la liste des packages installés dans l’environnement actuel.

1. De même, cliquez avec le bouton droit sur **PIP. exe** > **exécuter en tant qu’administrateur**, puis entrez `pip list` pour retourner les mêmes informations. 

Pour plus d’informations  sur Conda et sur la façon dont vous pouvez l’utiliser pour créer et gérer plusieurs environnements Python, consultez [gestion des environnements avec Conda](https://conda.io/docs/user-guide/tasks/manage-environments.html).

> [!Note]
> SQL Server installation n’ajoute pas PIP ou Conda au chemin d’accès système et sur une instance de SQL Server de production, il est recommandé de conserver les exécutables non essentiels en dehors du chemin d’accès. Toutefois, pour les environnements de développement et de test, vous pouvez ajouter le dossier scripts à la variable d’environnement du chemin d’accès système pour exécuter la commande PIP et Conda sur n’importe quel emplacement.
