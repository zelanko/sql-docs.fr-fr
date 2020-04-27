---
title: Sources de données prises en charge (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d6c2b1b3-91fc-4175-af25-509946dc7f24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 345e733e5c1e90f637efab02a9942e307c2fb9f4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66067380"
---
# <a name="data-sources-supported-ssas-tabular"></a>Sources de données prises en charge (SSAS Tabulaire)
  Cette rubrique décrit les types de sources de données qui peuvent être utilisées avec les modèles tabulaires.  
  
 Cet article contient les sections suivantes :  
  
-   [Sources de données prises en charge](#bkmk_supported_ds)  
  
-   [Sources non prises en charge](#bkmk_unsupported_ds)  
  
-   [Conseils pour le choix des sources de données](#bkmk_tips)  
  
##  <a name="supported-data-sources"></a><a name="bkmk_supported_ds"></a>Sources de données prises en charge  
 Vous pouvez importer des données à partir des sources de données dans la table suivante. Lorsque vous installez [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], le programme d'installation n'installe pas les fournisseurs répertoriés pour chaque source de données. Certains fournisseurs ont pu être déjà installés sur votre ordinateur avec d'autres applications ; dans le cas contraire, vous devez télécharger et installer le fournisseur.  
  
|||||  
|-|-|-|-|  
|Source|Versions|Type de fichier|Fournisseurs <sup>1</sup>|  
|Bases de données Access|Microsoft Access 2003, 2007, 2010.|.accdb ou .mdb|Fournisseur OLE DB ACE 14|  
|Bases de données relationnelles SQL Server|Microsoft SQL Server 2005, 2008, 2008 R2 ; SQL Server 2012, Microsoft SQL Azure Database <sup>2</sup>|(non applicable)|Fournisseur OLE DB pour SQL Server<br /><br /> Fournisseur OLE DB SQL Server Native Client<br /><br /> Fournisseur OLE DB SQL Server Native Client 10.0<br /><br /> Fournisseur de données .NET Framework pour SQL Client|  
|SQL Server Parallel Data Warehouse (PDW) <sup>3</sup>|2008 R2|(non applicable)|Fournisseur OLE DB pour SQL Server PDW|  
|Bases de données relationnelles Oracle|Oracle 9i, 10g, 11g.|(non applicable)|Fournisseur OLE DB Oracle<br /><br /> Fournisseur de données .NET Framework pour client Oracle<br /><br /> Fournisseur de données .NET Framework pour SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Bases de données relationnelles Teradata|Teradata V2R6, V12|(non applicable)|Fournisseur OLE DB TDOLEDB<br /><br /> Fournisseur de données .Net pour Teradata|  
|Bases de données relationnelles Informix||(non applicable)|Fournisseur OLE DB Informix|  
|Bases de données relationnelles IBM DB2|8.1|(non applicable)|DB2OLEDB|  
|Bases de données relationnelles Sybase Adaptive Server Enterprise (ASE)|15.0.2|(non applicable)|Fournisseur OLE DB Sybase|  
|Autres bases de données relationnelles|(non applicable)|(non applicable)|Fournisseur OLE DB pour pilote ODBC|  
|Fichiers texte|(non applicable)|.txt, .tab, .csv|Fournisseur OLE DB ACE 14 pour Microsoft Access|  
|Fichiers Microsoft Excel|Excel 97-2003, 2007, 2010|.xlsx, xlsm, .xlsb, .xltx, .xltm|Fournisseur OLE DB ACE 14|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] classeur|Microsoft SQL Server 2008 R2 Analysis Services|xlsx, xlsm, .xlsb, .xltx, .xltm|ASOLEDB 10.5<br /><br /> (utilisé uniquement avec les classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] publiés dans des batteries de serveurs SharePoint où [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] est installé)|  
|Cube Analysis Services|Microsoft SQL Server 2005, 2008, 2008 R2 Analysis Services|(non applicable)|ASOLEDB 10|  
|Flux de données<br /><br /> (utilisé pour importer des données à partir de rapports Reporting Services, de documents de service Atom, de Microsoft Azure Marketplace DataMarket et d'un flux de données unique)|Format Atom 1.0<br /><br /> Base de données ou document qui est exposé en tant que Windows Communication Foundation (WCF) Data Services (anciennement ADO.NET Data Services).|.atomsvc pour un document de service qui définit un ou plusieurs flux<br /><br /> .atom pour un document de flux Web Atom|Fournisseur de flux de données Microsoft pour [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> Fournisseur de données de flux de données .NET Framework pour [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
|Fichiers de connexion de base de données Office||.odc||  
  
 <sup>1</sup> vous pouvez également utiliser le fournisseur de OLE DB pour ODBC.  
  
 <sup>2</sup> pour plus d’informations sur SQL Azure, consultez le site Web [SQL Azure](https://go.microsoft.com/fwlink/?LinkID=157856).  
  
 <sup>3</sup> pour plus d’informations sur SQL Server PDW, consultez le site web [SQL Server 2008 R2 Data Warehouse parallèle](https://go.microsoft.com/fwlink/?LinkId=150895).  
  
 <sup>4</sup> dans certains cas, l’utilisation du fournisseur de OLE DB MSDAORA peut entraîner des erreurs de connexion, en particulier avec les versions plus récentes d’Oracle. Si vous rencontrez des erreurs, nous vous recommandons d'utiliser l'un des autres fournisseurs répertoriés pour Oracle.  
  
##  <a name="unsupported-sources"></a><a name="bkmk_unsupported_ds"></a>Sources non prises en charge  
 La source de données suivante n'est pas prise en charge actuellement :  
  
-   Les documents de serveur, comme les bases de données Access déjà publiées sur SharePoint, ne peuvent pas être importés.  
  
##  <a name="tips-for-choosing-data-sources"></a><a name="bkmk_tips"></a>Conseils pour le choix des sources de données  
  
1.  Importer des tables à partir de bases de données relationnelles vous épargne certaines opérations, car les relations de *clé étrangère* sont utilisées pendant l'importation pour créer des relations entre des tables dans le générateur de modèles.  
  
2.  Importer plusieurs tables, puis supprimer celles dont vous n'avez pas besoin peut également vous épargner des opérations. Si vous importez des tables une par une, il vous faudra peut-être encore créer manuellement des relations entre les tables.  
  
3.  Les colonnes qui contiennent des données similaires dans différentes sources de données constituent la base de la création de relations dans le générateur de modèles. Si vous utilisez des sources de données hétérogènes, choisissez des tables qui comportent des colonnes pouvant être mappées à des tables d'autres sources de données qui contiennent des données identiques ou similaires.  
  
4.  Les fournisseurs OLE DB peuvent parfois offrir de meilleures performances pour des données à grande échelle. Quand vient le moment de faire votre choix parmi différents fournisseurs pour la même source de données, il est conseillé d'essayer en premier le fournisseur OLE DB.  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données &#40;&#41;tabulaire SSAS](../data-sources-ssas-tabular.md)   
 [Importer des données &#40;SSAS Tabulaire&#41;](../import-data-ssas-tabular.md)  
  
  
