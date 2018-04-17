---
title: Affichage R ou des packages Python installées sur SQL Server | Documents Microsoft
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 227da5cd4ba9ae91019556cc9bac00aee770a525
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="viewing-r-or-python-packages-installed-on-sql-server"></a>Affichage R ou des packages Python installées sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Si vous avez installé plusieurs environnements Python ou utilisez plusieurs outils R, il est facile à installer un package vers la bibliothèque incorrecte ou d’un environnement et alors en mesure de le retrouver ultérieurement. 

Cet article fournit des requêtes que vous pouvez utiliser pour déterminer votre version actuelle et pour répertorier les packages qui sont installés dans l’environnement actuel de SQL Server.

## <a name="verify-the-current-default-library"></a>Vérifiez que la bibliothèque par défaut en cours

Pour **R** dans SQL Server, exécutez l’instruction suivante pour vérifier que la bibliothèque par défaut pour l’instance actuelle :

```sql
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Pour **Python** dans SQL Server, exécutez l’instruction suivante pour vérifier que la bibliothèque par défaut pour l’instance actuelle :

```sql
EXEC sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

## <a name="generate-a-package-list-using-a-stored-procedure"></a>Générer une liste de packages à l’aide d’une procédure stockée

Il existe plusieurs méthodes que vous pouvez obtenir une liste complète des packages actuellement installés. L’un des avantages de l’exécution des commandes de liste de package à partir de sp_execute_external_script sont que vous avez la garantie pour obtenir les packages installés dans la bibliothèque de l’instance.

### <a name="r"></a>R

L’exemple suivant utilise la fonction R `installed.packages()` dans un [!INCLUDE [tsql](..\..\includes\tsql-md.md)] procédure stockée pour obtenir une matrice des packages qui ont été installés dans la bibliothèque R_SERVICES pour l’instance actuelle. Pour éviter d’analyser les champs du fichier DESCRIPTION, seul le nom est retourné.

```SQL
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
NameOnly <- packagematrix[,1];
OutputDataSet <- as.data.frame(NameOnly);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250) ))
```

Pour plus d’informations sur le paramètre facultatif et des champs par défaut pour le champ de DESCRIPTION du package R, consultez [ https://cran.r-project.org ](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

### <a name="python"></a>Python

Le `pip` module est installé par défaut et prend en charge de nombreuses opérations pour les packages de liste installé, en plus de ceux pris en charge par Python standard. Vous pouvez exécuter `pip` à partir d’une Python invite de commandes, bien entendu, mais vous pouvez également appeler certaines fonctions pip de `sp_execute_external_script`.

```sql
execute sp_execute_external_script 
@language = N'Python', 
@script = N'
import pip
import pandas as pd
installed_packages = pip.get_installed_distributions()
installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
     for i in installed_packages])
df = pd.DataFrame(installed_packages_list)
OutputDataSet = df
'
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

Lors de l’exécution `pip` à partir de la ligne de commande, il existe de nombreuses autres fonctions utiles : `pip list` Obtient tous les packages qui sont installés, tandis que `pip freeze` répertorie les packages installés par `pip`et ne répertorie pas les packages qui lui-même pip dépend. Vous pouvez également utiliser `pip freeze` pour générer un fichier de dépendance.

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>Vérifiez si un package est installé avec une instance

Si vous avez installé un package et que vous souhaitez vous assurer qu’il est disponible pour une instance particulière de SQL Server, vous pouvez exécuter l’appel de procédure stockée suivante pour charger le package et de retourner uniquement les messages.

### <a name="r"></a>R

Cet exemple recherche et charge la bibliothèque RevoScaleR, s’il est disponible.

```sql
EXEC sp_execute_external_script  @language =N'R',
@script=N'require("RevoScaleR")'
GO
```

+ Si le package est trouvé, un message est retourné : « Commandes exécutée avec succès. »

+ Si le package ne peut pas être situé ou chargé, vous obtenez une erreur qui contient le texte : « il n’existe aucun package appelé 'MissingPackageName' »

### <a name="python"></a>Python

La vérification équivalente pour Python peut être effectuée à partir de Python shell, à l’aide de `conda` ou `pip` commandes. Vous pouvez également exécuter cette instruction dans une procédure stockée :

```sql
exec sp_execute_external_script
       @language = N'Python'
       , @script = N'
import pip
import pkg_resources
pckg_name = "revoscalepy"
pckgs = pandas.DataFrame([(i.key) for i in pip.get_installed_distributions()], columns = ["key"])
installed_pckg = pckgs.query(''key == @pckg_name'')
print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")
```

## <a name="view-installed-packages-using-a-utility-or-ide"></a>Afficher les packages installés à l’aide des utilitaires ou IDE

La plupart des outils de développement fournissent un Explorateur d’objets ou une liste des packages installés ou chargés dans l’environnement ou d’espace de travail actuel. Cette section fournit des conseils courts pour l’utilisation des outils courants de R ou Python.

### <a name="r-tools"></a>Outils R

Il existe plusieurs façons d’obtenir la liste des packages installés ou chargés à l’aide des utilitaires de R. 

+ À partir d’un utilitaire R local, utilisez une fonction R de base, telles que `installed.packages()`, qui est inclus dans le `utils` package. Pour obtenir une liste est correcte pour une instance, vous devez spécifier le chemin d’accès de la bibliothèque de manière explicite, ou utiliser les outils R associés à la bibliothèque de l’instance.

### <a name="python-tools"></a>Outils Python

Extensions de Python pour Visual Studio rendent très facile d’afficher les packages installés dans l’environnement actuel, ou dans d’autres environnements virtuels répertoriés dans l’IDE. Vous pouvez configurer plusieurs environnements, choisissez un environnement à partir d’une liste et afficher les packages ou installez de nouveaux packages de cet environnement.

+ [Environnements Python](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio)

Code Visual Studio est un éditeur gratuit qui prend en charge de Python, avec plusieurs linters Python disponibles. Bien que le Code de Visual Studio ne fournit pas d’un navigateur de package comme celle de Visual Studio, il prend en charge la configuration et le basculement entre plusieurs environnements.

+ [Python dans le Code de Visual Studio](https://code.visualstudio.com/docs/languages/python)

Une configuration supplémentaire peut-être être nécessaires pour exécuter **revoscalepy** commandes à partir d’un client distant :

+ [Installer localement des interpréteur et des packages Python personnalisés sur Windows](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)

Ce blog fournit des conseils utiles sur la configuration d’autres environnements Python, y compris PyCharm, pour travailler avec **revoscalepy**.

+ [Prise en main les Services Web Python à l’aide du serveur de Machine Learning](https://blogs.msdn.microsoft.com/mlserver/2017/12/13/getting-started-with-python-web-services-using-machine-learning-server/)

## <a name="use-functions-from-machine-learning-server"></a>Utiliser des fonctions à partir du serveur de Machine Learning

Étant donné que les bibliothèques utilisées avec l’exécution de SQL Server prise en charge du code à partir d’un client distant, vous pouvez utiliser ces fonctions pour déterminer quels packages sont installés dans un environnement distant.

### <a name="revoscaler"></a>RevoScaleR

Si vous travaillez dans un client distant et que vous n’avez pas accès au serveur, vous pouvez toujours obtenir une liste des packages qui sont installés sur le serveur SQL Server, à l’aide de fonctions RevoScaleR. Vous spécifiez le serveur SQL Server en tant que contexte de calcul, ce qui nécessite que vous êtes autorisé à se connecter au serveur. 

+ [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage) recherche le chemin d’accès d’un package dans le contexte de calcul à distance.

+ [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages) Obtient des informations sur les packages installés dans un contexte de calcul.

Par exemple, exécutez le code R suivant pour obtenir la liste des packages disponibles dans le contexte de calcul de SQL Server spécifié.

```R
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```

L’exemple suivant obtient l’emplacement de la bibliothèque de RevoScaleR dans le contexte de calcul local et la version du package.

```R
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

### <a name="revoscalepy"></a>revoscalepy

Fonctions similaires à ceux de RevoScaleR ne sont pas disponibles pour l’instant. Rechercher dans une version ultérieure de **revoscalepy**.

## <a name="get-library-location-and-version"></a>Obtenir la version et l’emplacement de la bibliothèque

Parfois, lorsque vous travaillez avec plusieurs environnements ou les installations de R ou Python, vous devez vérifier que le code que vous utilisez est à l’aide de l’environnement approprié pour Python ou que l’espace de travail correct pour R.

Par exemple, si vous avez mis à niveau les composants à l’aide de la liaison d’apprentissage automatique, le chemin d’accès à la bibliothèque R peut être dans un dossier autre que celui de la valeur par défaut. En outre, si vous installez R ou une instance du serveur autonome, vous pouvez avoir plusieurs bibliothèques R sur votre ordinateur.

Ces exemples montrent comment obtenir le chemin d’accès et la version de la bibliothèque qui est utilisée par SQL Server.

### <a name="r"></a>R

Cette procédure stockée retourne le chemin d’accès de la bibliothèque de l’instance et la version du package RevoScaleR utilisé par SQL Server :

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> Le [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) fonction peut être exécutée uniquement sur l’ordinateur cible. La fonction ne peut pas retourner des chemins d’accès de bibliothèque pour les connexions distantes.

**Résultats**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```

### <a name="python"></a>Python

Cet exemple retourne la liste des dossiers inclus dans les Python `sys.path` variable. La liste inclut le répertoire actif et le chemin d’accès de la bibliothèque standard.

```sql
EXEC sp_execute_external_script
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

Pour plus d’informations sur la variable `sys.path` et la façon dont il est utilisé pour définir le chemin de recherche de l’interpréteur de modules, consultez la [documentation de Python](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)

