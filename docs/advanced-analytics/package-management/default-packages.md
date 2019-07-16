---
title: Obtenir des informations de package R et Python - SQL Server Machine Learning Services
description: Déterminer la version du package R et Python, vérifier l’installation et obtenir la liste des packages installés sur SQL Server R Services ou des Services Machine Learning.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 961d55237af75c0ef169332068c91e7d2341a542
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962785"
---
#  <a name="get-r-and-python-package-information"></a>Obtenir des informations de package R et Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Parfois, lorsque vous travaillez avec plusieurs environnements ou les installations de R ou Python, vous devez vérifier que le code que vous exécutez est à l’aide de l’environnement attendu pour Python ou l’espace de travail correct pour R. Par exemple, si vous avez [mis à niveau R ou Python](../install/upgrade-r-and-python.md), le chemin d’accès à la bibliothèque R peut être dans un dossier autre que celui de la valeur par défaut. En outre, si vous installez R Client ou une instance du serveur autonome, vous pouvez avoir plusieurs bibliothèques R sur votre ordinateur.

Exemples de script R et Python de cet article vous montrent comment obtenir le chemin d’accès et la version des packages utilisés par SQL Server.

## <a name="get-the-r-library-location"></a>Obtenir l’emplacement de la bibliothèque R

Pour n’importe quelle version de SQL Server, exécutez l’instruction suivante pour vérifier que la bibliothèque de packages R par défaut pour l’instance actuelle :

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Si vous le souhaitez, vous pouvez utiliser [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) dans les versions plus récentes de RevoScaleR dans SQL Server 2017 Machine Learning Services ou [R Services mis à niveau R pour au moins RevoScaleR 9.0.1](../install/upgrade-r-and-python.md). Cette procédure stockée retourne le chemin d’accès de la bibliothèque de l’instance et la version de RevoScaleR utilisé par SQL Server :

```sql
EXECUTE sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> Le [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) fonction peut être exécutée uniquement sur l’ordinateur local. La fonction ne peut pas retourner des chemins d’accès de bibliothèque pour les connexions distantes.

**Résultats**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.3.0'
```

## <a name="get-the-python-library-location"></a>Obtenir l’emplacement de la bibliothèque Python

Pour **Python** dans SQL Server 2017, exécutez l’instruction suivante pour vérifier que la bibliothèque par défaut pour l’instance actuelle. Cet exemple retourne la liste des dossiers inclus dans les Python `sys.path` variable. La liste inclut le répertoire actif et le chemin d’accès de la bibliothèque standard.

```sql
EXECUTE sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

**Résultats**

```text
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\python35.zip
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\DLLs
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Sphinx-1.5.4-py3.5.egg
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Pythonwin
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\setuptools-27.2.0-py3.5.egg
```

Pour plus d’informations sur la variable `sys.path` et il est utilisé pour définir le chemin de recherche de l’interpréteur pour les modules, consultez la [documentation Python](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)

## <a name="list-all-packages"></a>Liste de tous les packages

Il existe plusieurs méthodes que vous pouvez obtenir une liste complète des packages actuellement installés. L’un des avantages de l’exécution des commandes de liste de package à partir de sp_execute_external_script sont que vous êtes assuré d’obtenir les packages installés dans la bibliothèque de l’instance.

### <a name="r"></a>R

L’exemple suivant utilise la fonction R `installed.packages()` dans un [!INCLUDE[tsql](../../includes/tsql-md.md)] procédure stockée pour obtenir une matrice des packages qui ont été installés dans la bibliothèque R_SERVICES de l’instance actuelle. Ce script retourne les champs nom et la version de package dans le fichier DESCRIPTION, seul le nom est retourné.

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
  @script = N'str(OutputDataSet);
  packagematrix <- installed.packages();
  Name <- packagematrix[,1];
  Version <- packagematrix[,3];
  OutputDataSet <- data.frame(Name, Version);',
  @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Pour plus d’informations sur le paramètre facultatif et des champs par défaut pour le champ de DESCRIPTION de package R, consultez [ https://cran.r-project.org ](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

### <a name="python"></a>Python

Le `pip` module est installé par défaut et prend en charge de nombreuses opérations pour les packages de liste installé, en plus de ceux pris en charge par Python standard. Vous pouvez exécuter `pip` à partir de Python invite de commandes, bien sûr, mais vous pouvez également appeler certaines fonctions pip à partir de `sp_execute_external_script`.

```sql
EXECUTE sp_execute_external_script 
  @language = N'Python', 
  @script = N'
  import pip
  import pandas as pd
  installed_packages = pip.get_installed_distributions()
  installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
     for i in installed_packages])
  df = pd.DataFrame(installed_packages_list)
  OutputDataSet = df'
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

Lors de l’exécution `pip` à partir de la ligne de commande, il existe de nombreuses autres fonctions utiles : `pip list` Obtient tous les packages qui sont installés, tandis que `pip freeze` répertorie les packages installés par `pip`et ne répertorier les packages pip lui-même dépend. Vous pouvez également utiliser `pip freeze` pour générer un fichier de dépendance.

## <a name="find-a-single-package"></a>Rechercher un package unique

Si vous avez installé un package et que vous souhaitez vous assurer qu’il est disponible à une instance particulière de SQL Server, vous pouvez exécuter l’appel de procédure stockée suivant pour charger le package et de retourner uniquement les messages.

### <a name="r"></a>R

Cet exemple recherche et charge la bibliothèque RevoScaleR, s’il est disponible.

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("RevoScaleR")'
GO
```

+ Si le package est trouvé, un message est retourné : « Commandes s’est terminées correctement ».

+ Si le package ne peut pas être localisé ou chargé, vous obtenez une erreur contenant le texte : « il n’existe aucun package appelé « MissingPackageName » »

### <a name="python"></a>Python

La vérification équivalente pour Python peut être effectuée à partir de Python à l’aide de la shell `conda` ou `pip` commandes. Vous pouvez également exécuter cette instruction dans une procédure stockée :

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
  import pip
  import pkg_resources
  pckg_name = "revoscalepy"
  pckgs = pandas.DataFrame([(i.key) for i in pip.get_installed_distributions()], columns = ["key"])
  installed_pckg = pckgs.query(''key == @pckg_name'')
  print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")'
```

<a name="get-package-vers"></a>

## <a name="get-package-version"></a>Obtenir la version du package

Vous pouvez obtenir R et Python empaqueter les informations de version à l’aide de Management Studio.

### <a name="r-package-version"></a>Version du package R

Cette instruction retourne la version du package RevoScaleR et la version de R de base.

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("RevoScaleR"))
print(packageDescription("base"))
'
```

### <a name="python-package-version"></a>Version du package Python

Cette instruction retourne la version du package revoscalepy et la version de Python.

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

+ [Installer de nouveaux packages R](../r/install-additional-r-packages-on-sql-server.md)
+ [Installer de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Didacticiels, exemples, solutions](../tutorials/machine-learning-services-tutorials.md)