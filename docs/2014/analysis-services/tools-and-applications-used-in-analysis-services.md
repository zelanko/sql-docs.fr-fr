---
title: Outils et applications utilisés dans Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 0ddb3b7a-7464-4d04-8659-11cb2e4cf3c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ac80f4187bc57c86736f09a19200d408e83eb57d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213792"
---
# <a name="tools-and-applications-used-in-analysis-services"></a>Outils et applications utilisés dans Analysis Services
  Trouvez les outils et les applications dont vous avez besoin pour créer des modèles Analysis Services, ainsi que pour gérer les bases de données associées sur une instance Analysis Services.  
  
## <a name="analysis-services-model-designers"></a>Concepteurs de modèles Analysis Services  
 Les modèles tabulaires et multidimensionnels sont créés à partir de modèles de projet dans une solution générée au sein de l'interpréteur de commandes Visual Studio. Le modèle de projet permet aux concepteurs de créer les modèles, les cubes, les dimensions et les rôles qui constituent une solution Analysis Services.  
  
### <a name="download-sql-server-data-tools-for-business-intelligence-ssdt-bi"></a>Télécharger SQL Server Data Tools - Business Intelligence (SSDT-BI)  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] pour Business Intelligence (SSDT-BI), anciennement Business Intelligence Development Studio (BIDS), permet de créer des modèles Analysis Services, des rapports Reporting Services et des packages Integration Services. Téléchargez SSDT-BI à partir des emplacements suivants :  
  
-   [Télécharger SSDT-BI pour Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkId=396526)  
  
-   [Télécharger SSDT-BI pour Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkID=273673)  
  
 Si vous avez installé une version antérieure de SSDT-BI ou BIDS sur votre ordinateur, la version plus récente est installée côte à côte à la version antérieure. Il est habituel d'exécuter des versions précédentes et plus récentes des outils de conception sur une même station de travail afin de pouvoir modifier les projets et les solutions liés à des versions spécifiques du serveur.  
  
> [!NOTE]  
>  Il existe plusieurs sites de téléchargement de la version Visual Studio 2012 et Visual Studio 2013 de SSDT. La plupart ne comprennent pas les modèles de projet BI. En cliquant sur les liens ci-dessus, vous obtiendrez la version appropriée. Vous saurez que vous disposez de la version de SSDT-BI correcte si vous voyez le dossier des modèles de projet Business Intelligence. Ce dossier contient les modèles de projet pour Analysis Services, Reporting Services et Integration Services. Selon la manière dont vous avez installé SSDT-BI, vous verrez également un modèle de projet supplémentaire pour les bases de données SQL Server.  
  
 ![Modèles Nouveau projet dans SSDT](media/ssdt-biprojects.png "Modèles Nouveau projet dans SSDT")  
  
## <a name="administrative-tools"></a>Outils d'administration  
  
### <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 Management Studio est l'outil d'administration principal de toutes les fonctionnalités SQL Server, y compris Analysis Services. SQL Server Management Studio est un composant facultatif. Si vous ne le voyez pas parmi les autres applications SQL Server dans la page Applications de Windows Server 2012, exécutez le programme d'installation de SQL Server pour l'ajouter à votre installation.  
  
### <a name="sql-server-profiler"></a>SQL Server Profiler  
 Bien qu'il soit officiellement déconseillé, SQL Server Profiler permet de surveiller facilement les connexions, l'exécution des requêtes MDX, ainsi que d'autres opérations relatives au serveur. SQL Server Profiler est installé par défaut. Vous le trouverez parmi les applications SQL Server dans la page Applications de Windows Server 2012.  
  
### <a name="powershell"></a>PowerShell  
 Vous pouvez utiliser des commandes PowerShell pour effectuer de nombreuses tâches d'administration. Pour plus d'informations, consultez [Analysis Services PowerShell](analysis-services-powershell.md) .  
  
### <a name="community-and-third-party-tools"></a>Communauté et outils tiers  
 Consultez la [page CodePlex consacrée à Analysis Services](http://sqlsrvanalysissrvcs.codeplex.com/) pour accéder à des exemples de code fournis par la Communauté. Les[forums](http://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlanalysisservices) peuvent être utiles pour trouver des recommandations sur les outils tiers qui prennent en charge Analysis Services.  
  
  
