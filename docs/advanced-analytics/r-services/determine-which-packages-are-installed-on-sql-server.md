---
title: "Identifier les packages install&#233;s sur SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "08/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Identifier les packages install&#233;s sur SQL Server
  Cette rubrique décrit comment vous pouvez déterminer quels packages R sont installés sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.  
  
Par défaut, l’installation du [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] crée une bibliothèque de package R associée à chaque instance. Par conséquent, pour savoir quels packages sont installés sur un ordinateur, vous devez exécuter cette requête sur chaque instance séparée, où R Services est installé. Notez que les bibliothèques de package sont **pas** partagé entre des instances, il est possible pour les différents packages doivent être installés sur des instances différentes.

Pour plus d’informations sur la façon de déterminer l’emplacement de la bibliothèque par défaut d’une instance, consultez [installation et la gestion des Packages R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).   
   
 
## Obtenir la liste des Packages installés à l’aide de R  
 Il existe plusieurs façons d’obtenir la liste des packages installés ou chargées à l’aide des outils R et les fonctions R.  
  
+   De nombreux outils de développement R fournissent un explorateur d’objets ou une liste des packages installés ou chargés dans l’espace de travail R actuel.  

+ Nous vous recommandons des fonctions suivantes à partir du package RevoScaleR qui sont fournies spécifiquement pour la gestion des packages dans des contextes de calcul :
  - [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/rxfindpackage)
  - [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/rxInstalledPackages)   
  
+   Vous pouvez utiliser une fonction R, telle que `installed.packages()`, incluse dans le package `utils` installé. La fonction analyse les fichiers de DESCRIPTION de chaque package qui a été trouvé dans la bibliothèque spécifiée et renvoie une matrice des noms de packages, les chemins d’accès de la bibliothèque et les numéros de version.  
 
### Exemples  
L’exemple suivant utilise la fonction `rxInstalledPackages` pour obtenir la liste des packages disponibles dans le contexte de calcul de SQL Server fourni.

~~~~
sqlServerCompute <- RxInSqlServer(connectionString = 
"Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
     sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
     sqlPackages
~~~~

 L’exemple suivant utilise la fonction R base `installed.packages()` dans un [!INCLUDE[tsql](../../includes/tsql-md.md)] procédure stockée pour obtenir une matrice de packages qui ont été installés dans la bibliothèque R_SERVICES pour l’instance actuelle. Pour éviter d’analyser les champs du fichier DESCRIPTION, seul le nom est retourné.  
  
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
  
 Pour plus d’informations sur les champs facultatifs dans le fichier DESCRIPTION du package R par défaut, consultez la page [https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file](https://cran.r-project.org/doc/manuals/R-exts.html).  
  
## Voir aussi  
 [Installer des Packages R supplémentaires sur SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)  
  
  