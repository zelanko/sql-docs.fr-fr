---
title: SQL Server Management Studio (SSMS)
description: Description de SQL Server Management Studio (SSMS) et de ce qu’il peut faire.
ms.prod: sql
ms.technology: ssms
ms.topic: overview
author: markingmyname
ms.author: maghan
ms.reviewer: ''
f1_keywords:
- sql13.ssms.viewhelp.f1
helpviewer_keywords:
- SQL Server Management Studio
- SQL Server Management Studio for Integration Services
- SQL Server Management Studio for Reporting Services
- SQL Server Management Studio for Analysis Services
ms.custom: ''
ms.date: 05/29/2019
ms.openlocfilehash: 3f80cc74cc20c2ed02e32577fadbe13a5bf7dd38
ms.sourcegitcommit: 1800fc15075bb17b50d0c18b089d8a64d87ae726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66500339"
---
# <a name="what-is-sql-server-management-studio-ssms"></a>Qu’est-ce que SQL Server Management Studio (SSMS) ?

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (SSMS) est un environnement intégré de gestion des infrastructures SQL. Utilisez SSMS pour accéder à, configurer, gérer, administrer et développer tous les composants de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Azure SQL Database et SQL Data Warehouse. SSMS fournit un utilitaire unique et complet qui associe un vaste ensemble d’outils graphiques à différents éditeurs de script performants, pour permettre aux développeurs et aux administrateurs de base de données de tous niveaux d’avoir accès à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

- [**Télécharger SQL Server Management Studio (SSMS)**](download-sql-server-management-studio-ssms.md)
- [**Télécharger SQL Server Developer**](https://my.visualstudio.com/Downloads?q=SQL%20Server%20Developer)
- [**Télécharger Visual Studio**](https://www.visualstudio.com/downloads/)

## <a name="sql-server-management-studio-components"></a>Composants de SQL Server Management Studio  
  
|Description|Composant|  
|---------------|---------|  
|Utilisez **l’Explorateur d’objets** pour afficher et gérer tous les objets d’une ou plusieurs instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Explorateur d’objets](../ssms/object/object-explorer.md)|  
|Comment utiliser l’**Explorateur de modèles** pour créer et gérer des fichiers de texte réutilisable que vous utilisez pour accélérer le développement de requêtes et de scripts.|[l’Explorateur de modèles](../ssms/template/template-explorer.md)|  
|Comment utiliser **l’Explorateur de solutions** déconseillé pour créer des projets visant à gérer les éléments d’administration, comme les scripts et les requêtes.|[Explorateur de solutions](../ssms/solution/solution-explorer.md)|  
|Comment utiliser les outils de conception visuelle inclus dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].|[Visual Database Tools](../ssms/visual-db-tools/visual-database-tools.md)|  
|Comment utiliser les éditeurs de langage de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] pour créer et déboguer des requêtes et des scripts de manière interactive.|[Éditeurs de texte et de requête (SQL Server Management Studio)](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)|

## <a name="sql-server-management-studio-for-business-intelligence"></a>SQL Server Management Studio pour le décisionnel

Pour accéder, configurer, gérer et administrer [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], utilisez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Même si les trois technologies de décisionnel reposent sur [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], les tâches d'administration associées à chacune d'entre elle sont légèrement différentes.
  
> [!NOTE]
> Pour créer et modifier des solutions [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]et [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , utilisez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull_md.md)], et non [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull_md.md)] est un environnement de développement basé sur [!INCLUDE[msCoName](../includes/msconame_md.md)][!INCLUDE[vsprvs](../includes/vsprvs-md.md)].
  
### <a name="managing-analysis-services-solutions-using-sql-server-management-studio"></a>Gestion des solutions Analysis Services à l'aide de SQL Server Management Studio

[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] vous permet de gérer des objets [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] , par exemple effectuer des sauvegardes et le traitement d’objets.
  
[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] fournit un projet Script [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] dans lequel vous pouvez développer et enregistrer des scripts écrits dans une syntaxe MDX (Multidimensional Expressions) et XMLA (XML for Analysis). Ces projets Script [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] servent à effectuer les tâches de gestion ou recréer des objets, tels que les bases de données et les cubes, sur des instances [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] . Par exemple, vous pouvez développer un script XMLA dans un projet de Script [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] qui crée directement des objets sur une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] existante. Les projets de Script [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] peuvent être enregistrés au sein d'une solution et intégrés avec un système de contrôle de code source.
  
Pour plus d’informations sur la façon d’utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], consultez [Développement et implémentation à l’aide de SQL Server Management Studio](../analysis-services/instances/analysis-services-scripts-project-in-sql-server-management-studio.md).
  
### <a name="managing-integration-services-solutions-using-sql-server-management-studio"></a>Gestion des solutions Integration Services à l'aide de SQL Server Management Studio

[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] vous permet d’utiliser le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour gérer les packages et surveiller les packages en cours d’exécution. Vous pouvez également utiliser [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] pour organiser des packages en dossiers, exécuter des packages, importer et exporter des packages, migrer des packages DTS (Data Transformation Services) et mettre à jour des packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .

### <a name="managing-reporting-services-projects-using-sql-server-management-studio"></a>Gestion des projets Reporting Services à l'aide de SQL Server Management Studio

Utiliser SQL Server Management Studio pour activer les fonctionnalités de Reporting Services, administrer le serveur et les bases de données, et gérer des rôles et des travaux.

Vous gérez des planifications partagées à l'aide du dossier Planifications partagées et gérer des bases de données du serveur de rapports (ReportServer, ReportServerTempdb). Vous créez aussi un RSExecRole dans la base de données système Master quand vous déplacez une base de données du serveur de rapports vers un moteur de base de données SQL Server ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde_md.md)]). Pour plus d'informations sur ces tâches, consultez les rubriques suivantes :  

- [Management Studio - Rubriques de procédures](https://msdn.microsoft.com/60685458-9108-47bf-820a-5e7db454d408)
- [Administration d'une base de données du serveur de rapports](../reporting-services/report-server/administer-a-report-server-database-ssrs-native-mode.md)
- [Guide pratique : Créer le RSExecRole](../reporting-services/security/create-the-rsexecrole.md)
  
Vous gérez également le serveur en activant et configurant différentes fonctionnalités, en définissant les valeurs par défaut du serveur, et en gérant des rôles et des travaux. Pour plus d'informations sur ces tâches, consultez les rubriques suivantes :

- [Guide pratique : Définir les propriétés du serveur de rapports (Management Studio)](https://msdn.microsoft.com/1ed0f84b-b12a-4e49-b65c-a11a99f9093f)
- [Guide pratique : Créer, supprimer ou modifier un rôle (Management Studio)](https://msdn.microsoft.com/3d1d56e6-a283-44a7-8417-36cb4d2c74d1)
- [Activation et désactivation de l'impression côté client pour Reporting Services](https://msdn.microsoft.com/0e709c96-7517-4547-8ef6-5632f8118524)

## <a name="non-english-language-versions-of-sql-server-management-studio-ssms"></a>Versions de SQL Server Management Studio (SSMS) dans d’autres langues que l’anglais

Le blocage sur l’installation en plusieurs langues a été levé. Vous pouvez installer SSMS en allemand sur un ordinateur Windows français. Si la langue du système d’exploitation ne correspond pas à la langue de SSMS, l’utilisateur doit changer la langue sous Outils > Options > Paramètres internationaux. Sinon, SSMS affiche l’interface utilisateur en anglais.

Pour plus d’informations sur les différents paramètres régionaux avec les versions antérieures, consultez [Installer des versions non anglaises de SSMS](install-other-languages.md).

## <a name="support-policy-for-ssms"></a>Stratégie de prise en charge pour SSMS

- À partir de SSMS 17.0, l’équipe SQL Tools a adopté la [stratégie de cycle de vie moderne Microsoft](https://support.microsoft.com/help/30881/modern-lifecycle-policy).
- Lisez [l’annonce sur la stratégie de cycle de vie moderne](https://support.microsoft.com/help/447912/announcing-microsoft-modern-lifecycle-policy).
- Pour plus d’informations, consultez les [Questions fréquentes (FAQ) sur la politique de cycle de vie moderne](https://support.microsoft.com/help/30882/modern-lifecycle-policy-faq).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="next-steps"></a>Étapes suivantes

- [Installer des versions de SQL Server Management Studio (SSMS) dans d’autres langues que l’anglais](install-other-languages.md)
- [Tutoriel : SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Tutoriel : Écriture d’instructions Transact-SQL](https://msdn.microsoft.com/2addc9be-67d0-423d-a457-192fe9d7d058)
- [Développement et implémentation à l’aide de SQL Server Data Tools](../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)
- [Reporting Services dans les outils de données SQL Server](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)
- [Tutoriel : SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/tutorials/tutorial-sql-server-management-studio)

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]