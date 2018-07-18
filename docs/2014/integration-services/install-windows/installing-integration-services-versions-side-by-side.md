---
title: Interopérabilité et Coexistence (Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interoperability and coexistence [Integration Services]
- Integration Services, interoperability and coexistence
ms.assetid: edfbcd56-012f-462e-a542-95491394fda9
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8f7face1f41fdf02f772c05427db9d45d1bd6050
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277585"
---
# <a name="interoperability-and-coexistence-integration-services"></a>Interopérabilité et coexistence (Integration Services)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services (SSIS) peut coexister côte à côte avec [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services et [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services.  
  
## <a name="features-and-differences"></a>Fonctionnalités et différences  
 Le tableau ci-dessous répertorie certaines des différences entre la version actuelle et les versions antérieures de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Fonctionnalité|[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]|[!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]|[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]|  
|-------------|-------------------------------|---------------------------------|---------------------------------|  
|Environnement de développement|[SQL Server 2014 Data Tools – Business Intelligence pour Visual Studio 2012 CTP 2](http://www.microsoft.com/download/details.aspx?id=40736)<br /><br /> [SQL Server 2014 Data Tools - Business Intelligence pour Visual Studio 2013](http://www.microsoft.com/download/details.aspx?id=42313)|[SQL Server Data Tools pour Visual Studio 2010](http://msdn.microsoft.com/library/hh500335\(v=vs.103\).aspx)<br /><br /> [SQL Server Data Tools – Business Intelligence pour Visual Studio 2012](http://www.microsoft.com/download/details.aspx?id=36843)|Business Intelligence Development Studio ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)])|  
|Environnement de gestion|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
|Table système principale dans msdb pour le stockage des packages|sysssispackages|sysssispackages|sysssispackages|  
|Utilitaire d'invite de commandes principal pour l'exécution des packages|**dtexec** (dtexec.exe), version 2014|**dtexec** (dtexec.exe), version 2012|**dtexec** (dtexec.exe), version 2008|  
|Dossier racine par défaut du système de fichiers|C:\Program Files\Microsoft SQL Server\120\DTS|C:\Program Files\Microsoft SQL Server\110\DTS|C:\Program Files\Microsoft SQL Server\100\DTS|  
|Clé de Registre racine par défaut|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS|  
  
## <a name="side-by-side-compatibility-issues"></a>Problèmes de compatibilité côte à côte  
 Lorsque [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services est installé côte à côte avec [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services et [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services, vous pouvez effectuer les tâches suivantes :  
  
-   **Concevoir des packages dans les outils de données SQL Server**. Utilisez les outils suivants pour développer et maintenir des packages en fonction des versions correspondantes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Utilisez la version [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] de Business Intelligence Development Studio pour développer et maintenir des packages basés sur [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]  
  
    -   Utilisez le [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] version de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour développer et maintenir des packages qui sont basés sur [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
    -   Utilisez le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour développer et maintenir des packages qui sont basés sur [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
-   **Charger et exécuter des packages**. Vous pouvez charger et exécuter des packages qui ont été développés dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], dans le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Lorsque vous ajoutez le package à un projet existant, le package est mis à niveau définitivement au format utilisé par [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services. Lorsque vous ouvrez le fichier de package dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], le package est mis à niveau temporairement au format utilisé par [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services. Si vous enregistrez les modifications apportées au package, il est définitivement mis à niveau. Une fois enregistrés au format qui [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilise Integration Services, les packages ne peuvent plus être ouverts dans le correspondantes [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] version de Business Intelligence Development Studio, ni exécutés par le correspondantes [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] outils Integration Services.  
  
-   **Gérer les packages dans SQL Server Management Studio**. Vous ne pouvez pas vous connecter à une instance de la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version de la [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service, à partir de la [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou le [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] version de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Vous ne pouvez pas vous connecter à une instance de la [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou le [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] version de la [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service à partir de la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Vous pouvez utiliser la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour gérer des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stockés dans une instance de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Vous devez modifier le fichier de configuration du service pour ajouter l'instance de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] à la liste des emplacements gérés par le service. Pour plus d’informations, consultez [Configuring the Integration Services Service &#40;SSIS Service&#41;](../service/integration-services-service-ssis-service.md).  
  
-   **Stocker les packages dans SQL Server**. Vous pouvez stocker des packages dans les bases de données suivantes.  
  
    |Format du package|Base de données|  
    |--------------------|--------------|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services|base de données msdb d’une instance de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services|base de données msdb d’une instance de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|  
    |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services|base de données msdb d’une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
     Sur une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez importer des packages à partir d’une instance de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou d’une instance de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], mais vous ne pouvez pas exporter des packages à une instance de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou à une instance de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
     Sur une instance de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou une instance de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], vous ne pouvez pas importer de packages provenant d'une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ni exporter de packages vers une telle instance.  
  
-   **Exécuter les packages**. Vous pouvez exécuter [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services et [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] packages Integration Services à l’aide de la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version de la **dtexec** utilitaire ou de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Chaque fois qu’un [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] l’outil Integration Services charge un package qui a été développé dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], l’outil convertit temporairement, en mémoire, le package au package de mise en forme qui [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] utilise. Si le [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] package présente des problèmes qui empêchent une conversion réussie, le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] outil d’Integration Services ne peut pas exécuter le package jusqu'à ce que ces problèmes soient résolus. Pour plus d’informations, voir [Upgrade Integration Services Packages](upgrade-integration-services-packages.md).  
  
  
