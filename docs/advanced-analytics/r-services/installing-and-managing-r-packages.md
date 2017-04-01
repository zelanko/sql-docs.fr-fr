---
title: "Installation et gestion des Packages R | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Installation et gestion des Packages R
 Toute solution R qui s’exécute dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] doit utiliser les packages sont installés dans la bibliothèque par défaut R. En règle générale, les solutions R référencera bibliothèques utilisateur en spécifiant un chemin d’accès du code R, mais cela n’est pas recommandé pour la production.

Par conséquent, il est la tâche de l’administrateur de base de données ou un autre administrateur sur le serveur pour vous assurer que tous les packages requis sont installés sur le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] instance. Si vous aient des privilèges d’administrateur sur l’ordinateur qui héberge le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]  instance, vous pouvez fournir aux informations sur l’installation des packages R administrateur et fournir l’accès à un référentiel sécurisé où les packages demandés par les utilisateurs peuvent être obtenus. Cette section fournit des informations. 

> [!TIP]
> [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] fournit de nouvelles fonctionnalités pour l’installation et la gestion des packages R qui donnent à la fois l’administrateur de base de données et une plus grande liberté de données scientifiques et contrôler l’utilisation du package et le programme d’installation. Pour plus d’informations, consultez [Gestion des packages R pour SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 

## <a name="installed-packages"></a>Packages installés
Lorsque vous installez  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)],  par défaut R **base** packages sont installés, tels que `stats` et `utils`, ainsi que de la **RevoScaleR** package qui prend en charge les connexions à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
> [!NOTE]  
>  Pour obtenir la liste des packages installés par défaut, consultez la page [Packages installés avec Microsoft R Open](https://mran.microsoft.com/rro/installed/).  

 Si vous avez besoin d’un package à partir de la section CRAN ou un autre référentiel supplémentaire, vous devez télécharger le package et l’installer sur votre station de travail.  
  
 Si vous devez exécuter le nouveau package dans le contexte du serveur, un administrateur doit l’installer sur le serveur.   
   
## <a name="where-and-how-to-get-new-packages"></a>Où et comment obtenir de nouveaux packages  
 Il existe plusieurs sources de packages R, plus connues étant CRAN et Bioconductor. Le site officiel du langage R ([https://www.r-project.org/](https://www.r-project.org/)) répertorie la plupart de ces ressources. De nombreux packages sont également publiés sur GitHub, où vous pouvez obtenir le code source. Par ailleurs, vous avez peut-être également reçu des packages R développés par une personne dans votre entreprise.  
  
 Quelle que soit la source, les packages doivent être fournis au format d’un fichier compressé à installer. En outre, pour utiliser le package avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], veillez à obtenir le fichier compressé au format binaire Windows. (Certains packages ne peuvent pas en charge ce format.) Pour plus d’informations sur le contenu du format de fichier zip et comment créer un package R, nous vous recommandons de ce didacticiel, vous pouvez télécharger au format PDF à partir du site de projet R : [Freidrich Leisch : création de Packages R](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf). 
  
 En général, les packages R peuvent être installés facilement à partir de la ligne de commande sans les télécharger à l’avance si l’ordinateur a accès à Internet.  Cela n’est généralement pas le cas avec les serveurs exécutant [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] .  Par conséquent, pour installer un package R sur un ordinateur qui exécute **pas** ont accès à Internet, vous devez télécharger le package au format zip approprié avance puis copiez les fichiers dans un dossier qui est accessible par l’ordinateur. 
 
 Les rubriques suivantes décrivent deux méthodes d’installation des packages hors connexion : 

+ [Créer un référentiel de Package en mode hors connexion à l’aide de miniCRAN](../../advanced-analytics/r-services/create-a-local-package-repository-using-minicran.md)

  Décrit comment utiliser le package R **miniCRAN** pour créer un référentiel hors connexion. Ceci est probablement la méthode la plus efficace si vous avez besoin installer des packages vers plusieurs serveurs et gérer le référentiel depuis un emplacement unique. 
+ [Installez les nouveaux Packages R à partir d’Internet](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)

  Inclut des instructions pour l’installation des packages hors ligne en copiant manuellement les fichiers compressés.   

## <a name="permissions-required-for-installing-r-packages"></a>Autorisations requises pour l’installation des packages R  
  
Pour installer un nouveau package de R sur un ordinateur exécutant [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous devez disposer des droits d’administration sur l’ordinateur.   

Si vous ne disposez pas de ces droits, contactez votre administrateur et fournissez-lui les informations sur le package à installer.  
  

Si vous installez un nouveau package de R sur un ordinateur qui est utilisé comme une station de travail R et que l’ordinateur **pas** une instance de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] installé, vous devez toujours des droits administratifs sur l’ordinateur pour installer le package. Après avoir installé le package, vous pouvez l’exécuter localement.  
 
> [!NOTE]
> Dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], nouveaux rôles de base de données ont été ajoutées pour prendre en charge étendue des autorisations d’installation de package à un niveau d’instance et base de données. Pour plus d’informations, consultez [Gestion des packages R pour SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md).
 

### <a name="location-of-default-r-library-location-for-r-services"></a>Emplacement de bibliothèque par défaut R pour les Services de R

Si vous avez installé  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] à l’aide de l’instance par défaut, la bibliothèque de package R utilisée par l’instance se trouve sous le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] dossier de l’instance. Exemple : 

+ Instance par défaut _MSSQLSERVER_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
+ Instance nommée _MyNamedInstance_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library` 


Vous pouvez exécuter l’instruction suivante pour vérifier la bibliothèque par défaut pour l’instance actuelle de R. 
~~~~
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
~~~~

Pour plus d’informations, consultez [déterminer lequel les Packages sont installés sur SQL Server](../../advanced-analytics/r-services/determine-which-packages-are-installed-on-sql-server.md).

## <a name="managing-installed-packages"></a>Gestion des Packages installés

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] fournit de nouvelles fonctionnalités pour l’installation et la gestion des packages R qui donnent à la fois l’administrateur de base de données et une plus grande liberté de données scientifiques et contrôler l’utilisation du package et le programme d’installation. Pour plus d’informations, consultez [Gestion des packages R pour SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 

Si vous utilisez SQL Server 2106 R Services, les nouvelles fonctionnalités de gestion du package ne sont pas disponibles pour l’instant. En attendant, vous disposez de ces options pour déterminer quels packages sont installés sur le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ordinateur, utilisez une des options suivantes :

+ Afficher la bibliothèque par défaut, si vous disposez des autorisations pour le dossier.
+ Exécuter une commande à partir de la commande R pour répertorier les packages à l’emplacement de la bibliothèque R_SERVICES
+ Sur l’instance, utilisez une procédure stockée comme suit :
   ```SQL
   EXECUTE sp_execute_external_script  @language=N'R'  
        ,@script = N'str(OutputDataSet);  
        packagematrix <- installed.packages();  
        NameOnly <- packagematrix[,1];  
        OutputDataSet <- as.data.frame(NameOnly);'  
        ,@input_data_1 = N'SELECT 1 as col'  
        WITH RESULT SETS ((PackageName nvarchar(250) ))   
   ```


 ## <a name="see-also"></a>Voir aussi  
 [Gestion et surveillance des Solutions R](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  