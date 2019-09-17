---
title: Télécharger SQL Server Data Tools (SSDT) | Microsoft Docs
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssdt
ms.topic: conceptual
keywords: installer ssdt, télécharger ssdt, dernière version ssdt
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 08/15/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 7fc8925b4257631561b6b68ed144becbadece639
ms.sourcegitcommit: 949e55b32eff6610087819a93160a35af0c5f1c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70383786"
---
# <a name="download-and-install-sql-server-data-tools-ssdt-for-visual-studio"></a>Télécharger et installer SQL Server Data Tools (SSDT) pour Visual Studio

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

**SQL Server Data Tools** est un outil de développement moderne permettant de générer des bases de données relationnelles SQL Server, des bases de données SQL Azure, des modèles de données AS (Analysis Services), des packages IS (Integration Services) et des rapports RS (Reporting Services). Avec SSDT, vous pouvez concevoir et déployer tout type de contenu SQL Server avec la même facilité que lorsque vous développez une application dans Visual Studio.

## <a name="changes-in-ssdt-for-visual-studio-2019"></a>Modifications apportées à SSDT pour Visual Studio 2019

Avec Visual Studio 2019, les fonctionnalités requises pour activer des projets Analysis Services, Integration Services et Reporting Services ont été déplacées dans les extensions respectives de Visual Studio. La fonctionnalité SSDT de base pour créer des projets de base de données est restée intégrée à Visual Studio (vous devez sélectionner la charge de travail de stockage et de traitement des données pendant l’installation). Une installation autonome de SSDT n’est plus nécessaire.

Si vous disposez déjà d’une licence pour Visual Studio 2019 :

- Pour les projets de base de données SQL, installez la charge de travail de stockage et de traitement des données pour Visual Studio
- Pour les projets Analysis Services, Integration Services ou Reporting Services, installez la ou les extensions appropriées à partir de la marketplace

Si vous n’avez pas encore de licence pour Visual Studio 2019 :

- Installez [Visual Studio Community 2019](https://visualstudio.microsoft.com/downloads/)
- Installez l’extension Analysis Services, Integration Services et Reporting Services de manière appropriée

## <a name="changes-in-ssdt-for-visual-studio-2017"></a>Modifications apportées à SSDT pour Visual Studio 2017

À partir de Visual Studio 2017, la fonctionnalité de création de projets de base de données a été intégrée dans l’installation de Visual Studio. Il est inutile d’installer le programme d’installation autonome SSDT pour bénéficier d’une expérience SSDT de base. Pour créer des projets Integration Services/Analysis Services/Reporting Services, vous avez toujours besoin du programme d’installation autonome SSDT.

- Pour les projets de base de données, installez la charge de travail de stockage et de traitement des données pour Visual Studio
- Pour les projets Analysis Services, Integration Services ou Reporting Services, téléchargez et installez [SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017)

## <a name="install-ssdt-with-visual-studio-2017"></a>Installer SSDT avec Visual Studio 2017

Pour installer SSDT dans le cadre de [l’installation de Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio), sélectionnez la charge de travail **Stockage et traitement des données**, puis **SQL Server Data Tools**. Si Visual Studio est déjà installé, vous pouvez [modifier la liste des charges de travail](https://docs.microsoft.com/visualstudio/install/modify-visual-studio) pour inclure SSDT : ![Charge de travail Stockage et traitement des données](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload.png)

## <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>Installer les outils Analysis Services, Integration Services et Reporting Services

Pour installer la prise en charge des projet AS, IS et RS, exécutez le [programme d’installation autonome de SSDT](#ssdt-for-vs-2017-standalone-installer).

Le programme d’installation répertorie les instances disponibles de Visual Studio auxquelles vous pouvez ajouter les outils SSDT. Si Visual Studio n’est pas installé, vous pouvez sélectionner **Installer une nouvelle instance de SQL Server Data Tools** pour installer SSDT avec une version minimale de Visual Studio. Toutefois, pour bénéficier d’une expérience optimale, nous vous recommandons d’utiliser SSDT avec [la dernière version de Visual Studio](https://www.visualstudio.com/downloads).

![sélectionner AS, IS, RS](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)

## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT pour Visual Studio 2017 (programme d’installation autonome)

[![télécharger](../ssdt/media/download.png) Télécharger SSDT pour Visual Studio 2017 (15.9.2)](https://go.microsoft.com/fwlink/?linkid=2095463)

> [!IMPORTANT]
> - Avant d’installer SSDT pour Visual Studio 2017 (15.9.2), désinstallez les extensions *Projets Analysis Services* et *Projets Reporting Services* si elles sont déjà installées, puis fermez toutes les instances de VS.
> - Utilisez SSDT pour Visual Studio 2017 (15.8.0) ou les versions antérieures pour concevoir des packages SSIS qui contiennent une source/destination Teradata. SSDT pour Visual Studio 2017 après la version 15.8.0 ne peut pas concevoir de packages SSIS qui contiennent une source/destination Teradata par Attunity.

### <a name="version-information"></a>Informations sur la version

Numéro de version : 15.9.2 Numéro de build : 14.0.16194.0 Date de publication : 17 juillet 2019 

Pour obtenir une liste complète des modifications, consultez [Notes de publication pour SQL Server Data Tools (SSDT)](release-notes-ssdt.md).

SSDT pour Visual Studio 2017 nécessite la même [configuration](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs) que Visual Studio.

### <a name="available-languages---ssdt-for-vs-2017"></a>Langues disponibles : SSDT pour VS 2017

Vous pouvez installer cette version de **SSDT pour VS 2017** dans les langues suivantes :

- [Chinois (simplifié)]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x804)
- [Chinois (traditionnel)]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x404)
- [Anglais (États-Unis)]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x409)
- [Français]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x40c)
- [Allemand]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x407)
- [Italien]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x410)
- [Japonais]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x411)
- [Coréen]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x412)
- [Portugais (Brésil)]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x416)
- [Russe]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x419)
- [Espagnol]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x40a)

## <a name="offline-install"></a>Installation hors connexion

Pour installer SSDT quand vous n’êtes pas connecté à Internet, suivez les étapes de cette section. Pour plus d’informations, consultez [Créer une installation réseau de Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio).

Commencez par effectuer les étapes suivantes tant que vous êtes **en ligne** :

1. [Télécharger le programme d’installation autonome SSDT](#ssdt-for-vs-2017-standalone-installer).
2. [Télécharger vs_sql.exe](https://aka.ms/vs/15/release/vs_sql.exe).
3. Pendant que vous êtes toujours en ligne, exécutez l’une des commandes suivantes pour télécharger tous les fichiers nécessaires à l’installation hors connexion. L’utilisation de l’option `--layout` est primordiale. Elle permet de télécharger les fichiers en vue d’une installation hors connexion. Remplacez `<filepath>` par le vrai chemin des dispositions pour y enregistrer les fichiers.
   1. Pour une langue spécifique, passez les paramètres régionaux : `vs_sql.exe --layout c:\<filepath> --lang en-us` (une seule langue correspond environ à 1 Go).
   1. Pour toutes les langues, omettez l’argument `--lang` : `vs_sql.exe --layout c:\<filepath>` (toutes les langues correspondent environ à 3,9 Go).

4. Exécutez `SSDT-Setup-ENU.exe /layout c:\<filepath>` pour extraire la charge utile SSDT dans l’emplacement `<filepath>` où les fichiers Visual Studio 2017 ont été téléchargés. De cette façon, tous les fichiers sont réunis dans un seul dossier de dispositions.

Après avoir effectué les étapes précédentes, vous pouvez effectuer celles-ci **hors connexion** :

1. Exécutez `vs_setup.exe --NoWeb` pour installer l’interpréteur de commandes de VS 2017 et le projet de données SQL Server.
2. À partir du dossier de dispositions, exécutez `SSDT-Setup-ENU.exe /install`, puis sélectionnez SSRS/SSIS/SSAS.
   - Pour une installation sans assistance, exécutez `SSDT-Setup-ENU.exe /INSTALLALL[:vsinstances] /passive`.

Pour les options disponibles, exécutez `SSDT-Setup-ENU.exe /help`

> [!NOTE]
> Si vous utilisez une version complète de Visual Studio 2017, créez un dossier en mode hors connexion pour SSDT uniquement et exécutez `SSDT-Setup-ENU.exe` à partir de ce dossier nouvellement créé. (N’ajoutez pas SSDT à une autre disposition hors connexion de Visual Studio 2017). Si vous ajoutez la disposition SSDT à une disposition hors connexion existante de Visual Studio, les composants d’exécution (.exe) nécessaires ne sont pas créés ici.

### <a name="considerations-and-limitations"></a>Observations et limitations

- Vous ne pouvez pas installer la version Community hors connexion
- Pour mettre à niveau SSDT, vous devez effectuer les mêmes étapes que celles suivies pour installer SSDT. Par exemple, si vous avez ajouté SSDT à l’aide de VSIX, effectuez une mise à niveau par le biais de VSIX. Si vous avez installé SSDT par le biais d’une installation distincte, vous devez effectuer la mise à niveau à l’aide de cette méthode.

## <a name="supported-sql-versions"></a>Versions de SQL prises en charge
 
|Modèles de projet|Plateformes SQL prises en charge| 
|-------------------|--------------------| 
|Bases de données relationnelles| SQL Server 2005\* - SQL Server 2017<br> (utilisez SSDT 17.x ou SSDT pour Visual Studio 2017 pour vous connecter à [SQL Server sur Linux](../linux/sql-server-linux-overview.md))<br /><br />Azure SQL Database<br /><br />Azure SQL Data Warehouse (prend uniquement en charge les requêtes ; les projets de base de données ne sont pas encore pris en charge)<br /><br /> \* La prise en charge de SQL Server 2005 est dépréciée,<br /><br /> passez à une version de SQL officiellement prise en charge|
|Modèles Analysis Services<br /><br />Reporting Services, rapports | SQL Server 2008 - SQL Server 2017|
|Integration Services, packages| SQL Server 2012 - SQL Server 2019 |

## <a name="dacfx"></a>DacFx

SSDT pour Visual Studio 2015 et SSDT pour Visual Studio 2017 utilisent tous les deux DacFx 17.4.1 : [Télécharger le framework d’application de la couche Données (DacFx) 17.4.1](https://www.microsoft.com/download/details.aspx?id=56508).

## <a name="previous-versions"></a>Versions précédentes

Pour télécharger et installer SSDT pour Visual Studio 2015 ou une version précédente de SSDT, consultez [Versions précédentes de SQL Server Data Tools (SSDT et SSDT-BI)](previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md).

## <a name="next-steps"></a>Étapes suivantes

Après l’installation de SSDT, parcourez ces didacticiels pour apprendre à créer des bases de données, des packages, des modèles de données et des rapports à l’aide de SSDT : 

- [Développement de base de données hors connexion orienté projet](project-oriented-offline-database-development.md) 
- [Tutoriel SSIS : Créer un package ETL simple](../integration-services/ssis-how-to-create-an-etl-package.md) 
- [Didacticiels sur Analysis Services](https://docs.microsoft.com/analysis-services/analysis-services-tutorials-ssas) 
- [Créer un rapport de tableau de base (didacticiel SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md) 

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="see-also"></a> Voir aussi

[Forum MSDN SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt) 
[Blog de l’équipe SSDT](https://blogs.msdn.com/b/ssdt/) 
[Informations de référence sur l’API DACFx](https://msdn.microsoft.com/library/dn645454.aspx) 
[Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) 
