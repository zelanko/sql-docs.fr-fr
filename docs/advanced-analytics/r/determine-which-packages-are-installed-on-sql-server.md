---
title: "Identifier les packages installés sur SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 08/31/2016
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
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 90e7146bde123ca8ac8a8e6ff3e11d212fd4a35a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="determine-which-packages-are-installed-on-sql-server"></a>Identifier les packages installés sur SQL Server
  Cette rubrique décrit comment vous pouvez identifier les packages R qui sont installés sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Par défaut, l’installation de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] crée une bibliothèque de packages R associée à chaque instance. Par conséquent, pour savoir quels packages sont installés sur un ordinateur, vous devez exécuter cette requête sur chaque instance distincte sur laquelle R Services est installé. Notez que les bibliothèques de packages **ne sont pas** partagées par les instances. Il est donc possible d’installer des packages différents sur différentes instances.

Pour plus d’informations sur la façon d’identifier l’emplacement de la bibliothèque par défaut d’une instance, consultez [Installation et gestion des packages R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).   
   
 
## <a name="get-a-list-of-installed-packages-using-r"></a>Obtenir la liste des packages installés à l’aide de R  
 Il existe différentes façons d’obtenir la liste des packages installés ou chargés à l’aide d’outils ou de fonctions R.  
  
+   De nombreux outils de développement R fournissent un explorateur d’objets ou une liste des packages installés ou chargés dans l’espace de travail R actuel.  

+ Nous vous recommandons les fonctions suivantes du package RevoScaleR qui sont fournies spécifiquement pour la gestion des packages dans des contextes de calcul :
  - [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage)
  - [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages)   
  
+   Vous pouvez utiliser une fonction R, telle que `installed.packages()`, incluse dans le package `utils` installé. La fonction analyse les fichiers DESCRIPTION de chaque package identifié dans la bibliothèque spécifiée et retourne une matrice des noms de packages, des chemins d’accès à la bibliothèque et des numéros de version.  
 
### <a name="examples"></a>Exemples  
L’exemple suivant utilise la fonction `rxInstalledPackages` pour obtenir la liste des packages disponibles dans le contexte de calcul SQL Server fourni.

~~~~
sqlServerCompute <- RxInSqlServer(connectionString = 
"Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
     sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
     sqlPackages
~~~~

 L’exemple suivant utilise la fonction R de base `installed.packages()` dans une procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] pour obtenir une matrice des packages qui ont été installés dans la bibliothèque R_SERVICES de l’instance actuelle. Pour éviter d’analyser les champs du fichier DESCRIPTION, seul le nom est retourné.  
  
```  
EXECUTE sp_execute_external_script  
@language=N'R'  
,@script = N'str(OutputDataSet);  
packagematrix <- installed.packages();  
NameOnly <- packagematrix[,1];  
OutputDataSet <- as.data.frame(NameOnly);'  
,@input_data_1 = N'SELECT 1 as col'  
WITH RESULT SETS ((PackageName nvarchar(250) ))  
```  
  
 Pour plus d’informations, consultez la description des champs facultatifs et par défaut du fichier DESCRIPTION du package R à l’adresse [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).  
  
## <a name="see-also"></a>Voir aussi  
 [Installer des packages R supplémentaires sur SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)  
  
  

