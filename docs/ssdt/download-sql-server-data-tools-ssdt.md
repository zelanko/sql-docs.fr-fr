---
title: Télécharger SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 07/02/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssdt
ms.reviewer: ''
ms.suite: sql
ms.technology: ssdt
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords:
- installer ssdt, télécharger ssdt, dernière version ssdt
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 6989aaf0ccef6a9cb7656a23ffdc28062a33839b
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43084928"
---
# <a name="download-and-install-sql-server-data-tools-ssdt-for-visual-studio"></a>Télécharger et installer SQL Server Data Tools (SSDT) pour Visual Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
**SQL Server Data Tools** est un outil de développement moderne permettant de générer des bases de données relationnelles SQL Server, des bases de données SQL Azure, des modèles de données AS (Analysis Services), des packages IS (Integration Services) et des rapports RS (Reporting Services). Avec SSDT, vous pouvez concevoir et déployer tout type de contenu SQL Server avec la même facilité que lorsque vous développez une application dans Visual Studio.

*Pour la plupart des utilisateurs, SSDT (SQL Server Data Tools) est installé en même temps que Visual Studio. Le programme d’installation de Visual Studio installe les fonctionnalités SSDT de base. Vous devez donc exécuter le [programme d’installation autonome de SSDT](#ssdt-for-vs-2017-standalone-installer) pour bénéficier des outils AS, IS et RS*.

## <a name="install-ssdt-with-visual-studio-2017"></a>Installer SSDT avec Visual Studio 2017

Pour installer SSDT dans le cadre de [l’installation de Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio), sélectionnez la charge de travail **Stockage et traitement des données**, puis **SQL Server Data Tools**. Si Visual Studio est déjà installé, vous pouvez [modifier la liste des charges de travail](https://docs.microsoft.com/visualstudio/install/modify-visual-studio) pour inclure SSDT : ![Charge de travail Stockage et traitement des données](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload.png)



## <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>Installer les outils Analysis Services, Integration Services et Reporting Services
Pour installer la prise en charge des projet AS, IS et RS, exécutez le [programme d’installation autonome de SSDT](#ssdt-for-vs-2017-standalone-installer). 

Le programme d’installation répertorie les instances disponibles de Visual Studio auxquelles vous pouvez ajouter les outils SSDT. Si Visual Studio n’est pas installé, vous pouvez sélectionner **Installer une nouvelle instance de SQL Server Data Tools** pour installer SSDT avec une version minimale de Visual Studio. Toutefois, pour bénéficier d’une expérience optimale, nous vous recommandons d’utiliser SSDT avec [la dernière version de Visual Studio](https://www.visualstudio.com/downloads). 

![sélectionner AS, IS, RS](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)



## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT pour Visual Studio 2017 (programme d’installation autonome)

[![télécharger](../ssdt/media/download.png) Télécharger SSDT pour Visual Studio 2017 (15.7.1) ](https://go.microsoft.com/fwlink/?linkid=875613) 

> [!IMPORTANT]
> - Avant d’installer SSDT pour Visual Studio 2017 (15.7.1), désinstallez les extensions *Projets Analysis Services* et *Projets Reporting Services* si elles sont déjà installées, puis fermez toutes les instances de Visual Studio.
> - Si vous installez SSDT sous Windows 10 en choisissant **Installer la nouvelle instance SQL Server Data Tools pour Visual Studio 2017**, décochez toutes les cases et installez d’abord la nouvelle instance. Redémarrez alors l’ordinateur et rouvrez le programme d’installation SSDT pour continuer l’installation.  



**Informations sur la version**  
  
Numéro de version : 15.7.1  
Numéro de build : 14.0.16167.0  
Date de publication : 2 juillet 2018  

Pour obtenir la liste complète des modifications, consultez le [journal des modifications](changelog-for-sql-server-data-tools-ssdt.md).

SSDT pour Visual Studio 2017 nécessite la même [configuration](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs) que Visual Studio.  

### <a name="available-languages---ssdt-for-vs-2017"></a>Langues disponibles : SSDT pour VS 2017

Vous pouvez installer cette version de **SSDT pour VS 2017** dans les langues suivantes :  

[Chinois (simplifié)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x804) | 
[Chinois (traditionnel)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x404) | 
[Anglais (États-Unis)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x409) | 
[Français]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x40c)  
[allemand]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x407) | 
[italien]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x410) | 
[japonais]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x411) | 
[coréen]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x412) | 
[portugais (Brésil)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x416) | 
[russe]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x419) | 
[espagnol]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x40a)  



## <a name="ssdt-for-vs-2015-standalone-installer"></a>SSDT pour Visual Studio 2015 (programme d’installation autonome)

[![télécharger](../ssdt/media/download.png) Télécharger SSDT pour Visual Studio 2015 (17.4)](https://go.microsoft.com/fwlink/?linkid=863440)

**Informations sur la version**  
  
Numéro de version : 17.4

Numéro de build de cette version : 14.0.61712.050
  
Pour obtenir la liste complète des modifications, consultez le [journal des modifications](changelog-for-sql-server-data-tools-ssdt.md).

### <a name="available-languages---ssdt-for-vs-2015"></a>Langues disponibles : SSDT pour VS 2015
  
Vous pouvez installer cette version de **SSDT pour VS 2015** dans les langues suivantes :  

[Chinois (simplifié)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x804) | 
[Chinois (traditionnel)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x404) | 
[Anglais (États-Unis)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x409) | 
[Français]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x40c)  
[allemand]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x407) | 
[italien]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x410) | 
[japonais]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x411) | 
[coréen]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x412) | 
[portugais (Brésil)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x416) | 
[russe]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x419) | 
[espagnol]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x40a)  

### <a name="iso-images---ssdt-for-vs-2015"></a>Images ISO - SSDT pour VS 2015

Une image ISO de SSDT peut être utilisée comme alternative pour installer SSDT ou pour installer un point d'installation d'administration. L'image ISO est un fichier auto-extractible qui contient tous les composants nécessaires à SSDT et qui peut être téléchargée à l'aide d'un gestionnaire de téléchargement redémarrable, ce qui est utile en cas de bande passante réseau limitée ou peu fiable. Une fois téléchargée, l’image ISO peut être montée comme lecteur ou gravée sur un DVD.

> [!NOTE]
> SSDT pour les images ISO Visual Studio 2015 17.4 est maintenant disponible.

[Chinois (simplifié)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x804) |
[Chinois (traditionnel)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x404) |
[Anglais (États-Unis)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x409) |
[Français]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x40c)  
[allemand]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x407) |
[italien]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x410) |
[japonais]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x411) |
[coréen]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x412) |
[portugais (Brésil)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x416) |
[russe]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x419) |
[espagnol]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x40a)



## <a name="supported-sql-versions"></a>Versions de SQL prises en charge
  
|Modèles de projet|Plateformes SQL prises en charge|  
|-------------------|--------------------|  
Bases de données relationnelles|  SQL Server 2005* - SQL Server 2017<br> (utilisez SSDT 17.x ou SSDT pour Visual Studio 2017 pour vous connecter à [SQL Server sur Linux](../linux/sql-server-linux-overview.md))<br /><br />Azure SQL Database<br /><br />Azure SQL Data Warehouse (prend uniquement en charge les requêtes ; les projets de base de données ne sont pas encore pris en charge)<br /><br />  * SQL Server 2005 est déprécié,<br /><br /> passez à une version de SQL officiellement prise en charge|
  |Modèles Analysis Services<br /><br />Reporting Services, rapports | SQL Server 2008 – SQL Server 2017|
  |Integration Services, packages| SQL Server 2012 – SQL Server 2017    |
  
## <a name="dacfx"></a>DacFx
SSDT pour Visual Studio 2015 et SSDT pour Visual Studio 2017 utilisent tous deux DacFx 17.4.1 : [Télécharger l’infrastructure d’application de couche Données (DacFx) 17.4.1](https://www.microsoft.com/download/details.aspx?id=56508).


## <a name="next-steps"></a>Étapes suivantes  
Après l’installation de SSDT, parcourez ces didacticiels pour apprendre à créer des bases de données, des packages, des modèles de données et des rapports à l’aide de SSDT :  

- [Développement de base de données hors connexion orienté projet](project-oriented-offline-database-development.md)  
- [Didacticiel SSIS : Créer un package ETL simple](../integration-services/ssis-how-to-create-an-etl-package.md)  
- [Didacticiels sur Analysis Services](../analysis-services/analysis-services-tutorials-ssas.md)  
- [Créer un rapport de tableau de base (didacticiel SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]


## <a name="see-also"></a> Voir aussi  
[Forum MSDN SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Blog de l’équipe SSDT](http://blogs.msdn.com/b/ssdt/)  
[Référence de l’API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
