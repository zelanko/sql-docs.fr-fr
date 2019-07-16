---
title: Installer de nouveaux packages de langage Python - SQL Server Machine Learning
description: Ajouter de nouveaux packages de Python pour SQL Server 2017 Machine Learning Services (en base de données) et Machine Learning Server (autonome).
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/16/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: f30c00503a0dd183619550d3ab0e92c0be1449dd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962775"
---
# <a name="install-new-python-packages-on-sql-server"></a>Installer de nouveaux packages de Python sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment installer de nouveaux packages de Python sur une instance de SQL Server 2017 Machine Learning Services. En règle générale, le processus d’installation de nouveaux packages est similaire à celle dans un environnement Python standard. Toutefois, quelques étapes supplémentaires sont nécessaires si le serveur ne dispose pas d’une connexion internet.

Pour plus d’informations sur les chemins d’installation et emplacement de package, consultez [obtenir de R ou Python sur les packages](../package-management/installed-package-information.md).

## <a name="prerequisites"></a>Prérequis

+ [SQL Server 2017 Machine Learning Services (en base de données)](../install/sql-machine-learning-services-windows-install.md) avec l’option de langage Python. 

+ Packages doivent être Python 3.5 conforme et exécuté sur Windows. 

+ Accès administratif au serveur est requis pour installer des packages.

## <a name="considerations"></a>Observations

Avant d’ajouter des packages, envisagez si le package est adapté à l’environnement SQL Server. En règle générale, un serveur de base de données est une ressource partagée prenant en charge de plusieurs charges de travail. Si vous ajoutez des packages qui trop solliciter calcul sur le serveur, les performances seront affectées. 

En outre, certains packages Python populaires (par exemple, Flask) effectuer des tâches, tels que le développement web, qui sont mieux adaptées pour un environnement autonome. Nous vous recommandons d’utiliser Python dans la base de données pour les tâches qui bénéficient d’une intégration étroite avec le moteur de base de données, comme machine learning, plutôt que les tâches que simplement interroger la base de données.

Serveurs de base de données sont fréquemment verrouillés. Dans de nombreux cas, les accès à Internet est entièrement bloqué. Pour les packages avec une longue liste de dépendances, vous devez identifier ces dépendances à l’avance et être prêt à installer manuellement de chacun d’eux.

## <a name="add-a-new-python-package"></a>Ajouter un nouveau package de Python

Pour cet exemple, nous partons du principe que vous souhaitez installer un nouveau package directement sur l’ordinateur SQL Server.

Installation du package s’effectue par instance. Si vous avez plusieurs instances de Machine Learning Services, vous devez ajouter le package à chacun d’eux.

Le package est installé dans cet exemple est [CNTK](https://docs.microsoft.com/cognitive-toolkit/), une infrastructure pour l’apprentissage profond de Microsoft qui prend en charge la personnalisation, la formation et le partage des différents types de réseaux neuronaux.

### <a name="step-1-download-the-windows-version-of-the-python-package"></a>Étape 1. Téléchargez la version Windows du package Python

+ Si vous installez les packages Python sur un serveur sans accès à internet, vous devez télécharger le fichier WHL vers un autre ordinateur et copiez-le sur le serveur.

    Par exemple, sur un ordinateur distinct, vous pouvez télécharger le fichier WHL à partir de ce site [ https://cntk.ai/PythonWheel/CPU-Only ](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl), puis copiez le fichier `cntk-2.1-cp35-cp35m-win_amd64.whl` dans un dossier local sur l’ordinateur SQL Server.

+ SQL Server 2017 utilise Python 3.5. 

> [!IMPORTANT]
> Assurez-vous que vous obtenez la version Windows du package. Si le fichier se termine par .gz, il n’est probablement pas la bonne version.

Cette page contient des téléchargements pour plusieurs plateformes et pour plusieurs versions de Python : [Configurer CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>Étape 2. Ouvrez une invite de commande Python

Recherchez l’emplacement de bibliothèque de Python par défaut utilisé par SQL Server. Si vous avez installé plusieurs instances, recherchez le dossier PYTHON_SERVICE pour l’instance où vous souhaitez ajouter le package.

Par exemple, si la Machine Learning Services a été installé à l’aide des valeurs par défaut, et apprentissage automatique est activé sur l’instance par défaut, le chemin d’accès serait comme suit :

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Ouvrez l’invite de commande Python associé à l’instance.

> [!TIP]
> Pour les futures, débogage et test, vous souhaiterez configurer un environnement Python spécifique à la bibliothèque de l’instance.

### <a name="step-3-install-the-package-using-pip"></a>Étape 3. Installez le package à l’aide de pip

+ Si vous êtes habitué à l’aide de la ligne de commande Python, utilisez PIP.exe pour installer de nouveaux packages. Vous pouvez trouver la **pip** programme d’installation dans le `Scripts` sous-dossier. 

  Le programme d’installation de SQL Server n’ajoute pas de Scripts pour le chemin d’accès système. Si vous obtenez une erreur `pip` n’est pas reconnu comme une commande interne ou externe, vous pouvez ajouter le dossier Scripts à la variable de chemin d’accès dans Windows.

  Le chemin d’accès complet de le **Scripts** dossier dans une installation par défaut est la suivante :

    C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts

+ Si vous utilisez Visual Studio 2017 ou Visual Studio 2015 avec les extensions de Python, vous pouvez exécuter `pip install` à partir de la **environnements Python** fenêtre. Cliquez sur **Packages**et dans la zone de texte, indiquez le nom ou l’emplacement du package à installer. Vous n’avez pas besoin de taper `pip install`; il est renseigné pour vous automatiquement. 

    - Si l’ordinateur a accès à Internet, fournissez le nom du package, ou l’URL d’un package spécifique et une version. 
    
    Par exemple, pour installer la version de CNTK est pris en charge pour Windows et Python 3.5, vous devez spécifier l’URL de téléchargement : `https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - Si l’ordinateur n’a pas accès à internet, vous devez télécharger le fichier WHL avant de commencer l’installation. Ensuite, spécifiez le chemin d’accès local et le nom. Par exemple, collez le chemin d’accès et le fichier pour installer le fichier WHL téléchargé depuis le site suivant : `"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

Vous pouvez être invité à élever les autorisations pour terminer l’installation.

En tant qu’installation progresse, vous pouvez voir les messages d’état dans la fenêtre d’invite de commandes :

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

Lors de l’installation est terminée, vous pouvez commencer immédiatement à l’aide du package comme décrit dans l’étape suivante.

Pour obtenir des exemples d’apprentissage profond à l’aide de CNTK, consultez ces didacticiels : [API Python pour CNTK](https://cntk.ai/pythondocs/tutorials.html)

Pour utiliser les fonctions à partir du package dans votre script, insérez la norme `import <package_name>` instruction dans les lignes initiales du script :

```python
import numpy as np
import cntk as cntk
cntk._version_
```

## <a name="list-installed-packages-using-conda"></a>Lister les packages installés à l’aide de conda

Il existe différentes façons dont vous pouvez obtenir une liste des packages installés. Par exemple, vous pouvez afficher les packages installés dans le **environnements Python** windows de Visual Studio.

Si vous utilisez la ligne de commande Python, vous pouvez utiliser **Pip** ou **conda** Gestionnaire de package, inclus avec l’environnement Anaconda Python ajoutée par le programme d’installation de SQL Server.

1. Accédez à C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Scripts

1. Avec le bouton droit **conda.exe** > **exécuter en tant qu’administrateur**, puis entrez `conda list` pour retourner une liste des packages installés dans l’environnement actuel.

1. De même, avec le bouton droit **pip.exe** > **exécuter en tant qu’administrateur**, puis entrez `pip list` pour retourner les mêmes informations. 

Pour plus d’informations sur **conda** et comment vous pouvez l’utiliser pour créer et gérer plusieurs environnements Python, consultez [la gestion des environnements avec conda](https://conda.io/docs/user-guide/tasks/manage-environments.html).

> [!Note]
> Le programme d’installation de SQL Server n’ajoute pas de Pip ou Conda pour le chemin d’accès système et sur une instance de SQL Server de production, maintenir les exécutables non essentielles hors le chemin d’accès est une bonne pratique. Toutefois, pour les environnements de développement et de test, vous pouvez ajouter le dossier Scripts à la variable d’environnement de chemin d’accès système pour exécuter Pip et Conda sur la commande à partir de n’importe quel emplacement.
