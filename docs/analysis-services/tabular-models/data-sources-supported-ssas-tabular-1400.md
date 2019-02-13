---
title: Sources de données prises en charge dans les modèles tabulaires 1400 SQL Server Analysis Services | Microsoft Docs
ms.date: 02/12/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4c900c6f1683b9f4c96355a759c604022515d2ce
ms.sourcegitcommit: 89a7bd9ccbcb19bb92a1f4ba75576243a58584e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56159754"
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1400-models"></a>Sources de données pris en charge dans SQL Server Analysis Services les modèles tabulaires 1400

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

Cet article décrit les types de sources de données qui peuvent être utilisées avec les modèles tabulaires SQL Server Analysis Services (SSAS) au niveau de compatibilité 1400. 

Pour les modèles tabulaires SSAS niveaux de compatibilité 1200 et versions antérieures, consultez [des sources de données prises en charge dans les modèles 1200 tabulaires SQL Server Analysis Services](data-sources-supported-ssas-tabular.md).

Pour Azure Analysis Services, consultez [des sources de données prises en charge dans Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource).


## <a name="cloud-data-sources"></a>Sources de données cloud

|Source de données  |En mémoire  |DirectQuery  |
|---------|---------|---------|
|Azure SQL Database     |   Oui      |    Oui      |
|Azure SQL Data Warehouse.     |   Oui      |   Oui       |
|Stockage Blob Azure     |   Oui       |    Non      |
|Stockage Table Azure    |   Oui       |    Non      |
|Azure Cosmos DB     |  Oui        |  Non        |
|Azure Data Lake Store (Gen1)<sup>[1](#gen2)</sup>      |   Oui       |    Non      |
|Azure HDInsight HDFS    |     Oui     |   Non       |
|Azure HDInsight Spark <sup> [2](#databricks)</sup>     |   Oui       |   Non       |
||||

<a name="gen2">1</a> -ADLS Gen2 n’est actuellement pas pris en charge.   
<a name="databricks">2</a> - azure Databricks en utilisant le connecteur n’est actuellement pas pris en charge de Spark.   



**Fournisseur**   
En mémoire et les modèles DirectQuery connexion aux sources de données Azure utilisent le fournisseur de données .NET Framework pour SQL Server.

## <a name="on-premises-data-sources"></a>Sources de données locales

### <a name="supported-by-in-memory-and-directquery-models"></a>Pris en charge en mémoire et les modèles DirectQuery

|Source de données | Fournisseur en mémoire | Fournisseur DirectQuery |
|  --- | --- | --- |
| SQL Server |SQL Server Native Client 11.0, fournisseur Microsoft OLE DB pour SQL Server, le fournisseur de données .NET Framework pour SQL Server | Fournisseur de données .NET Framework pour SQL Server |
| SQL Server Data Warehouse |SQL Server Native Client 11.0, fournisseur Microsoft OLE DB pour SQL Server, le fournisseur de données .NET Framework pour SQL Server | Fournisseur de données .NET Framework pour SQL Server |
| Oracle |Fournisseur Microsoft OLE DB pour Oracle, fournisseur de données Oracle pour .NET |Fournisseur de données Oracle pour .NET | |
| Teradata |Fournisseur OLE DB pour Teradata, fournisseur de données Teradata pour .NET |Fournisseur de données Teradata pour .NET | |
| | | |

> [!NOTE]
> Pour les modèles en mémoire, les fournisseurs OLE DB peuvent offrir de meilleures performances pour les données à grande échelle. Lors du choix entre différents fournisseurs pour la même source de données, essayez tout d’abord le fournisseur OLE DB.  

### <a name="supported-by-in-memory-models-only"></a>Prise en charge par les modèles en mémoire uniquement

|Base de données  |
|---------|---------|---------|
|Base de données Access     | 
|SQL Server Analysis Services     | 
|IBM Informix (bêta) | 
|Document JSON     | 
|Lignes à partir du fichier binaire     | 
|Base de données MySQL     | 
|Base de données PostgreSQL    | Oui | Non
|SAP HANA   | Oui | Non
|SAP Business Warehouse    | Oui | Non
|Base de données Sybase     | Oui | Non
|||

|Fichier  |  
|---------|---------|
|Classeur Excel     |
|Dossier     | 
|JSON | 
|Texte/CSV    | 
|Table XML    | 
|||

|Services en ligne  |  
|---------|---------|
|Dynamics 365      |
|Exhange Online     |
|Objets Salesforce    | 
|Rapports Salesforce     |
|Liste SharePoint Online     |
|||

|Autres  |  
|---------|---------|
|Active Directory      | 
|Exhange     |  
|Flux OData     | 
|Requête ODBC     | 
|OLE DB  | 
|Liste SharePoint | 
|||

## <a name="see-also"></a>Voir aussi

[Sources de données pris en charge dans SQL Server Analysis Services les modèles 1200 tabulaires](data-sources-supported-ssas-tabular.md)

[Sources de données prises en charge dans Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   
