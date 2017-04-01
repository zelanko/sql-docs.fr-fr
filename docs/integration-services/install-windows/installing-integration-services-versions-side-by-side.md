---
title: "Installation de plusieurs versions Integration&#160;Services c&#244;te &#224; c&#244;te | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interopérabilité et coexistence [Integration Services]"
  - "Integration Services, interopérabilité et coexistence"
ms.assetid: edfbcd56-012f-462e-a542-95491394fda9
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 41
---
# Installation de plusieurs versions Integration&#160;Services c&#244;te &#224; c&#244;te
  Vous pouvez installer   
      [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] plusieurs versions d’Integration Services (SSIS) côte à côte. Cette rubrique décrit certaines limitations des installations côte à côte.  
  
## Conception et gestion de packages  
 Pour concevoir et gérer des packages ciblant SQL Server 2016, SQL Server 2014 ou SQL Server 2012, utilisez SQL Server Data Tools (SSDT) pour Visual Studio 2015. Pour obtenir SSDT, voir [Télécharger la dernière version de SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx).  
  
 Dans les pages de propriétés d’un projet Integration Services, au niveau de l’onglet **Général** de **Propriétés de configuration**, sélectionnez la propriété **TargetServerVersion** et choisissez SQL Server 2016, SQL Server 2014 ou SQL Server 2012.  
  
|Version cible de SQL Server|Environnement de développement de packages SSIS|  
|----------------------------------|-----------------------------------------------|  
|2016|SQL Server Data Tools pour Visual Studio 2015|  
|2014|SQL Server Data Tools pour Visual Studio 2015<br /><br /> ou<br /><br /> SQL Server Data Tools - Business Intelligence pour Visual Studio 2013|  
|2012|SQL Server Data Tools pour Visual Studio 2015<br /><br /> ou<br /><br /> SQL Server Data Tools – Business Intelligence pour Visual Studio 2012|  
|2008|Business Intelligence Development Studio dans SQL Server 2008|  
  
 Lorsque vous ajoutez un package existant à un projet existant, le package est converti au format ciblé par le projet.  
  
## Exécution des packages  
 Pour exécuter des packages Integration Services créés par des versions antérieures des outils de développement, vous pouvez utiliser la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de l’utilitaire **dtexec** ou de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Lorsque ces outils [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] chargent un package développé dans une version antérieure des outils de développement, l’outil convertit momentanément le package en mémoire dans le format de package utilisé par [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] . Si le package présente des problèmes empêchant une conversion, l’outil [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne peut pas exécuter le package tant que ces problèmes ne sont pas résolus. Pour plus d’informations, consultez [Mettre à niveau des packages Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
  