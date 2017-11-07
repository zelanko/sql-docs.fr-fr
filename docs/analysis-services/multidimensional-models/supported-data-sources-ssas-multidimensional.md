---
title: "Prise en charge des Sources de données (SSAS - multidimensionnel) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Analysis Services, data sources
- data sources [Analysis Services], about data sources
- Analysis Services, data sources
- connections [Analysis Services]
- SSAS, data sources
ms.assetid: c97e0f8d-7ddd-4941-8b51-e7832f30fbbe
caps.latest.revision: 69
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 173ba9ef24e1f05dcd3500ad8fecbad0dba98241
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="supported-data-sources-ssas---multidimensional"></a>Sources de données prises en charge (SSAS - Multidimensionnel)
  Cette rubrique décrit les types de sources de données que vous pouvez utiliser dans un modèle multidimensionnel.  
  
##  <a name="bkmk_supported_ds"></a> Sources de données prises en charge  
 Vous pouvez récupérer des données à partir des sources de données dans la table suivante. Lorsque vous installez [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], le programme d'installation n'installe pas les fournisseurs répertoriés pour chaque source de données. Certains fournisseurs ont pu être déjà installés sur votre ordinateur avec d'autres applications ; dans le cas contraire, vous devez télécharger et installer le fournisseur.  
  
> [!NOTE]  
>  Les fournisseurs tiers, tels que le Fournisseur Oracle OLE DB, permettent également de se connecter aux bases de données tierces, le support technique étant assuré par ceux-ci.  
  
|||||  
|-|-|-|-|  
|Source|Versions|Type de fichier|Fournisseurs*|  
|Bases de données Access|Microsoft Access 2010, 2013, 2016|.accdb ou .mdb|Fournisseur Microsoft Jet 4.0 OLE DB|  
|Bases de données relationnelles SQL Server*|Microsoft SQL Server 2008, 2008 R2, 2012, 2014, 2016, [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] , Microsoft Analytics Platform System (APS)<br /><br /> <br /><br /> Remarque : pour plus d’information sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] , voir [Azure.com](http://go.microsoft.com/fwlink/?LinkID=157856).<br /><br /> Remarque : le Système de plateforme d’analyse (APS) était auparavant désigné sous le nom « SQL Server Parallel Data Warehouse » (PDW). À l’origine, la connexion à PDW à partir d’Analysis Services nécessitait un fournisseur de données spécial. Ce fournisseur a été remplacé dans SQL Server 2012. À partir de SQL Server 2012, le client natif SQL Server est utilisé pour les connexions à PDW/APS. Pour plus d’informations sur APS, consultez le site web du [Système de plateforme d’analyse de Microsoft](http://www.microsoft.com/en-us/server-cloud/products/analytics-platform-system/resources.aspx).|(non applicable)|Fournisseur OLE DB pour SQL Server<br /><br /> Fournisseur OLE DB SQL Server Native Client<br /><br /> Fournisseur OLE DB SQL Server Native Client 11.0<br /><br /> Fournisseur de données .NET Framework pour SQL Client|  
|Bases de données relationnelles Oracle|Oracle 9i, 10g, 11g, 12g|(non applicable)|Fournisseur OLE DB Oracle<br /><br /> Fournisseur de données .NET Framework pour client Oracle<br /><br /> Fournisseur de données .NET Framework pour SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Bases de données relationnelles Teradata|Teradata V2R6, V12|(non applicable)|Fournisseur OLE DB TDOLEDB<br /><br /> Fournisseur de données .Net pour Teradata|  
|Bases de données relationnelles Informix|V11.10|(non applicable)|Fournisseur OLE DB Informix|  
|Bases de données relationnelles IBM DB2|8.1|(non applicable)|DB2OLEDB|  
|Bases de données relationnelles Sybase Adaptive Server Enterprise (ASE)|15.0.2|(non applicable)|Fournisseur OLE DB Sybase|  
|Autres bases de données relationnelles|(non applicable)|(non applicable)|Un fournisseur OLE°DB|  
  
 \* Les sources de données ODBC ne sont pas prises en charge dans les solutions multidimensionnelles. Bien qu’Analysis Services gère la connexion, les concepteurs de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] utilisés pour générer des solutions ne peuvent pas se connecter à une source de données ODBC, même en utilisant le pilote MSDASQL. Si vos besoins commerciaux exigent une source de données ODBC, envisagez de créer une solution tabulaire à la place.  
  
 ** Certaines fonctionnalités nécessitent une base de données relationnelle SQL Server qui s’exécute en local. Plus particulièrement, le stockage des données d’écriture différée et le stockage ROLAP requièrent une base de données relationnelle SQL Server comme la source de données sous-jacente.  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)   
 [Sources de données dans des modèles multidimensionnels](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Vues de sources de données dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  

