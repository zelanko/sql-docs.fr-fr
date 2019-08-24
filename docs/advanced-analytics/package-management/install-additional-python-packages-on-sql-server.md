---
title: Installer des packages Python avec PIP
description: Découvrez comment utiliser le PIP Python pour installer de nouveaux packages Python sur une instance de SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 50463f27f37f9da410d1598002989f7cea6d8158
ms.sourcegitcommit: 01c8df19cdf0670c02c645ac7d8cc9720c5db084
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000776"
---
# <a name="install-python-packages-with-sqlmlutils"></a>Installer des packages Python avec sqlmlutils

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment utiliser les fonctions du package [**sqlmlutils**](https://github.com/Microsoft/sqlmlutils) pour installer de nouveaux packages python dans une instance de SQL Server machine learning services. Les packages que vous installez peuvent être utilisés dans les scripts Python exécutés dans la base de données à l’aide de l’instruction T-SQL [SP-Execute-External-script-Transact-SQL](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) .

Pour plus d’informations sur l’emplacement des packages et les chemins d’installation, consultez obtenir des informations sur les [packages python](../package-management/python-package-information.md).

> [!NOTE]
> La commande python `pip install` standard n’est pas recommandée pour l’ajout de packages Python sur SQL Server. Utilisez plutôt **sqlmlutils** comme décrit dans cet article.

## <a name="prerequisites"></a>Prérequis

+ [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) doit être installé avec l’option de langage Python.

+ Installez [python](https://www.python.org/) sur l’ordinateur client que vous utilisez pour vous connecter à SQL Server. Vous pouvez également avoir besoin d’un environnement de développement Python, par exemple [Visual Studio code](https://code.visualstudio.com/download) avec l' [extension Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python). 

+ Installez [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) ou [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) sur l’ordinateur client que vous utilisez pour vous connecter à SQL Server. Vous pouvez utiliser d’autres outils de gestion de base de données ou de requête, mais cet article suppose Azure Data Studio ou SSMS.

### <a name="other-considerations"></a>Autres points à considérer

+ Les packages doivent être conformes à python 3,5 et s’exécuter sur Windows.

+ La bibliothèque de packages Python se trouve dans le dossier Program Files de votre instance SQL Server et, par défaut, l’installation de dans ce dossier requiert des autorisations d’administrateur. Pour plus d’informations, consultez emplacement de la [bibliothèque de packages](../package-management/python-package-information.md#default-python-library-location).

+ L’installation du package est par instance. Si vous avez plusieurs instances de Machine Learning Services, vous devez ajouter le package à chacun d’eux.

+ Avant d’ajouter un package, déterminez si le package est adapté à l’environnement de SQL Server.

  + Nous vous recommandons d’utiliser python dans la base de données pour les tâches qui bénéficient d’une intégration étroite avec le moteur de base de données, par exemple Machine Learning, plutôt que des tâches qui interrogent simplement la base de données.

  + Si vous ajoutez des packages qui placent une pression de calcul trop importante sur le serveur, les performances en seront affectées.

  + Dans un environnement de SQL Server renforcé, vous souhaiterez peut-être éviter ce qui suit:
    + Packages qui nécessitent un accès réseau
    + Packages nécessitant un accès avec système de fichiers élevé
    + Packages utilisés pour le développement Web ou d’autres tâches qui ne bénéficient pas de l’exécution dans SQL Server

## <a name="install-sqlmlutils-on-the-client-computer"></a>Installer sqlmlutils sur l’ordinateur client

Pour utiliser **sqlmlutils**, vous devez d’abord l’installer sur l’ordinateur client que vous utilisez pour vous connecter à SQL Server.

1. Téléchargez le fichier zip **sqlmlutils** le plus https://github.com/Microsoft/sqlmlutils/tree/master/Python/dist récent à partir de sur l’ordinateur client. Ne Décompressez pas le fichier.

1. Ouvrez une **invite de commandes** et exécutez la commande suivante pour installer le package **sqlmlutils** . Remplacez le chemin d’accès complet au fichier zip **sqlmlutils** que vous avez téléchargé. cet exemple suppose que le `c:\temp\sqlmlutils_0.6.0.zip`fichier téléchargé est.

   ```console
   pip install --upgrade --upgrade-strategy only-if-needed c:\temp\sqlmlutils_0.6.0.zip
   ```

## <a name="add-a-python-package-on-sql-server"></a>Ajouter un package Python sur SQL Server

Dans l’exemple suivant, vous allez ajouter le package d' [outils de texte](https://pypi.org/project/text-tools/) à SQL Server.

### <a name="add-the-package-online"></a>Ajouter le package en ligne

Si l’ordinateur client que vous utilisez pour vous connecter à SQL Server a accès à Internet, vous pouvez utiliser **sqlmlutils** pour rechercher le package d' **outils de texte** et toutes les dépendances sur Internet, puis installer le package sur une instance de SQL Server à distance.

1. Sur l’ordinateur client, ouvrez **python** ou un environnement Python.

1. Utilisez les commandes suivantes pour installer le package d' **outils de texte** . Remplacez vos propres informations de connexion à la base de données SQL Server.

   ```python
   import sqlmlutils
   connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase", uid="yoursqluser", pwd="yoursqlpassword")
   sqlmlutils.SQLPackageManager(connection).install("text-tools")
   ```

### <a name="add-the-package-offline"></a>Ajouter le package hors connexion

Si l’ordinateur client que vous utilisez pour vous connecter à SQL Server ne dispose pas d’une connexion Internet, vous pouvez utiliser **PIP** sur un ordinateur disposant d’un accès à Internet pour télécharger le package et tous les packages dépendants dans un dossier local. Vous copiez ensuite le dossier sur l’ordinateur client sur lequel vous pouvez installer le package hors connexion.

#### <a name="on-a-computer-with-internet-access"></a>Sur un ordinateur connecté à Internet

1. Ouvrez une **invite de commandes** et exécutez la commande suivante pour créer un dossier local qui contient le package d' **outils de texte** . Cet exemple crée le dossier `c:\temp\text-tools`.

   ```command
   pip download text-tools -d c:\temp\text-tools
   ```

1. Copiez `text-tools` le dossier sur l’ordinateur client. L’exemple suivant suppose que vous l’avez copié `c:\temp\packages\text-tools`dans.

#### <a name="on-the-client-computer"></a>Sur l’ordinateur client

Utilisez **sqlmlutils** pour installer chaque package (fichier WHL) que vous trouvez dans le dossier local créé par le **PIP** . Peu importe l’ordre dans lequel vous installez les packages.

Dans cet exemple, les `text-tools` outils de texte n’ont pas de dépendances. il n’y a donc qu’un seul fichier à partir du dossier que vous pouvez installer. En revanche, un package tel que **scikit-Plot** a 11 dépendances. par conséquent, vous trouverez 12 fichiers dans le dossier (le package **scikit-Plot** et les 11 packages dépendants) et vous installerez chacun d’eux.

Exécutez le script Python suivant. Remplacez vos propres informations de connexion de base de données SQL Server, ainsi que le chemin d’accès et le nom de fichier réels du package. Répétez `sqlmlutils.SQLPackageManager` l’instruction pour chaque fichier de package dans le dossier.

```python
import sqlmlutils
connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase", uid="yoursqluser", pwd="yoursqlpassword")
sqlmlutils.SQLPackageManager(connection).install("c:/temp/packages/text-tools/text_tools-1.0.0-py3-none-any.whl")
```

## <a name="use-the-package-in-sql-server"></a>Utiliser le package dans SQL Server

Vous pouvez maintenant utiliser le package dans un script Python dans SQL Server. Exemple :

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

Si vous souhaitez supprimer le package d' **outils de texte** , utilisez la commande python suivante sur l’ordinateur client, en utilisant la même variable de connexion que celle que vous avez définie précédemment.

```python
sqlmlutils.SQLPackageManager(connection).uninstall("text-tools")
```

## <a name="see-also"></a>Voir aussi

+ Pour afficher des informations sur les packages python installés dans SQL Server Machine Learning Services, consultez [obtenir des informations](../package-management/python-package-information.md)sur les packages Python.

+ Pour plus d’informations sur l’installation de packages R dans SQL Server Machine Learning Services, consultez [installer de nouveaux packages r sur SQL Server](../r/install-additional-r-packages-on-sql-server.md).
