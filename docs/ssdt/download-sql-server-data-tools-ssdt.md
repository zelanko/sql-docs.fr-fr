---
title: "Télécharger SQL Server Data Tools (SSDT) | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "installer ssdt, télécharger ssdt, dernière version ssdt"
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 681ad2f6d7aeb88db45dde3f2e695db672b97dbd
ms.lasthandoff: 04/11/2017

---
# <a name="download-sql-server-data-tools-ssdt"></a>Télécharger SSDT (SQL Server Data Tools)

**[SQL Server Data Tools](https://msdn.microsoft.com/mt186501)** est un outil de développement moderne que vous pouvez télécharger gratuitement pour créer des bases de données relationnelles SQL Server, des bases de données SQL Azure, des packages Integration Services, des modèles de données Analysis Services et des rapports Reporting Services. Avec SSDT, vous pouvez concevoir et déployer tout type de contenu SQL Server avec la même facilité que lorsque vous développez une application dans Visual Studio. Cette version prend en charge SQL Server 2016 jusqu’à SQL Server 2005 et fournit l’environnement de conception pour ajouter des fonctionnalités qui sont nouvelles dans SQL Server 2016.  
    
    
| ![téléchargement](../ssdt/media/download.png) Télécharger SQL Server Data Tools pour Visual Studio 2015  | Télécharger l’Infrastructure d’application de la couche Données (DacFx) ||
|:---|:---|:---|
|**[Télécharger SQL Server Data Tools (16.5)](https://msdn.microsoft.com/mt186501)**|[**Télécharger DacFx et SqlPackage.exe (16.5)**](https://www.microsoft.com/download/details.aspx?id=54106) |Version de disponibilité générale actuelle pour la production.|
|[**Télécharger SQL Server Data Tools (SSDT) - Version Release Candidate**](../ssdt/sql-server-data-tools-ssdt-release-candidate.md)| [**Télécharger DacFx et SqlPackage.exe - Version Release Candidate**](../ssdt/sql-server-data-tools-ssdt-release-candidate.md) |Prise en charge de SQL Server vNext.|



## <a name="download-visual-studio"></a>Télécharger Visual Studio

* [**Télécharger Visual Studio Community 2015**](https://www.visualstudio.com/products/visual-studio-community-vs.aspx)

### <a name="use-ssdt-in-visual-studio-2017"></a>Utiliser SSDT dans Visual Studio 2017

* [**Télécharger Visual Studio 2017**](https://www.visualstudio.com/) -([Comparaison des fonctionnalités de Visual Studio 2017 par édition](https://www.visualstudio.com/vs/compare/))

Pour utiliser les projets de base de données relationnelle, nous vous recommandons de vérifier la charge de travail de **stockage et de traitement des données** lors de l’installation. La prise en charge des projets de base de données SSDT est également incluse dans plusieurs autres charges de travail, y compris *Azure*, le *développement web et ASP.Net*, et le *développement multiplateforme .NET Core*.

Si vous utilisez SSDT avec Visual Studio 2017, installez les composants AS et RS :
* [Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)
* [Reporting Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio)


## <a name="installing-ssdt-without-visual-studio-pre-installed"></a>Installation de SSDT sans préinstallation de Visual Studio

Si Visual Studio n’est pas installé sur votre ordinateur, l’installation de SSDT pour Visual Studio 2015 installera aussi une version « Shell intégré » minimale de Visual Studio 2015. Vous pouvez installer gratuitement cette version de Visual Studio et l’utiliser sur autant d’ordinateurs que vous le voulez. Elle vous permet d’utiliser tous les types de projets SQL Server, ainsi que l’Explorateur d’objets de SQL Server et d’autres outils SQL.

Si [Visual Studio 2015 Community Edition (ou ultérieur)](https://www.visualstudio.com/products/visual-studio-community-vs.aspx) est installé sur votre ordinateur, l’installation de SSDT ajoutera l’ensemble complet des outils SQL Server à votre installation existante de Visual Studio. Visual Studio inclut de nombreuses fonctionnalités que vous pouvez utiliser, comme l’intégration du contrôle de code source et la prise en charge de langages non-SQL. Nous recommandons l’utilisation de Visual Studio 2015 Community ou ultérieur pour bénéficier de la meilleure expérience lors du développement avec T-SQL.

## <a name="supported-sql-versions"></a>Versions de SQL prises en charge
  
|Modèles de projets|Plateformes SQL prises en charge|  
|-------------------|--------------------|  
Bases de données relationnelles|  SQL Server 2005* - SQL Server 2016 <br /><br />Base de données Azure SQL<br /><br />Azure SQL Data Warehouse (prend uniquement en charge les requêtes ; les projets de base de données ne sont pas encore pris en charge)<br /><br />  * SQL Server 2005 est déprécié,<br /><br /> passez à une version de SQL officiellement prise en charge|
  |Modèles Analysis Services<br /><br />Reporting Services, rapports | SQL Server 2008 – SQL Server 2016|
  |Integration Services, packages| SQL Server 2012 – SQL Server 2016    |
  
## <a name="next-steps"></a>Étapes suivantes  
Après l’installation de SSDT, parcourez ces didacticiels pour apprendre à créer des bases de données, des packages, des modèles de données et des rapports à l’aide de SSDT :  
  
-   [Développement de base de données hors connexion orienté projet](https://msdn.microsoft.com/library/hh272702(v=vs.103).aspx)  
  
-   [Didacticiel SSIS : Créer un package ETL simple](https://msdn.microsoft.com/library/ms169917.aspx)  
  
-   [Didacticiels sur Analysis Services](https://msdn.microsoft.com/library/hh231701.aspx)  
  
-   [Créer un rapport de tableau de base (didacticiel SSRS)](https://msdn.microsoft.com/library/ms167305.aspx)  
  
## <a name="see-also"></a>Voir aussi  
[SQL Server Data Tools dans Visual Studio](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Forum MSDN SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Blog de l’équipe SSDT](http://blogs.msdn.com/b/ssdt/)  
[Commentaires Connect SSDT](https://connect.microsoft.com/SQLServer/Feedback)  
[Documentation de SSDT](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Référence de l’API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  

