---
title: "Déterminer quels packages R sont installés sur SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 10/09/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 138368a3ca212cb4c176df57d78d02b6f41c4344
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="determine-which-r-packages-are-installed-on-sql-server"></a>Déterminer quels packages R sont installés sur SQL Server

Lorsque vous installez un apprentissage dans SQL Server avec l’option de langage R, le programme d’installation crée une bibliothèque de package de R associée à l’instance. Chaque instance possède une bibliothèque de package distinct. Bibliothèques de package sont **pas** partagé entre les instances, il est donc possible pour les packages différents doivent être installés sur des instances différentes.

Cet article décrit comment vous pouvez déterminer quels packages R sont installés pour une instance spécifique.

## <a name="generate-r-package-list-using-a-stored-procedure"></a>Générer la liste des packages R à l’aide d’une procédure stockée

L’exemple suivant utilise la fonction R `installed.packages()` dans un [!INCLUDE [tsql](..\..\includes\tsql-md.md)] procédure stockée pour obtenir une matrice des packages qui ont été installés dans la bibliothèque R_SERVICES pour l’instance actuelle. Pour éviter d’analyser les champs du fichier DESCRIPTION, seul le nom est retourné.

```SQL
EXECUTE sp_execute_external_script
@language=N'R'  
,@script = N'str(OutputDataSet);  
packagematrix <- installed.packages();  
NameOnly <- packagematrix[,1];  
OutputDataSet <- as.data.frame(NameOnly);'  
,@input_data_1 = N'SELECT 1 as col'  
WITH RESULT SETS ((PackageName nvarchar(250) ))  
```

Pour plus d’informations sur le paramètre facultatif et de champs par défaut pour le fichier de DESCRIPTION du package R, consultez [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>Vérifiez si un package est installé avec une instance

Si vous avez installé un package et que vous souhaitez vous assurer qu’il est disponible pour une instance particulière de SQL Server, vous pouvez exécuter l’appel de procédure stockée suivante pour charger le package et de retourner uniquement les messages.

```SQL
EXEC sp_execute_external_script  @language =N'R',
@script=N'library("RevoScaleR")'
GO
```

Cet exemple recherche et charge la bibliothèque de RevoScaleR.

+ Si le package est trouvé, le message retourné doit être quelque chose comme « Commandes exécutée avec succès. »

+ Si le package ne peut pas être situé ou chargé, vous obtenez ce type d’erreur : « une erreur de script externe s’est produite : erreur dans library("RevoScaleR") : il n’existe aucun package appelé RevoScaleR »

## <a name="get-a-list-of-installed-packages-using-r"></a>Obtenir la liste des packages installés à l’aide de R

Il existe différentes façons d’obtenir la liste des packages installés ou chargés à l’aide d’outils ou de fonctions R. De nombreux outils de développement R fournissent un explorateur d’objets ou une liste des packages installés ou chargés dans l’espace de travail R actuel.

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
## <a name="see-also"></a>Voir aussi

[Installer des packages R supplémentaires sur SQL Server](install-additional-r-packages-on-sql-server.md)

