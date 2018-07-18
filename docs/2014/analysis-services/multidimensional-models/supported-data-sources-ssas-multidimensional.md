---
title: Sources de données pris en charge (SSAS multidimensionnel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Analysis Services, data sources
- data sources [Analysis Services], about data sources
- Analysis Services, data sources
- connections [Analysis Services]
- SSAS, data sources
ms.assetid: c97e0f8d-7ddd-4941-8b51-e7832f30fbbe
caps.latest.revision: 59
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7c4d8c3c37b63568da63d65e9548b50c44bcc455
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301169"
---
# <a name="data-sources-supported-ssas-multidimensional"></a>Sources de données prises en charge (SSAS multidimensionnel)
  Cette rubrique décrit les types de sources de données que vous pouvez utiliser dans un modèle multidimensionnel.  
  
##  <a name="bkmk_supported_ds"></a> Sources de données prises en charge  
 Vous pouvez récupérer des données à partir des sources de données dans la table suivante. Lorsque vous installez [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], le programme d'installation n'installe pas les fournisseurs répertoriés pour chaque source de données. Certains fournisseurs ont pu être déjà installés sur votre ordinateur avec d'autres applications ; dans le cas contraire, vous devez télécharger et installer le fournisseur.  
  
> [!NOTE]  
>  Les fournisseurs tiers, tels que le Fournisseur Oracle OLE DB, permettent également de se connecter aux bases de données tierces, le support technique étant assuré par ceux-ci.  
  
|||||  
|-|-|-|-|  
|Source|Versions|Type de fichier|Fournisseurs <sup>1</sup>|  
|Bases de données Access|Microsoft Access 2007, 2010, 2013.|.accdb ou .mdb|Fournisseur Microsoft Jet 4.0 OLE DB|  
|Les bases de données relationnelles SQL Server <sup>5</sup>|Microsoft SQL Server 2005, 2008, 2008 R2, 2012, 2014 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] <sup>2</sup>, SQL Server Parallel Data Warehouse (PDW) <sup>3</sup>|(non applicable)|Fournisseur OLE DB pour SQL Server<br /><br /> Fournisseur OLE DB SQL Server Native Client<br /><br /> Fournisseur OLE DB SQL Server Native Client 11.0<br /><br /> Fournisseur de données .NET Framework pour SQL Client|  
|Bases de données relationnelles Oracle|Oracle 9i, 10g, 11g.|(non applicable)|Fournisseur OLE DB Oracle<br /><br /> Fournisseur de données .NET Framework pour client Oracle<br /><br /> Fournisseur de données .NET Framework pour SQL Server<br /><br /> Fournisseur OLE DB MSDAORA <sup>4</sup><br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Bases de données relationnelles Teradata|Teradata V2R6, V12|(non applicable)|Fournisseur OLE DB TDOLEDB<br /><br /> Fournisseur de données .Net pour Teradata|  
|Bases de données relationnelles Informix|V11.10|(non applicable)|Fournisseur OLE DB Informix|  
|Bases de données relationnelles IBM DB2|8.1|(non applicable)|DB2OLEDB|  
|Bases de données relationnelles Sybase Adaptive Server Enterprise (ASE)|15.0.2|(non applicable)|Fournisseur OLE DB Sybase|  
|Autres bases de données relationnelles|(non applicable)|(non applicable)|Un fournisseur OLE°DB|  
  
 <sup>1</sup> sources de données ODBC ne sont pas pris en charge dans les solutions multidimensionnelles. Bien qu’Analysis Services gère la connexion, les concepteurs de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] utilisés pour générer des solutions ne peuvent pas se connecter à une source de données ODBC, même en utilisant le pilote MSDASQL. Si vos besoins commerciaux exigent une source de données ODBC, envisagez de créer une solution tabulaire à la place.  
  
 <sup>2</sup> pour plus d’informations, consultez [!INCLUDE[ssSDS](../../includes/sssds-md.md)], dans [azure.microsoft.com](http://go.microsoft.com/fwlink/?LinkID=157856).  
  
 <sup>3</sup> pour plus d’informations sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] PDW, consultez [SQL Server Parallel Data Warehouse](http://go.microsoft.com/fwlink/?LinkId=150895).  
  
 <sup>4</sup> dans certains cas, l’utilisation du fournisseur OLE DB MSDAORA peut entraîner des erreurs de connexion, en particulier avec les versions plus récentes d’Oracle. Si vous rencontrez des erreurs, nous vous recommandons d'utiliser l'un des autres fournisseurs répertoriés pour Oracle.  
  
 <sup>5</sup> certaines fonctionnalités nécessitent une base de données relationnelle SQL Server qui s’exécute en local. Plus particulièrement, le stockage des données d'écriture différée et le stockage ROLAP requièrent une base de données relationnelle SQL Server comme la source de données sous-jacente.  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données prises en charge &#40;SSAS tabulaire&#41;](../tabular-models/data-sources-supported-ssas-tabular.md)   
 [Sources de données dans les modèles multidimensionnels](data-sources-in-multidimensional-models.md)   
 [Vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md)  
  
  
