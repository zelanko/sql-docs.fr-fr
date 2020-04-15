---
title: Obtenir des informations sur les packages Python
description: Découvrez comment obtenir des informations sur les packages Python ayant été installés, y compris les versions et les emplacements d’installation, sur SQL Server Machine Learning Services.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 173be52a343ad6f19395d6c532124ddd837ed70f
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "81118002"
---
# <a name="get-python-package-information"></a>Obtenir des informations sur les packages Python

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article vous explique comment obtenir des informations sur les packages Python ayant été installés, y compris les versions et les emplacements d’installation, sur SQL Server Machine Learning Services. Les exemples de scripts Python vous montrent comment répertorier des informations de package telles que le chemin d’installation et la version.

## <a name="default-python-library-location"></a>Emplacement par défaut de la bibliothèque Python

Lorsque vous installez Machine Learning avec SQL Server, une seule bibliothèque de packages est créée au niveau de l’instance pour chaque langage que vous installez. Sur Windows, la bibliothèque d’instances est un dossier sécurisé enregistré avec SQL Server.

Tous les scripts ou les codes qui s’exécutent dans la base de données sur SQL Server doivent charger les fonctions à partir de la bibliothèque d’instances. SQL Server ne peut pas accéder aux packages installés dans d’autres bibliothèques. Cela s’applique également aux clients distants : tout code Python qui s’exécute dans le contexte de calcul du serveur peut uniquement utiliser des packages installés dans la bibliothèque d’instances.
Pour protéger les ressources du serveur, la bibliothèque d’instances par défaut ne peut être modifiée que par un administrateur de l’ordinateur.

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Le chemin d’accès par défaut aux éléments binaires pour Python est :

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
Le chemin d’accès par défaut aux éléments binaires pour Python est :

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

Cela nécessite d’utiliser l’instance SQL par défaut, MSSQLSERVER. Si SQL Server est installé en tant qu’instance nommée définie par l’utilisateur, le nom donné est utilisé à la place.

Exécutez l’instruction suivante pour déterminer la bibliothèque par défaut de l’instance actuelle. Cet exemple renvoie la liste des dossiers inclus dans la variable `sys.path` Python. La liste comprend le répertoire actuel et le chemin d’accès de la bibliothèque standard.

```sql
EXECUTE sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

Pour en savoir plus sur la variable `sys.path` et sur la façon dont elle est utilisée pour définir le chemin de recherche de l’interpréteur pour les modules, consultez la section [Chemin de recherche du module](https://docs.python.org/2/tutorial/modules.html#the-module-search-path).

## <a name="default-python-packages"></a>Packages Python par défaut

Les packages Python suivants sont installés avec SQL Server Machine Learning Services lorsque vous sélectionnez la fonctionnalité Python au moment de l’installation.

| . | Version |  Description |
| ---------|---------|--------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2 | Utilisé pour les contextes de calcul distants, la diffusion en continu, l’exécution parallèle des fonctions rx pour l’importation et la transformation des données, la modélisation, la visualisation et l’analyse. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2 | Ajoute des algorithmes d’apprentissage automatique dans Python. |

### <a name="component-upgrades"></a>Mise à niveau des composants

Par défaut, les packages Python sont actualisés grâce aux Service Packs et aux mises à jour cumulatives. Les packages supplémentaires et les mises à niveau de version complètes des composants de base de Python ne sont possibles que par le biais de mises à niveau de produit ou par liaison de la prise en charge de Python avec Microsoft Machine Learning Server.

Pour plus d’informations, consultez la section [Mettre à niveau les composants R et Python dans SQL Server](../install/upgrade-r-and-python.md).

## <a name="default-open-source-python-packages"></a>Packages Python open source par défaut

Lorsque vous sélectionnez l’option de langage Python au cours de l’installation, la distribution Anaconda 4.2 (sur Python 3.5) est installée. En plus des bibliothèques de code Python, l’installation standard comprend des exemples de données, des tests unitaires et des exemples de scripts.

> [!IMPORTANT]
> Ne remplacez jamais manuellement la version de Python installée par le programme de SQL Server par des versions plus récentes obtenues sur le Web. Les packages Microsoft Python sont basés sur des versions spécifiques d’Anaconda. Vous risquez de les déstabiliser si vous modifiez votre installation.

## <a name="list-all-installed-python-packages"></a>Répertorier tous les packages Python ayant été installés

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

## <a name="find-a-single-python-package"></a>Rechercher un seul package Python

Si vous avez installé un package Python et que vous souhaitez vous assurer qu’il est disponible pour une instance SQL Server donnée, vous pouvez exécuter une procédure stockée pour charger le package et renvoyer des messages.

Par exemple, le code suivant recherche le package `scikit-learn`.
Si le package est trouvé, le code renvoie le message « le package scikit-learn est installé ».

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

L’exemple suivant renvoie les versions du package revoscalepy et de Python.

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

::: moniker range="<=sql-server-2017||=sqlallproducts-allversions"
+ [Installer des packages avec des outils Python](install-python-packages-standard-tools.md)
::: moniker-end
::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
+ [Installer de nouveaux packages Python avec sqlmlutils](install-additional-r-packages-on-sql-server.md)
::: moniker-end