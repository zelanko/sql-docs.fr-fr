---
title: Recevoir des informations sur les packages R et Python
description: Déterminez la version du package R et Python, vérifiez l’installation et procurez-vous une liste des packages installés sur SQL Server R Services ou Machine Learning Services.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ff4d0839cfdf24b1b43fe9d5a371092713bc63cf
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715795"
---
#  <a name="get-r-and-python-package-information"></a>Recevoir des informations sur les packages R et Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Parfois, lorsque vous travaillez avec plusieurs environnements ou installations de R ou python, vous devez vérifier que le code que vous exécutez utilise l’environnement attendu pour Python ou l’espace de travail correct pour R. Par exemple, si vous avez [mis à niveau r ou python](../install/upgrade-r-and-python.md), le chemin d’accès à la bibliothèque r se trouve peut-être dans un dossier différent de celui par défaut. En outre, si vous installez R client ou une instance du serveur autonome, vous pouvez avoir plusieurs bibliothèques R sur votre ordinateur.

Les exemples de scripts R et Python de cet article montrent comment récupérer le chemin d’accès et la version des packages utilisés par SQL Server.

## <a name="get-the-r-library-location"></a>Obtient l’emplacement de la bibliothèque R

Pour toute version de SQL Server, exécutez l’instruction suivante pour vérifier la bibliothèque de packages R par défaut pour l’instance actuelle:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Si vous le souhaitez, vous pouvez utiliser [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) dans les versions plus récentes de RevoScaleR dans SQL Server machine learning services ou [r services mis à niveau r vers au moins RevoScaleR 9.0.1](../install/upgrade-r-and-python.md). Cette procédure stockée retourne le chemin d’accès de la bibliothèque d’instances et la version de RevoScaleR utilisée par SQL Server:

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
> La fonction [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) ne peut être exécutée que sur l’ordinateur local. La fonction ne peut pas retourner de chemins d’accès de bibliothèque pour les connexions à distance.

**Résultats**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.3.0'
```

## <a name="get-the-python-library-location"></a>Obtient l’emplacement de la bibliothèque python

Pour **python**, exécutez l’instruction suivante pour vérifier la bibliothèque par défaut de l’instance actuelle. Cet exemple retourne la liste des dossiers inclus dans la variable `sys.path` Python. La liste comprend le répertoire actif et le chemin d’accès de la bibliothèque standard.

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

Pour plus d’informations sur la `sys.path` variable et sur la façon dont elle est utilisée pour définir le chemin de recherche de l’interpréteur pour les modules, consultez la [documentation python](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)

## <a name="list-all-packages"></a>Répertorier tous les packages

Il existe plusieurs façons d’obtenir la liste complète des packages actuellement installés. L’un des avantages de l’exécution des commandes de liste de packages à partir de sp_execute_external_script est que vous êtes sûr d’avoir des packages installés dans la bibliothèque d’instances.

### <a name="r"></a>R

L’exemple suivant utilise la fonction `installed.packages()` R dans une [!INCLUDE[tsql](../../includes/tsql-md.md)] procédure stockée pour obtenir une matrice des packages qui ont été installés dans la bibliothèque R_SERVICES pour l’instance actuelle. Ce script retourne les champs nom et version du package dans le fichier de DESCRIPTION, seul le nom est retourné.

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

Pour plus d’informations sur les champs facultatifs et par défaut du champ DESCRIPTION du package [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)R, consultez.

### <a name="python"></a>Python

Le `pip` module est installé par défaut et prend en charge de nombreuses opérations pour répertorier les packages installés, en plus de ceux pris en charge par la norme Python. Vous pouvez exécuter `pip` à partir d’une invite de commandes Python, bien entendu, mais vous pouvez également appeler certaines `sp_execute_external_script`fonctions PIP à partir de.

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

Lors de `pip` l’exécution à partir de la ligne de commande, il existe de nombreuses autres fonctions utiles: récupère tous `pip freeze` les packages installés, tandis que répertorie les packages installés par `pip`, et ne répertorie pas les packages qui se PIP lui-même. `pip list` dépend de. Vous pouvez également utiliser `pip freeze` pour générer un fichier de dépendance.

## <a name="find-a-single-package"></a>Rechercher un package unique

Si vous avez installé un package et que vous souhaitez vous assurer qu’il est disponible pour une instance de SQL Server particulière, vous pouvez exécuter l’appel de procédure stockée suivant pour charger le package et retourner uniquement des messages.

### <a name="r"></a>R

Cet exemple recherche et charge la bibliothèque RevoScaleR, si elle est disponible.

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("RevoScaleR")'
GO
```

+ Si le package est trouvé, un message est retourné: «Commandes terminées avec succès».

+ Si le package est introuvable ou ne peut pas être chargé, vous recevez une erreur contenant le texte: «il n’y a aucun package appelé «MissingPackageName»»

### <a name="python"></a>Python

La vérification équivalente de Python peut être effectuée à partir de l’interpréteur `pip` de commandes Python, à l’aide `conda` des commandes ou. Vous pouvez également exécuter cette instruction dans une procédure stockée:

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

## <a name="get-package-version"></a>Obtient la version du package

Vous pouvez récupérer des informations sur la version des packages R et Python à l’aide de Management Studio.

### <a name="r-package-version"></a>Version du package R

Cette instruction retourne la version du package RevoScaleR et la version R de base.

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