---
title: Sources de données prises en charge dans les modèles tabulaires 1400 SQL Server Analysis Services | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 856e15e7365128bc79d119afe267334fb8470832
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38041657"
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1400-models"></a>Sources de données pris en charge dans SQL Server Analysis Services les modèles tabulaires 1400

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

Cet article décrit les types de sources de données qui peuvent être utilisées avec les modèles tabulaires SQL Server Analysis Services (SSAS) au niveau de compatibilité 1400. 

Pour les modèles tabulaires SSAS niveaux de compatibilité 1200 et versions antérieures, consultez [des sources de données prises en charge dans les modèles 1200 tabulaires SQL Server Analysis Services](data-sources-supported-ssas-tabular.md).

Pour Azure Analysis Services, consultez [des sources de données prises en charge dans Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource).


## <a name="cloud-data-sources"></a>Sources de données cloud

|Source de données Azure  |En mémoire  |DirectQuery  |
|---------|---------|---------|
|Azure SQL Database     |   Oui      |    Oui      |
|Azure SQL Data Warehouse     |   Oui      |   Oui       |
|Stockage Blob Azure     |   Oui       |    non      |
|Stockage Table Azure    |   Oui       |    non      |
|Azure Cosmos DB      |  Oui        |  non        |
|Azure Data Lake Store     |   Oui       |    non      |
|Azure HDInsight HDFS     |     Oui     |   non       |
|Azure HDInsight Spark (bêta)     |   Oui       |   non       |
||||

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
|Base de données PostgreSQL    | Oui | non
|SAP HANA   | Oui | non
|SAP Business Warehouse    | Oui | non
|Base de données Sybase     | Oui | non
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
|Exchange Online     |
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
