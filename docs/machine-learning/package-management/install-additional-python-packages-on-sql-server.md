---
title: Installer des packages Python avec sqlmlutils
description: Découvrez comment utiliser le PIP Python pour installer de nouveaux packages Python sur une instance de SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/30/2020
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4e72ded2e2f2a51805403132c662bff3d70c97ce
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487110"
---
# <a name="install-python-packages-with-sqlmlutils"></a>Installer des packages Python avec sqlmlutils

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article décrit comment utiliser les fonctions du package [**sqlmlutils**](https://github.com/Microsoft/sqlmlutils) pour installer de nouveaux packages Python sur une instance de SQL Server Machine Learning Services. Les packages que vous installez peuvent être utilisés dans des scripts Python exécutés dans la base de données à l’aide de l’instruction T-SQL [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Pour plus d’informations sur l’emplacement des packages et les chemins d’installation, consultez [Obtenir des informations sur les packages Python](../package-management/python-package-information.md).

> [!NOTE]
> La commande Python standard `pip install` n’est pas recommandée pour l’ajout de packages Python sur SQL Server 2019. Au lieu de cela, utilisez **sqlmlutils** comme décrit dans cet article.

## <a name="prerequisites"></a>Prérequis

+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) doit être installé avec l’option de langage Python.

+ Installez [Python](https://www.python.org/) sur l’ordinateur client que vous utilisez pour vous connecter à SQL Server. Vous pouvez également avoir besoin d’un environnement de développement Python, par exemple [Visual Studio Code](https://code.visualstudio.com/download) avec [l’extension Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python). 

+ Installez [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) ou [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) sur l’ordinateur client que vous utilisez pour vous connecter à SQL Server. Vous pouvez utiliser d’autres outils de gestion de base de données ou de requête, mais cet article part du principe que vous utilisez Azure Data Studio ou SSMS.

### <a name="other-considerations"></a>Autres considérations

+ Les packages doivent être compatibles avec la version de Python que vous utilisez. Pour savoir quelle version de Python est fournie avec chaque version de SQL Server, consultez les [informations sur les versions de Python et de R dans Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../sql-server-machine-learning-services.md#versions)

+ La bibliothèque de packages Python se trouve dans le dossier Program Files de votre instance SQL Server et, par défaut, l’installation dans ce dossier requiert des autorisations d’administrateur. Pour plus d’informations, consultez [Emplacement de la bibliothèque de packages](../package-management/python-package-information.md#default-python-library-location).

+ L’installation du package se fait par instance. Si vous avez plusieurs instances de Machine Learning Services, vous devez ajouter le package à chacune d’entre elles.

+ Avant d’ajouter un package, déterminez si le package est adapté à l’environnement SQL Server.

  + Nous vous recommandons d’utiliser Python dans la base de données pour les tâches qui bénéficient d’une intégration étroite avec le moteur de base de données, par exemple l’apprentissage automatique, plutôt que pour les tâches qui interrogent simplement la base de données.

  + Si vous ajoutez des packages qui placent trop de pression de calcul sur le serveur, les performances en seront affectées.

  + Dans un environnement SQL Server renforcé, vous souhaiterez peut-être éviter ce qui suit :
    + Les packages qui nécessitent un accès réseau
    + Les packages qui nécessitent un accès au système de fichiers élevé
    + Les packages utilisés pour le développement Web ou d’autres tâches qui ne bénéficient pas de l’exécution dans SQL Server

## <a name="install-sqlmlutils-on-the-client-computer"></a>Installer sqlmlutils sur l’ordinateur client

Pour utiliser **sqlmlutils**, vous devez d’abord l’installer sur l’ordinateur client que vous utilisez pour vous connecter à SQL Server. Vérifiez que vous avez installé `pip` ; consultez [Installation de PIP](https://pip.pypa.io/en/stable/installing/) pour plus d’informations.

1. Téléchargez le dernier fichier zip **sqlmlutils** à partir de https://github.com/Microsoft/sqlmlutils/tree/master/Python/dist sur l’ordinateur client. Ne décompressez pas le fichier.

1. Ouvrez une **invite de commandes** et exécutez les commandes suivantes pour installer le package **sqlmlutils**. Remplacez le chemin d’accès complet par le fichier zip **sqlmlutils** que vous avez téléchargé (cet exemple suppose que le fichier téléchargé est `c:\temp\sqlmlutils-1.0.0.zip`).

   ```console
   pip install "pymssql<3.0"
   pip install --upgrade --upgrade-strategy only-if-needed c:\temp\sqlmlutils-1.0.0.zip
   ```

## <a name="add-a-python-package-on-sql-server"></a>Ajouter un package Python sur SQL Server

Dans l’exemple suivant, vous allez ajouter le package [text-tools](https://pypi.org/project/text-tools/) à SQL Server.

### <a name="add-the-package-online"></a>Ajouter le package en ligne

Si l’ordinateur client que vous utilisez pour vous connecter à SQL Server a accès à Internet, vous pouvez utiliser **sqlmlutils** pour rechercher le package **text-tools** et toutes les dépendances sur Internet, puis installer le package sur une instance SQL Server distante.

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

1. Sur l’ordinateur client, ouvrez **Python** ou un environnement Python.

1. Utilisez les commandes suivantes pour installer le package **text-tools**. Remplacez vos propres informations de connexion de base de données SQL Server (si vous utilisez l’authentification Windows, vous n’avez pas besoin des paramètres `uid` et `pwd`).

::: moniker-end

::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

1. Sur l’ordinateur client, ouvrez **Python** ou un environnement Python.

1. Utilisez les commandes suivantes pour installer le package **text-tools**. Remplacez les valeurs existantes par vos propres informations de connexion à la base de données SQL Server.

::: moniker-end

   ```python
   import sqlmlutils
   connection = sqlmlutils.ConnectionInfo(server="server", database="database", uid="username", pwd="password")
   sqlmlutils.SQLPackageManager(connection).install("text-tools")
   ```

### <a name="add-the-package-offline"></a>Ajouter le package hors connexion

Si l’ordinateur client que vous utilisez pour vous connecter à SQL Server n’est pas connecté à Internet, vous pouvez utiliser **pip** sur un ordinateur disposant d’un accès à Internet pour télécharger le package et tous les packages dépendants dans un dossier local. Vous copiez ensuite le dossier sur l’ordinateur client sur lequel vous pouvez installer le package hors connexion.

#### <a name="on-a-computer-with-internet-access"></a>Sur un ordinateur connecté à Internet

1. Ouvrez une **invite de commandes** et exécutez la commande suivante pour créer un dossier local qui contient le package **text-tools**. Cet exemple crée le dossier `c:\temp\text-tools`.

   ```console
   pip download text-tools -d c:\temp\text-tools
   ```

1. Copiez le dossier `text-tools` sur l’ordinateur client. L’exemple suivant suppose que vous l’avez copié dans `c:\temp\packages\text-tools`.

#### <a name="on-the-client-computer"></a>Sur l’ordinateur client

Utilisez **sqlmlutils** pour installer chaque package (fichier WHL) que vous trouvez dans le dossier local créé par **pip**. Peu importe l’ordre dans lequel vous installez les packages.

Dans cet exemple, **text-tools** n’a pas de dépendances. Il n’y a donc qu’un seul fichier du dossier `text-tools` que vous pouvez installer. En revanche, un package tel que **scikit-plot** a 11 dépendances. Par conséquent, vous trouverez 12 fichiers dans le dossier (le package **scikit-plot** et les 11 packages dépendants) et vous devez tous les installer.

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

Exécutez le script Python suivant. Remplacez le chemin du fichier, le nom du package et vos propres informations de connexion de base de données SQL Server (si vous utilisez l’authentification Windows, vous n’avez pas besoin des paramètres `uid` et `pwd`). Répétez l’instruction `sqlmlutils.SQLPackageManager` pour chaque fichier de package dans le dossier.

::: moniker-end

::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"

Exécutez le script Python suivant. Remplacez le chemin du fichier, le nom du package et vos propres informations de connexion de base de données SQL Server. Répétez l’instruction `sqlmlutils.SQLPackageManager` pour chaque fichier de package dans le dossier.

::: moniker-end

```python
import sqlmlutils
connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase", uid="username", pwd="password"))
sqlmlutils.SQLPackageManager(connection).install("text_tools-1.0.0-py3-none-any.whl")
```

## <a name="use-the-package-in-sql-server"></a>Utiliser le package dans SQL Server

Vous pouvez maintenant utiliser le package dans un script Python dans SQL Server. Par exemple :

```python
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
from text_tools.finders import find_best_string
corpus = "Lorem Ipsum text"
query = "Ipsum"
first_match = find_best_string(query, corpus)
print(first_match)
  '
```

## <a name="remove-the-package-from-sql-server"></a>Supprimer le package de SQL Server

Si vous souhaitez supprimer le package **text-tools**, utilisez la commande Python suivante sur l’ordinateur client, en utilisant la même variable de connexion que celle que vous avez définie précédemment.

```python
sqlmlutils.SQLPackageManager(connection).uninstall("text-tools")
```

## <a name="see-also"></a>Voir aussi

+ Pour afficher des informations sur les packages Python installés dans SQL Server Machine Learning Services, consultez [Obtenir des informations sur les packages Python](../package-management/python-package-information.md).

+ Pour plus d’informations sur l’installation de packages R dans SQL Server Machine Learning Services, consultez [Installer de nouveaux packages R sur SQL Server](install-additional-r-packages-on-sql-server.md).
