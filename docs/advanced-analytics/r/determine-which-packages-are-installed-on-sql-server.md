---
title: "Déterminer quels packages R sont installés sur SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 5db9405b6ef2e7c1423fa2affe6ad8bca58e5d68
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2018
---
# <a name="determine-which-r-packages-are-installed-on-sql-server"></a>Déterminer quels packages R sont installés sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Lorsque vous installez un apprentissage dans SQL Server avec l’option de langage R, une bibliothèque de package de R est créée spécifiquement pour une utilisation par l’instance. Chaque instance sur le serveur possède sa propre bibliothèque de package. Bibliothèques de package ne peut pas être partagés entre les instances.

Cet article décrit comment vous pouvez déterminer quels packages R sont installés pour une instance spécifique de SQL Server.

## <a name="generate-r-package-list-using-a-stored-procedure"></a>Générer la liste des packages R à l’aide d’une procédure stockée

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

Pour plus d’informations sur le paramètre facultatif et des champs par défaut pour le champ de DESCRIPTION du package R, consultez [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>Vérifiez si un package est installé avec une instance

Si vous avez installé un package et que vous souhaitez vous assurer qu’il est disponible pour une instance particulière de SQL Server, vous pouvez exécuter l’appel de procédure stockée suivante pour charger le package et de retourner uniquement les messages. Cet exemple recherche et charge la bibliothèque RevoScaleR, s’il est disponible.

```sql
EXEC sp_execute_external_script  @language =N'R',
@script=N'library("RevoScaleR")'
GO
```

+ Si le package est trouvé, un message est retourné : « Commandes exécutée avec succès. »

+ Si le package ne peut pas être situé ou chargé, vous obtenez une erreur qui contient le texte : « il n’existe aucun package appelé 'MissingPackageName' »

## <a name="get-a-list-of-installed-packages-using-r"></a>Obtenir la liste des packages installés à l’aide de R

Il existe différentes façons d’obtenir la liste des packages installés ou chargés à l’aide d’outils ou de fonctions R. De nombreux outils de développement R fournissent un explorateur d’objets ou une liste des packages installés ou chargés dans l’espace de travail R actuel. Cette section fournit des commandes courtes que vous pouvez utiliser à partir de n’importe quelle ligne de commande R ou fournisseur de services\_exécuter\_externe\_script.

+ À partir d’un utilitaire R local, utilisez une fonction R de base, telles que `installed.packages()`, qui est inclus dans le `utils` package. Pour obtenir une liste est correcte pour une instance, vous devez spécifier le chemin d’accès de la bibliothèque de manière explicite, ou utiliser les outils R associés à la bibliothèque de l’instance.

+ Pour vérifier si un package dans un contexte de calcul spécifique, vous pouvez utiliser les fonctions suivantes à partir du package RevoScaleR. Ces fonctions vous aider à identifier les packages dans les contextes de calcul spécifié :

+ [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage)

+ [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages)

Par exemple, exécutez le code R suivant pour obtenir la liste des packages disponibles dans le contexte de calcul de SQL Server spécifié.

```r
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```

## <a name="get-library-location-and-version"></a>Obtenir la version et l’emplacement de la bibliothèque

L’exemple suivant obtient l’emplacement de la bibliothèque de RevoScaleR dans le contexte de calcul local et la version du package.

```r
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

## <a name="determine-path-of-library-used-by-sql-server"></a>Déterminer le chemin d’accès de bibliothèque utilisé par SQL Server

Si vous avez mis à niveau les composants à l’aide de la liaison d’apprentissage automatique, le chemin d’accès à la bibliothèque R peut changer. Dans ce cas, précédentes raccourcis vers les outils R peuvent faire référence à une version antérieure. Pour être sûr de la version du chemin d’accès et le package utilisé par SQL Server, vous pouvez exécuter une commande telle que les éléments suivants :

```sql
EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    sql_r_path <- rxSqlLibPaths("local")
      print(sql_r_path)
    version_info <-packageVersion("RevoScaleR")
      print(version_info)'
```

**Résultats**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```
## <a name="see-also"></a>Voir aussi

[Installer des packages R supplémentaires sur SQL Server](install-additional-r-packages-on-sql-server.md)
