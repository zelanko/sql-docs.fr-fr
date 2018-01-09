---
title: Installer de nouveaux packages Python sur SQL Server | Documents Microsoft
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 78a76403f3212c7619afbf02577075161699fbd6
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="install-new-python-packages-on-sql-server"></a>Installer de nouveaux packages Python sur SQL Server

Cet article décrit comment installer de nouveaux packages Python sur une instance de SQL Server 2017.

Il explique également comment répertorier les packages qui sont installés dans l’environnement actuel.

## <a name="prerequisites"></a>Prerequisites

Le processus d’installation de nouveaux packages est très similaire dans un environnement de Python standard. Toutefois, quelques étapes supplémentaires sont nécessaires si le serveur ne dispose pas d’une connexion internet.

+ Vous devez avoir installé Machine Learning Services (de-de base de données) avec l’option de langage Python. Pour obtenir des instructions, consultez [configurer Python Machine Learning Services](setup-python-machine-learning-services.md).

+ Pour chaque instance de serveur, vous devez installer une copie distincte du package. Les packages ne peuvent pas être partagés entre les instances.

+ Déterminer si le package que vous envisagez d’utiliser fonctionnera avec Python 3.5 et dans l’environnement Windows. 

    En règle générale, il existe de certaines restrictions sur les packages que vous pouvez importer et utiliser dans l’environnement SQL Server. Problèmes possibles sont les packages qui utilisent la fonctionnalité de réseau qui est bloquée sur le serveur ou par le pare-feu, ou avec des dépendances qui ne peut pas être installés sur un ordinateur Windows.

+ Un accès administratif au serveur est requis pour installer des packages.

## <a name="add-a-new-python-package"></a>Ajouter un nouveau package de Python

Pour cet exemple, nous supposons que vous souhaitez installer un nouveau package directement sur l’ordinateur SQL Server.

Le package est installé dans cet exemple est [CNTK](https://docs.microsoft.com/cognitive-toolkit/), une infrastructure pour l’apprentissage de profondeur à partir de Microsoft qui prend en charge la personnalisation, la formation et le partage de différents types de réseaux neuronaux.

> [!TIP]
> Besoin d’aide pour la configuration de vos outils Python ? Consultez les blogs :
> 
> [Mise en route avec les Services Web Python à l’aide du serveur de Machine Learning](https://blogs.msdn.microsoft.com/mlserver/2017/12/13/getting-started-with-python-web-services-using-machine-learning-server/)
> 
> [David Crook : Outils d’analyse Microsoft cognitifs + VS Code](http://dacrook.com/cntk-vs-code-awesome/)

### <a name="step-1-download-the-windows-version-of-the-python-package"></a>Étape 1. Télécharger la version Windows du package Python

+ Si vous installez des packages Python sur un serveur sans accès à internet, vous devez télécharger le fichier WHL vers un autre ordinateur et puis copiez-le sur le serveur.

    Par exemple, sur un ordinateur distinct, vous pouvez télécharger le fichier WHL à partir de ce site [https://cntk.ai/PythonWheel/CPU-Only](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl), puis copiez le fichier `cntk-2.1-cp35-cp35m-win_amd64.whl` dans un dossier local sur l’ordinateur SQL Server.

+ SQL Server 2017 utilise Python 3.5. Veillez à obtenir la version Windows du package et une version compatible avec Python 3.5.

Cette page contient des téléchargements pour plusieurs plateformes et plusieurs versions de Python : [configurer CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>Étape 2. Ouvrez une invite de commandes de Python

Recherchez l’emplacement de bibliothèque de Python par défaut utilisé par SQL Server. Si vous avez installé plusieurs instances, veillez à localiser le dossier PYTHON_SERVICE pour l’instance où vous souhaitez ajouter le package.

Par exemple, si la Machine Learning Services a été installé à l’aide des valeurs par défaut et apprentissage automatique est activée sur l’instance par défaut, le chemin d’accès serait comme suit :

    `C:\Program Files\Microsoft SQL  Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

Ouvrez l’invite de commande Python associé à l’instance.

> [!TIP]
> Nous vous recommandons de définir un environnement de Python spécifiques à la Machine Learning Server ou SQL Server.

### <a name="step-3-install-the-package-using-pip"></a>Étape 3. Installez le package à l’aide du pip

+ Si vous êtes habitué à l’aide de la ligne de commande Python, utilisez PIP.exe pour installer les nouveaux packages. Vous pouvez trouver la **pip** programme d’installation dans le `Scripts` sous-dossier. 

    Si vous obtenez une erreur **pip** n’est pas reconnu comme une commande interne ou externe, vous pouvez ajouter le chemin d’accès de l’exécutable de Python et le dossier de scripts Python à la variable de chemin d’accès dans Windows.

    Le chemin d’accès complet de le **Scripts** dossier dans une installation par défaut est la suivante :

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Scripts`

+ Si vous utilisez Visual Studio 2017 ou Visual Studio 2015 avec les extensions de Python, vous pouvez exécuter `pip install` à partir de la **environnements Python** fenêtre. Cliquez sur **Packages**et dans la zone de texte, indiquez le nom ou l’emplacement du package à installer. Vous n’avez pas besoin de type `pip install`; il est renseigné pour vous automatiquement. 

    - Si l’ordinateur a accès à Internet, fournissez le nom du package, ou l’URL d’un package spécifique et la version. Par exemple, pour installer la version de CNTK est pris en charge pour Windows et Python 3.5, vous pouvez spécifier l’URL de téléchargement :`https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - Si l’ordinateur n’a pas accès à internet, vous devez avez téléchargé le fichier WHL à l’avance. Ensuite, spécifiez le chemin d’accès local et le nom. Par exemple, collez le chemin d’accès et le fichier pour installer le fichier WHL téléchargé depuis le site suivant :`"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

Vous pouvez être invité à élever les autorisations pour terminer l’installation.

En tant qu’installation suit son cours, vous pouvez voir les messages d’état dans la fenêtre d’invite de commandes :

```python
pip install https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
Collecting cntk==2.1 from https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
  Downloading https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl (34.1MB)
    100% |################################| 34.1MB 13kB/s
...
Installing collected packages: cntk
Successfully installed cntk-2.1
```



### <a name="step-4-load-the-package-or-its-functions-as-part-of-your-script"></a>Étape 4. Charger le package ou ses fonctions dans le cadre de votre script.

Lors de l’installation est terminée, vous pouvez commencer immédiatement à l’aide du package comme décrit dans l’étape suivante.

Pour des exemples d’apprentissage approfondie à l’aide de CNTK, consultez ces didacticiels : [API Python pour CNTK](https://cntk.ai/pythondocs/tutorials.html)

Pour utiliser des fonctions à partir du package dans votre script, insérez la norme `import <package_name>` instruction dans la ligne initiale du script :

```python
import numpy as np
import cntk as cntk
cntk._version_
```

##  <a name="how-to-view-installed-packages-using-conda"></a>Comment afficher les packages installés à l’aide de conda

Il existe différentes façons dont vous pouvez obtenir une liste des packages installés. Par exemple, vous pouvez afficher les packages installés dans le **environnements Python** windows de Visual Studio.

Si vous utilisez la ligne de commande Python, vous pouvez utiliser la **conda** package manager, qui est incluse dans l’environnement Anaconda Python ajoutée par le programme d’installation de SQL Server.

Pour afficher les packages Python qui ont été installés dans l’environnement actuel, exécutez cette commande à partir des fenêtres d’invite de commandes :

```python
conda list
```

Pour plus d’informations sur **conda** et comment vous pouvez l’utiliser pour créer et gérer plusieurs environnements Python, consultez [gestion des environnements avec conda](https://conda.io/docs/user-guide/tasks/manage-environments.html).
