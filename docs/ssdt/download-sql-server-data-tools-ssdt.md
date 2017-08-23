---
title: "Télécharger SQL Server Data Tools (SSDT) | Microsoft Docs"
ms.custom: 
ms.date: 08/07/2017
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
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 3f12671ace99d5fefc199c7b1c2db31e5b3cfade
ms.openlocfilehash: 4bcceaeca15c3fa20cd797bda0182cf48f73a730
ms.contentlocale: fr-fr
ms.lasthandoff: 08/08/2017

---
# <a name="download-sql-server-data-tools-ssdt"></a>Télécharger SSDT (SQL Server Data Tools)

**[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)** est un outil de développement moderne que vous pouvez télécharger gratuitement pour créer des bases de données relationnelles SQL Server, des bases de données SQL Azure, des packages Integration Services, des modèles de données Analysis Services et des rapports Reporting Services. Avec SSDT, vous pouvez concevoir et déployer tout type de contenu SQL Server avec la même facilité que lorsque vous développez une application dans Visual Studio. Cette version prend en charge SQL Server 2017 à SQL Server 2005 et fournit l’environnement de conception permettant d’ajouter de nouvelles fonctionnalités de SQL Server.  
    
    
![télécharger](../ssdt/media/download.png) [Télécharger SQL Server Data Tools 17.2 pour Visual Studio 2015](https://go.microsoft.com/fwlink/?linkid=852922)

![télécharger](../ssdt/media/download.png) [Télécharger Data-Tier Application Framework (DacFx) 17.2](https://www.microsoft.com/download/details.aspx?id=55713)

## <a name="sql-server-data-tools"></a>SQL Server Data Tools   
**Informations sur la version**  
  
Numéro de la version : 17.2  
Numéro de build de cette version : 14.0.61707.300
  
**Nouveautés**

**AS**

- La sécurité au niveau des objets peut maintenant être configurée dans la boîte de dialogue Rôles pour la sécurité avancée dans les modèles tabulaires de niveau de compatibilité 1400.
- Une nouvelle sélection de membre du rôle AAD a été ajoutée pour les utilisateurs sans adresse e-mail dans les modèles Azure AS des projets AS SSDT pour VS2017.
- Une nouvelle propriété de projet Azure AS « Toujours demander » a été ajoutée dans les projets tabulaires AS SSDT pour personnaliser le comportement de mise en cache des informations d’identification ADAL.


**Problèmes connus**

- Pour obtenir la liste complète des modifications, consultez le [journal des modifications](changelog-for-sql-server-data-tools-ssdt.md).
- Signalez les problèmes sur le site de [Commentaires Connect SSDT](https://connect.microsoft.com/SQLServer/Feedback).

> [!NOTE]
> Pour utiliser SQL Server Data Tools dans Visual Studio 2017, consultez [cette](#use-ssdt-in-visual-studio-2017) section ci-dessous

  **Langues disponibles**  
  
 Vous pouvez installer cette version de SSDT dans les langues suivantes :  
[chinois (République populaire de Chine)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x804) | 
[chinois (Taïwan)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x404) | 
[anglais (États-Unis)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x409) | 
[français]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x40c)  
[allemand]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x407) | 
[italien]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x410) | 
[japonais]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x411) | 
[coréen]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x412) | 
[portugais (Brésil)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x416) | 
[russe]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x419) | 
[espagnol]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x40a)  

**Images ISO**

Une image ISO de SSDT peut être utilisée comme alternative pour installer SSDT ou pour installer un point d'installation d'administration. L'image ISO est un fichier auto-extractible qui contient tous les composants nécessaires à SSDT et qui peut être téléchargée à l'aide d'un gestionnaire de téléchargement redémarrable, ce qui est utile en cas de bande passante réseau limitée ou peu fiable. Une fois téléchargée, l’image ISO peut être montée comme lecteur ou gravée sur un DVD.

[chinois (République populaire de Chine)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x804) |
[chinois (Taïwan)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x404) |
[anglais (États-Unis)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x409) |
[français]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x40c)  
[allemand]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x407) |
[italien]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x410) |
[japonais]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x411) |
[coréen]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x412) |
[portugais (Brésil)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x416) |
[russe]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x419) |
[espagnol]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x40a)

## <a name="download-visual-studio"></a>Télécharger Visual Studio

* [**Télécharger Visual Studio Community 2015**](https://www.visualstudio.com/products/visual-studio-community-vs.aspx)

## <a name="installing-ssdt-without-visual-studio-pre-installed"></a>Installation de SSDT sans préinstallation de Visual Studio

Si Visual Studio n’est pas installé sur votre ordinateur, l’installation de SSDT pour Visual Studio 2015 installera aussi une version « Shell intégré » minimale de Visual Studio 2015. Vous pouvez installer gratuitement cette version de Visual Studio et l’utiliser sur autant d’ordinateurs que vous le voulez. Elle vous permet d’utiliser tous les types de projets SQL Server, ainsi que l’Explorateur d’objets de SQL Server et d’autres outils SQL.

Si [Visual Studio 2015 Community Edition (ou ultérieur)](https://www.visualstudio.com/products/visual-studio-community-vs.aspx) est installé sur votre ordinateur, l’installation de SSDT ajoutera l’ensemble complet des outils SQL Server à votre installation existante de Visual Studio. Visual Studio inclut de nombreuses fonctionnalités que vous pouvez utiliser, comme l’intégration du contrôle de code source et la prise en charge de langages non-SQL. Nous recommandons l’utilisation de Visual Studio 2015 Community ou ultérieur pour bénéficier de la meilleure expérience lors du développement avec T-SQL.

## <a name="supported-sql-versions"></a>Versions de SQL prises en charge
  
|Modèles de projets|Plateformes SQL prises en charge|  
|-------------------|--------------------|  
Bases de données relationnelles|  SQL Server 2005* - SQL Server 2017 <br /><br />Azure SQL Database<br /><br />Azure SQL Data Warehouse (prend uniquement en charge les requêtes ; les projets de base de données ne sont pas encore pris en charge)<br /><br />  * SQL Server 2005 est déprécié,<br /><br /> passez à une version de SQL officiellement prise en charge|
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

