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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5bd0e1d3955d898824d285d28979089e2de6f322
ms.openlocfilehash: 7aaa4c48419bf24357b2bef95c40d721d1ab2f2a
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="download-sql-server-data-tools-ssdt"></a>Télécharger SSDT (SQL Server Data Tools)

**[SQL Server Data Tools](https://msdn.microsoft.com/mt186501)** est un outil de développement moderne que vous pouvez télécharger gratuitement pour créer des bases de données relationnelles SQL Server, des bases de données SQL Azure, des packages Integration Services, des modèles de données Analysis Services et des rapports Reporting Services. Avec SSDT, vous pouvez concevoir et déployer tout type de contenu SQL Server avec la même facilité que lorsque vous développez une application dans Visual Studio. Cette version prend en charge SQL Server 2017 à SQL Server 2005 et fournit l’environnement de conception pour ajouter des fonctionnalités qui sont nouvelles dans SQL Server 2016.  
    
    
![télécharger](../ssdt/media/download.png) [Télécharger SQL Server Data Tools 17.1 pour Visual Studio 2015](https://go.microsoft.com/fwlink/?linkid=849393)

![télécharger](../ssdt/media/download.png) [Télécharger Data-Tier Application Framework (DacFx) 17.1](https://www.microsoft.com/download/details.aspx?id=55255)

## <a name="sql-server-data-tools"></a>Outils de données SQL Server   
**Informations sur la version**  
  
Numéro de la version : 17.1  
Numéro de build de cette version : 14.0.61705.170
  
 **Nouveautés**
 - Prise en charge en mode hors connexion d’IntelliSense AS non lié au modèle (par exemple, mise en surbrillance, saisie semi-automatique des instructions et informations de paramètres)
 - Ajout à l’Explorateur de modèles tabulaires pour afficher les expressions M
 - Sélecteur de personnes d’Azure Active Directory pour la configuration des membres de rôle dans les modèles tabulaires
 - Prise en charge de l’encodage des indicateurs dans l’interface utilisateur lors de la définition des modèles 1400
 - Plusieurs correctifs de bogues de projet AS
 - Plusieurs correctifs de bogues DacFx

 **Problèmes connus**
 - Lors de la création d’une source de données dans un modèle AS de niveau de compatibilité 1400, si vous sélectionnez une source de données de fichiers et que vous appuyez sur Annuler avant de créer la source de données, l’éditeur tabulaire (Model.bim) bascule en lecture seule. Vous pouvez contourner ce problème en fermant simplement l’éditeur tabulaire et en le rouvrant à partir de l’Explorateur de solutions.

Liste complète des modifications disponibles dans le [journal des modifications](changelog-for-sql-server-data-tools-ssdt.md)

 > Pour utiliser SQL Server Data Tools dans Visual Studio 2017, consultez [cette](#use-ssdt-in-visual-studio-2017) section ci-dessous

  **Langues disponibles**  
  
 Vous pouvez installer cette version de SSDT dans les langues suivantes :  
[chinois (République populaire de Chine)]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x804) | 
[chinois (Taïwan)]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x404) | 
[anglais (États-Unis)]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x409) | 
[français]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x40c)  
[allemand]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x407) | 
[italien]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x410) | 
[japonais]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x411) | 
[coréen]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x412) | 
[portugais (Brésil)]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x416) | 
[russe]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x419) | 
[espagnol]( https://go.microsoft.com/fwlink/?linkid=849393&clcid=0x40a)  

**Images ISO**

Une image ISO de SSDT peut être utilisée comme alternative pour installer SSDT ou pour installer un point d'installation d'administration. L'image ISO est un fichier auto-extractible qui contient tous les composants nécessaires à SSDT et qui peut être téléchargée à l'aide d'un gestionnaire de téléchargement redémarrable, ce qui est utile en cas de bande passante réseau limitée ou peu fiable. Une fois téléchargée, l’image ISO peut être montée comme lecteur ou gravée sur un DVD.

[chinois (République populaire de Chine)]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x804) |
[chinois (Taïwan)]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x404) |
[anglais (États-Unis)]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x409) |
[français]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x40c)  
[allemand]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x407) |
[italien]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x410) |
[japonais]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x411) |
[coréen]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x412) |
[portugais (Brésil)]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x416) |
[russe]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x419) |
[espagnol]( https://go.microsoft.com/fwlink/?linkid=849399&clcid=0x40a)

## <a name="download-visual-studio"></a>Télécharger Visual Studio

* [**Télécharger Visual Studio Community 2015**](https://www.visualstudio.com/products/visual-studio-community-vs.aspx)

## <a name="installing-ssdt-without-visual-studio-pre-installed"></a>Installation de SSDT sans préinstallation de Visual Studio

Si Visual Studio n’est pas installé sur votre ordinateur, l’installation de SSDT pour Visual Studio 2015 installera aussi une version « Shell intégré » minimale de Visual Studio 2015. Vous pouvez installer gratuitement cette version de Visual Studio et l’utiliser sur autant d’ordinateurs que vous le voulez. Elle vous permet d’utiliser tous les types de projets SQL Server, ainsi que l’Explorateur d’objets de SQL Server et d’autres outils SQL.

Si [Visual Studio 2015 Community Edition (ou ultérieur)](https://www.visualstudio.com/products/visual-studio-community-vs.aspx) est installé sur votre ordinateur, l’installation de SSDT ajoutera l’ensemble complet des outils SQL Server à votre installation existante de Visual Studio. Visual Studio inclut de nombreuses fonctionnalités que vous pouvez utiliser, comme l’intégration du contrôle de code source et la prise en charge de langages non-SQL. Nous recommandons l’utilisation de Visual Studio 2015 Community ou ultérieur pour bénéficier de la meilleure expérience lors du développement avec T-SQL.

## <a name="supported-sql-versions"></a>Versions de SQL prises en charge
  
|Modèles de projets|Plateformes SQL prises en charge|  
|-------------------|--------------------|  
Bases de données relationnelles|  SQL Server 2005* - SQL Server 2017 <br /><br />Base de données Azure SQL<br /><br />Azure SQL Data Warehouse (prend uniquement en charge les requêtes ; les projets de base de données ne sont pas encore pris en charge)<br /><br />  * SQL Server 2005 est déprécié,<br /><br /> passez à une version de SQL officiellement prise en charge|
  |Modèles Analysis Services<br /><br />Reporting Services, rapports | SQL Server 2008 – SQL Server 2017|
  |Integration Services, packages| SQL Server 2012 – SQL Server 2017    |
  
## <a name="next-steps"></a>Étapes suivantes  
Après l’installation de SSDT, parcourez ces didacticiels pour apprendre à créer des bases de données, des packages, des modèles de données et des rapports à l’aide de SSDT :  
  
-   [Développement de base de données hors connexion orienté projet](https://msdn.microsoft.com/library/hh272702(v=vs.103).aspx)  
  
-   [Didacticiel SSIS : Créer un package ETL simple](https://msdn.microsoft.com/library/ms169917.aspx)  
  
-   [Didacticiels sur Analysis Services](https://msdn.microsoft.com/library/hh231701.aspx)  
  
-   [Créer un rapport de tableau de base (didacticiel SSRS)](https://msdn.microsoft.com/library/ms167305.aspx)  
  
## <a name="use-ssdt-in-visual-studio-2017"></a>Utiliser SSDT dans Visual Studio 2017 

* [**Télécharger Visual Studio 2017**](https://www.visualstudio.com/) -([Comparaison des fonctionnalités de Visual Studio 2017 par édition](https://www.visualstudio.com/vs/compare/))

Pour utiliser les projets de base de données relationnelle, nous vous recommandons de vérifier la charge de travail de **stockage et de traitement des données** lors de l’installation. La prise en charge des projets de base de données SSDT est également incluse dans plusieurs autres charges de travail, y compris *Azure*, le *développement web et ASP.Net*, et le *développement multiplateforme .NET Core*.

> [!NOTE]
> Les projets de base de données SSDT dans Visual Studio 2017 prennent actuellement en charge jusqu’à SQL Server 2016.  La prise en charge de SQL Server 2017 sera bientôt disponible dans une mise à jour de Visual Studio 2017.

Si vous utilisez SSDT avec Visual Studio 2017, installez les composants AS et RS :
* [Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)
* [Reporting Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio)


## <a name="see-also"></a>Voir aussi  
[SQL Server Data Tools dans Visual Studio](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Forum MSDN SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Blog de l’équipe SSDT](http://blogs.msdn.com/b/ssdt/)  
[Commentaires Connect SSDT](https://connect.microsoft.com/SQLServer/Feedback)  
[Documentation de SSDT](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Référence de l’API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  

