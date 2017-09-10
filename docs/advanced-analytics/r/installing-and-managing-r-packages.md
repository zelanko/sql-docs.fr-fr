---
title: "Installation et gestion des packages R | Microsoft Docs"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ae30bfc42e42b69158dbba5a38b0bccbe93523b4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="installing-and-managing-r-packages"></a>Installation et gestion des packages R
 Toutes les solutions R exécutées dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] doivent utiliser les packages qui sont installés dans la bibliothèque R par défaut. Le plus souvent, les solutions R référencent les bibliothèques utilisateur en spécifiant un chemin de fichier dans le code R, mais cette pratique n’est pas recommandée dans un environnement de production.

Par conséquent, c’est à l’administrateur de base de données ou à un autre administrateur du serveur de s’assurer que tous les packages nécessaires sont installés sur l’instance [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Si vous n’avez pas les privilèges d’administration sur l’ordinateur qui héberge l’instance [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], communiquez à l’administrateur les informations à utiliser pour installer les packages R, puis fournissez l’accès à un référentiel de packages sécurisé à partir duquel les utilisateurs pourront obtenir les packages dont ils ont besoin. Cette section fournit ces informations. 

> [!TIP]
> [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] offre de nouvelles fonctionnalités d’installation et de gestion des packages R qui permettent à l’administrateur de base de données et au scientifique des données d’installer et d’utiliser les packages avec plus de souplesse, tout en contrôlant davantage les opérations. Pour plus d’informations, consultez [Gestion des packages R pour SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 

## <a name="installed-packages"></a>Packages installés
Quand vous installez [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], les packages R de **base**, tels que `stats` et `utils`, sont par défaut installés avec le package **RevoScaleR** qui prend en charge les connexions à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
> [!NOTE]  
>  Pour obtenir la liste des packages installés par défaut, consultez [Packages installés avec Microsoft R Open](https://mran.microsoft.com/rro/installed/).  

 Si vous avez besoin d’un package supplémentaire du CRAN ou d’un autre référentiel, vous devez le télécharger et l’installer sur votre station de travail.  
  
 Si vous devez exécuter le nouveau package dans le contexte du serveur, ce package doit également être installé sur le serveur par un administrateur.   
   
## <a name="where-and-how-to-get-new-packages"></a>Où et comment obtenir de nouveaux packages  
 Il existe plusieurs sources de packages R, les plus connues étant CRAN et Bioconductor. Le site officiel pour le langage R ([https://www.r-project.org/](https://www.r-project.org/)) répertorie la plupart de ces ressources. De nombreux packages sont également publiés sur GitHub, où vous pouvez obtenir le code source. Par ailleurs, vous avez peut-être également reçu des packages R développés par une personne dans votre entreprise.  
  
 Quelle que soit la source, les packages doivent être fournis au format d’un fichier compressé à installer. De plus, pour utiliser le package avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], assurez-vous d’obtenir le fichier compressé au format binaire Windows. (Certains packages risquent de ne pas prendre en charge ce format.) Pour plus d’informations sur le contenu du format de fichier zip et sur la création d’un package R, nous vous recommandons de consulter le didacticiel [Freidrich Leisch: Creating R Packages](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf), téléchargeable au format PDF à partir du site R project. 
  
 En général, vous pouvez installer les packages R facilement à partir de la ligne de commande, sans avoir besoin de les télécharger au préalable si l’ordinateur utilisé est connecté à Internet.  Cela n’est généralement pas le cas avec les serveurs exécutant [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  Pour installer un package R sur un ordinateur qui n’est **pas** connecté à Internet, vous devez préalablement télécharger le package dans le format compressé approprié, puis copier les fichiers compressés dans un dossier accessible à l’ordinateur. 
 
 Les rubriques suivantes décrivent deux méthodes possibles pour installer des packages hors connexion : 

+ [Create an Offline Package Repository using miniCRAN](../../advanced-analytics/r-services/create-a-local-package-repository-using-minicran.md) (Créer un référentiel de packages hors connexion à l’aide de miniCRAN)

  Décrit comment utiliser le package R **miniCRAN** pour créer un référentiel hors connexion. Cette méthode est recommandée si vous souhaitez installer des packages sur plusieurs serveurs et gérer le référentiel à partir d’un emplacement unique. 
+ [Install New R Packages from the Internet](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md) (Installer de nouveaux packages R à partir d’Internet)

  Fournit des instructions pour installer des packages hors connexion en copiant manuellement les fichiers compressés.   

## <a name="permissions-required-for-installing-r-packages"></a>Autorisations requises pour l’installation des packages R  
  
Pour installer un nouveau package R sur un ordinateur exécutant [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous devez avoir des droits d’administration sur l’ordinateur.   

Si vous ne disposez pas de ces droits, contactez votre administrateur et fournissez-lui les informations sur le package à installer.  
  

Si vous souhaitez installer un nouveau package R sur un ordinateur faisant office de station de travail R, mais qui n’a **pas** d’instance [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] installée, vous devez également avoir des droits d’administration sur cet ordinateur pour installer le package. Après avoir installé le package, vous pouvez l’exécuter localement.  
 
> [!NOTE]
> Dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], de nouveaux rôles de base de données ont été ajoutés pour pouvoir définir l’étendue des autorisations d’installation des packages au niveau de l’instance et au niveau de la base de données. Pour plus d’informations, consultez [Gestion des packages R pour SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md).
 

### <a name="location-of-default-r-library-location-for-r-services"></a>Emplacement de la bibliothèque R par défaut pour R Services

Si vous avez installé [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sur l’instance par défaut, la bibliothèque de packages R utilisée par l’instance se trouve dans le dossier de l’instance [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Exemple : 

+ Instance par défaut _MSSQLSERVER_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
+ Instance nommée _MyNamedInstance_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library` 


Vous pouvez exécuter l’instruction suivante pour déterminer la bibliothèque par défaut pour l’instance actuelle de R. 
~~~~
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
~~~~

Pour plus d’informations, consultez [Identifier les packages installés sur SQL Server](../../advanced-analytics/r-services/determine-which-packages-are-installed-on-sql-server.md).

## <a name="managing-installed-packages"></a>Gestion des packages installés

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] offre de nouvelles fonctionnalités d’installation et de gestion des packages R qui permettent à l’administrateur de base de données et au scientifique des données d’installer et d’utiliser les packages avec plus de souplesse, tout en contrôlant davantage les opérations. Pour plus d’informations, consultez [Gestion des packages R pour SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 

Si vous utilisez SQL Server 2106 R Services, les nouvelles fonctionnalités de gestion des packages ne sont pas encore disponibles. À la place, vous pouvez utiliser l’une des méthodes suivantes pour identifier les packages installés sur l’ordinateur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] :

+ Affichez la bibliothèque par défaut, si vous avez les autorisations nécessaires sur le dossier.
+ Exécutez une commande à partir de la ligne de commande R pour afficher la liste des packages situés à l’emplacement de la bibliothèque R_SERVICES.
+ Utilisez une procédure stockée sur l’instance, comme celle-ci :
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
 [Gestion et surveillance des solutions R](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  

