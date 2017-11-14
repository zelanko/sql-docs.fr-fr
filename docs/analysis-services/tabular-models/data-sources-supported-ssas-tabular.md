---
title: "Les sources de données prises en charge dans les modèles tabulaires SQL Server Analysis Services | Documents Microsoft"
ms.custom: 
ms.date: 10/16/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6c2b1b3-91fc-4175-af25-509946dc7f24
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 6d18cbe5b20882581afa731ce5d207cbbc69be6c
ms.openlocfilehash: 2d716dc332ec8271a11498b6385d4801b64b808a
ms.contentlocale: fr-fr
ms.lasthandoff: 10/21/2017

---
# <a name="data-sources-supported-in-tabular-models"></a>Sources de données prises en charge dans les modèles tabulaires

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]   
Pour Azure Analysis Services, consultez [des sources de données prises en charge dans Azure Analysis Services](https://docs.microsoft.com/en-us/azure/analysis-services/analysis-services-datasource).

  Cette rubrique décrit les types de sources de données qui peuvent être utilisées avec les modèles tabulaires.  
  
##  <a name="bkmk_supported_ds"></a>Sources de données pris en charge pour les modèles tabulaires en mémoire  
Lorsque vous installez [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], le programme d'installation n'installe pas les fournisseurs répertoriés pour chaque source de données. Certains fournisseurs peuvent être installés avec d’autres applications sur votre ordinateur. Dans d’autres cas, vous devrez peut-être télécharger et installer le fournisseur.  
  
|||||  
|-|-|-|-|  
|Source|Versions|Type de fichier|Fournisseurs|  
|Bases de données Access|Microsoft Access 2010 et versions ultérieures.|.accdb ou .mdb|Fournisseur OLE DB ACE 14|  
|Bases de données relationnelles SQL Server|SQL Server 2008 et versions ultérieur, SQL Server 2008 de l’entrepôt de données et version ultérieure, Azure SQL Database, Azure SQL Data Warehouse, système de plateforme Analytique (APS)<br /><br /> <br /><br /> Système de plateforme Analytique (APS) était anciennement en tant que SQL Server Parallel Data Warehouse (PDW). À l’origine, la connexion à PDW à partir d’Analysis Services nécessitait un fournisseur de données spécial. Ce fournisseur a été remplacé dans SQL Server 2012. À partir de SQL Server 2012, le client natif SQL Server est utilisé pour les connexions à PDW/APS. |(non applicable)|Fournisseur OLE DB pour SQL Server<br /><br /> Fournisseur OLE DB SQL Server Native Client<br /><br /> Fournisseur OLE DB SQL Server Native Client 10.0<br /><br /> Fournisseur de données .NET Framework pour SQL Client|  
|Bases de données relationnelles Oracle|Oracle 9i et versions ultérieures.|(non applicable)|Fournisseur OLE DB Oracle<br /><br /> Fournisseur de données .NET Framework pour client Oracle<br /><br /> Fournisseur de données .NET Framework pour SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Bases de données relationnelles Teradata|Teradata V2R6 et versions ultérieures|(non applicable)|Fournisseur OLE DB TDOLEDB<br /><br /> Fournisseur de données .Net pour Teradata|  
|Bases de données relationnelles Informix||(non applicable)|Fournisseur OLE DB Informix|  
|Bases de données relationnelles IBM DB2|8.1|(non applicable)|DB2OLEDB|  
|Bases de données relationnelles Sybase Adaptive Server Enterprise (ASE)|15.0.2|(non applicable)|Fournisseur OLE DB Sybase|  
|Autres bases de données relationnelles|(non applicable)|(non applicable)|Fournisseur OLE DB pour pilote ODBC|  
|Fichiers texte|(non applicable)|.txt, .tab, .csv|Fournisseur OLE DB ACE 14 pour Microsoft Access|  
|Fichiers Microsoft Excel|Excel 2010 et versions ultérieures|.xlsx, xlsm, .xlsb, .xltx, .xltm|Fournisseur OLE DB ACE 14|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] classeur|Microsoft SQL Server 2008 Analysis Services et versions ultérieures|xlsx, xlsm, .xlsb, .xltx, .xltm|ASOLEDB 10.5<br /><br /> (utilisé uniquement avec les classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] publiés dans des batteries de serveurs SharePoint où [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] est installé)|  
|Cube Analysis Services|Microsoft SQL Server 2008 Analysis Services et versions ultérieures|(non applicable)|ASOLEDB 10|  
|Flux de données<br /><br /> (utilisé pour importer des données à partir de rapports Reporting Services, de documents de service Atom, de Microsoft Azure Marketplace DataMarket et d'un flux de données unique)|Format Atom 1.0<br /><br /> Base de données ou document qui est exposé en tant que Windows Communication Foundation (WCF) Data Services (anciennement ADO.NET Data Services).|`.atomsvc`pour un document de service qui définit un ou plusieurs flux<br /><br /> .atom pour un document de flux Web Atom|Fournisseur de flux de données Microsoft pour [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> Fournisseur de données de flux de données .NET Framework pour [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
|Fichiers de connexion de base de données Office||.odc||  
  
  
##  <a name="bkmk_supported_ds_dq"></a> Sources de données prises en charge pour les modèles DirectQuery  
 DirectQuery est une alternative au mode de stockage en mémoire : cette approche consiste à router les requêtes vers des systèmes de données back-end d’où sont retournés directement les résultats, plutôt qu’à stocker toutes les données à l’intérieur du modèle (et dans la mémoire RAM, une fois le modèle est chargé). Analysis Services doit formuler des requêtes dans la syntaxe de requête de base de données native, un sous-ensemble réduit de sources de données est prise en charge pour ce mode.  
  
Source de données   |Versions  |Fournisseurs
---------|---------|---------
Microsoft SQL Server    |  2008 et versions ultérieures      |       Fournisseur OLE DB pour SQL Server, fournisseur SQL Server Native Client OLE DB, fournisseur de données .NET Framework pour SQL Client  
Base de données SQL Microsoft Azure    |   Tous      |  Fournisseur OLE DB pour SQL Server, fournisseur SQL Server Native Client OLE DB, fournisseur de données .NET Framework pour SQL Client            
Microsoft Azure SQL Data Warehouse     |   Tous     |  Fournisseur SQL Server Native Client OLE DB, fournisseur de données .NET Framework pour SQL Client       
Microsoft SQL Analytics Platform System (APS)     |   Tous      |  Fournisseur OLE DB pour SQL Server, fournisseur SQL Server Native Client OLE DB, fournisseur de données .NET Framework pour SQL Client       
Bases de données relationnelles Oracle     |  Oracle 9i et versions ultérieures       |  Fournisseur OLE DB Oracle       
Bases de données relationnelles Teradata    |  Teradata V2R6 et versions ultérieures     | Fournisseur de données .Net pour Teradata    

  
##  <a name="bkmk_tips"></a> Conseils pour le choix des sources de données  
  
Importer des tables à partir de bases de données relationnelles vous épargne certaines opérations, car les relations de *clé étrangère* sont utilisées pendant l'importation pour créer des relations entre des tables dans le générateur de modèles.  
  
Importer plusieurs tables, puis supprimer celles dont vous n'avez pas besoin peut également vous épargner des opérations. Si vous importez des tables une par une, il vous faudra peut-être encore créer manuellement des relations entre les tables.  
  
Les colonnes qui contiennent des données similaires dans différentes sources de données constituent la base de la création de relations dans le générateur de modèles. Si vous utilisez des sources de données hétérogènes, choisissez des tables qui comportent des colonnes pouvant être mappées à des tables d'autres sources de données qui contiennent des données identiques ou similaires.  
  
Fournisseurs OLE DB peuvent parfois offrir de meilleures performances pour les données à grande échelle. Quand vient le moment de faire votre choix parmi différents fournisseurs pour la même source de données, il est conseillé d'essayer en premier le fournisseur OLE DB.  

