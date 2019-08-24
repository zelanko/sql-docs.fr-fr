---
title: Obtenir des informations sur les packages Python
description: Découvrez comment obtenir des informations sur les packages python installés, y compris les versions et les emplacements d’installation, sur SQL Server Machine Learning Services.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1aa12da4a138ea8f292fa8b64db00456d3c35fe3
ms.sourcegitcommit: 01c8df19cdf0670c02c645ac7d8cc9720c5db084
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000449"
---
# <a name="get-python-package-information"></a>Obtenir des informations sur les packages Python

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment obtenir des informations sur les packages python installés, y compris les versions et les emplacements d’installation, sur SQL Server Machine Learning Services. Les exemples de scripts Python vous montrent comment répertorier des informations de package telles que le chemin d’installation et la version.

## <a name="default-python-library-location"></a>Emplacement par défaut de la bibliothèque python

Lorsque vous installez Machine Learning avec SQL Server, une seule bibliothèque de packages est créée au niveau de l’instance pour chaque langue que vous installez. Sur Windows, la bibliothèque d’instances est un dossier sécurisé enregistré avec SQL Server.

Tout script ou code qui s’exécute dans la base de données sur SQL Server doit charger des fonctions à partir de la bibliothèque d’instances. SQL Server ne pouvez pas accéder aux packages installés dans d’autres bibliothèques. Cela s’applique également aux clients distants: tout code python s’exécutant dans le contexte de calcul du serveur ne peut utiliser que des packages installés dans la bibliothèque d’instances.
Pour protéger les ressources du serveur, la bibliothèque d’instances par défaut ne peut être modifiée que par un administrateur de l’ordinateur.

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Le chemin d’accès par défaut des binaires pour Python est le suivant:

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
Le chemin d’accès par défaut des binaires pour Python est le suivant:

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

Cela suppose l’instance SQL par défaut, MSSQLSERVER. Si SQL Server est installé en tant qu’instance nommée définie par l’utilisateur, le nom donné est utilisé à la place.

Exécutez l’instruction suivante pour vérifier la bibliothèque par défaut de l’instance actuelle. Cet exemple retourne la liste des dossiers inclus dans la variable `sys.path` Python. La liste comprend le répertoire actif et le chemin d’accès de la bibliothèque standard.

```sql
EXECUTE sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

Pour plus d’informations sur la `sys.path` variable et sur la façon dont elle est utilisée pour définir le chemin de recherche de l’interpréteur pour les modules, consultez [le chemin de recherche du module](https://docs.python.org/2/tutorial/modules.html#the-module-search-path).

## <a name="default-python-packages"></a>Packages python par défaut

Les packages python suivants sont installés avec SQL Server Machine Learning Services lorsque vous sélectionnez la fonctionnalité python lors de l’installation.

| . | Version |  Description |
| ---------|---------|--------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9,2 | Utilisé pour les contextes de calcul distants, la diffusion en continu et l’exécution parallèle des fonctions RX pour l’importation et la transformation des données, la modélisation, la visualisation et l’analyse. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9,2 | Ajoute des algorithmes de Machine Learning dans Python. |

### <a name="component-upgrades"></a>Mises à niveau de composants

Par défaut, les packages Python sont actualisés par le biais des service packs et des mises à jour cumulatives. Les packages supplémentaires et les mises à niveau de version complète des composants de base Python sont possibles uniquement par le biais de mises à niveau de produit ou par liaison de la prise en charge de Python à Microsoft Machine Learning Server.

Pour plus d’informations, consultez [mettre à niveau les composants R et Python dans SQL Server](../install/upgrade-r-and-python.md).

## <a name="default-open-source-python-packages"></a>Packages python Open source par défaut

Lorsque vous sélectionnez l’option de langage Python au cours de l’installation, la distribution Anaconda 4,2 (sur Python 3,5) est installée. En plus des bibliothèques de code Python, l’installation standard comprend des exemples de données, des tests unitaires et des exemples de scripts.

> [!IMPORTANT]
> Vous ne devez jamais remplacer manuellement la version de Python installée par SQL Server installation avec des versions plus récentes sur le Web. Les packages Microsoft Python sont basés sur des versions spécifiques de Anaconda. La modification de votre installation pourrait le déstabiliser.

## <a name="list-all-installed-python-packages"></a>Répertorier tous les packages python installés

L’exemple de script suivant affiche une liste des packages installés et leurs versions.

```sql
EXECUTE sp_execute_external_script 
  @language = N'Python', 
  @script = N'
import pkg_resources
import pandas as pd
installed_packages = pkg_resources.working_set
installed_packages_list = sorted(["%s==%s" % (i.key, i.version) for i in installed_packages])
df = pd.DataFrame(installed_packages_list)
OutputDataSet = df
  '
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

## <a name="find-a-single-python-package"></a>Rechercher un package Python unique

Si vous avez installé un package Python et que vous souhaitez vous assurer qu’il est disponible pour une instance de SQL Server particulière, vous pouvez exécuter une procédure stockée pour charger le package et renvoyer des messages.

Par exemple, le code suivant recherche le `scikit-learn` package.
Si le package est trouvé, le code retourne le message «le package scikit-Learn est installé».

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
import pkg_resources
pckg_name = "scikit-learn"
pckgs = pandas.DataFrame([(i.key) for i in pkg_resources.working_set], columns = ["key"])
installed_pckg = pckgs.query(''key == @pckg_name'')
print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")
  '
```

<a name="get-package-vers"></a>

L’exemple suivant retourne les versions du package revoscalepy et de Python.

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
import revoscalepy
import sys
print(revoscalepy.__version__)
print(sys.version)
  '
```

## <a name="next-steps"></a>Étapes suivantes

+ [Installer de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Récupérer les informations du package R](r-package-information.md)
+ [Installer de nouveaux packages R](../r/install-additional-r-packages-on-sql-server.md)
+ [Didacticiels R et Python](../tutorials/machine-learning-services-tutorials.md)
