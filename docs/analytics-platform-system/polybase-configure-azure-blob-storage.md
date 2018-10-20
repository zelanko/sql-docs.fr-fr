---
title: Configurer PolyBase pour accéder aux données externes dans le stockage Blob Azure | Microsoft Docs
description: Explique comment configurer PolyBase dans Parallel Data Warehouse pour se connecter à Hadoop externe.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7bbf2dface759da63bd6b9845f4e62321b1cbe76
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460630"
---
# <a name="configure-polybase-to-access-external-data-in-azure-blob-storage"></a>Configurer PolyBase pour accéder aux données externes dans le stockage Blob Azure

L’article explique comment utiliser PolyBase sur une instance de SQL Server pour interroger des données externes dans le stockage Blob Azure.

> [!NOTE]
> Actuellement, APS prend uniquement en charge le stockage standard à usage général v1 localement redondant (LRS) un objet Blob Azure.

## <a name="prerequisites"></a>Prérequis

 - Stockage d’objets Blob Azure dans votre abonnement.
 - Un conteneur est créé dans le stockage Blob Azure.

### <a name="configure-azure-blob-storage-connectivity"></a>Configurer la connectivité du stockage Blob Azure

Tout d’abord, configurez les points d’accès pour utiliser le stockage Blob Azure.

1. Exécutez [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) avec 'connectivité hadoop' la valeur est un fournisseur de stockage Blob Azure. Pour rechercher la valeur pour les fournisseurs, consultez [Configuration de la connectivité PolyBase](../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).

   ```sql  
   -- Values map to various external data sources.  
   -- Example: value 7 stands for Hortonworks HDP 2.1 to 2.6 on Linux,
   -- 2.1 to 2.3 on Windows Server, and Azure Blob storage  
   sp_configure @configname = 'hadoop connectivity', @configvalue = 7;
   GO

   RECONFIGURE
   GO
   ```  

2. Redémarrer la région de points d’accès à l’aide de la page État du Service sur [Appliance Configuration Manager](launch-the-configuration-manager.md).
  
## <a name="configure-an-external-table"></a>Configurer une table externe

Pour interroger les données dans votre stockage Blob Azure, vous devez définir une table externe à utiliser dans les requêtes Transact-SQL. Les étapes suivantes décrivent comment configurer la table externe.

1. Créer une clé principale de la base de données. Il est nécessaire pour chiffrer le secret des informations d’identification.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
   ```

1. Créer une information d’identification de niveau base de données pour le stockage d’objets Blob Azure.

   ```sql
   -- IDENTITY: any string (this is not used for authentication to Azure storage).  
   -- SECRET: your Azure storage account key.  
   CREATE DATABASE SCOPED CREDENTIAL AzureStorageCredential
   WITH IDENTITY = 'user', Secret = '<azure_storage_account_key>';
   ```

1. Créer une source de données externe avec [CREATE EXTERNAL DATA SOURCE](../t-sql/statements/create-external-data-source-transact-sql.md)...

   ```sql
   -- LOCATION:  Azure account storage account name and blob container name.  
   -- CREDENTIAL: The database scoped credential created above.  
   CREATE EXTERNAL DATA SOURCE AzureStorage with (  
         TYPE = HADOOP,
         LOCATION ='wasbs://<blob_container_name>@<azure_storage_account_name>.blob.core.windows.net',  
         CREDENTIAL = AzureStorageCredential  
   );  
   ```

1. Créer un format de fichier externe avec [CREATE EXTERNAL FILE FORMAT](../t-sql/statements/create-external-file-format-transact-sql.md).

   ```sql
   -- FORMAT TYPE: Type of format in Azure Blob storage (DELIMITEDTEXT,  RCFILE, ORC, PARQUET).
   -- In this example, the files are pipe (|) delimited
   CREATE EXTERNAL FILE FORMAT TextFileFormat WITH (  
         FORMAT_TYPE = DELIMITEDTEXT,
         FORMAT_OPTIONS (FIELD_TERMINATOR ='|',
               USE_TYPE_DEFAULT = TRUE)  
   ```

1. Créer une table externe pointant vers les données stockées dans le stockage Azure avec [CREATE EXTERNAL TABLE](../t-sql/statements/create-external-table-transact-sql.md). Dans cet exemple, les données externes contiennent des données de capteur de véhicules.

   ```sql
   -- LOCATION: path to file or directory that contains the data (relative to HDFS root).  
   CREATE EXTERNAL TABLE [dbo].[CarSensor_Data] (  
         [SensorKey] int NOT NULL,
         [CustomerKey] int NOT NULL,
         [GeographyKey] int NULL,
         [Speed] float NOT NULL,
         [YearMeasured] int NOT NULL  
   )  
   WITH (LOCATION='/Demo/',
         DATA_SOURCE = AzureStorage,  
         FILE_FORMAT = TextFileFormat  
   );  
   ```

1. Créer des statistiques sur une table externe.

   ```sql
   CREATE STATISTICS StatsForSensors on CarSensor_Data(CustomerKey, Speed)  
   ```

## <a name="polybase-queries"></a>Requêtes PolyBase

PolyBase est approprié pour trois fonctions :  
  
- Requêtes ad hoc sur les tables externes.  
- L’importation de données.  
- Exportation de données.  

Les requêtes suivantes fournissent un exemple avec des données de capteur de voiture fictif.

### <a name="ad-hoc-queries"></a>Requêtes ad hoc  

La requête ad hoc des jointures relationnelles avec des données dans le stockage Blob Azure. Il sélectionne les clients qui dépasser 35 mph, jointure de données structurées client stockée dans SQL Server avec les données de capteur de véhicules stockées dans le stockage Blob Azure.  

```sql  
SELECT DISTINCT Insured_Customers.FirstName,Insured_Customers.LastName,
       Insured_Customers. YearlyIncome, CarSensor_Data.Speed  
FROM Insured_Customers, CarSensor_Data  
WHERE Insured_Customers.CustomerKey = CarSensor_Data.CustomerKey and CarSensor_Data.Speed > 35
ORDER BY CarSensor_Data.Speed DESC  
```  

### <a name="importing-data"></a>Importation de données  

La requête suivante importe des données externes dans APS. Cet exemple importe les données pour les pilotes rapides dans les points d’accès pour effectuer une analyse plus approfondie. Pour améliorer les performances, il tire parti de la technologie Columnstore de points d’accès.  

```sql
CREATE TABLE Fast_Customers
WITH
(CLUSTERED COLUMNSTORE INDEX, DISTRIBUTION = HASH (CustomerKey))
AS
SELECT DISTINCT
      Insured_Customers.CustomerKey, Insured_Customers.FirstName, Insured_Customers.LastName,   
      Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
from Insured_Customers INNER JOIN   
(  
      SELECT * FROM CarSensor_Data where Speed > 35   
) AS SensorD  
ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
```  

### <a name="exporting-data"></a>Exportation de données  

La requête suivante exporte des données à partir de points d’accès vers le stockage Blob Azure. Il peut être utilisé pour archiver des données relationnelles à des objets Blob Azure stockage toujours être en mesure de l’interroger.

```sql
-- Export data: Move old data to Azure Blob storage while keeping it query-able via an external table.  
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] 
WITH (  
      LOCATION='/archive/customer/2009',  
      DATA_SOURCE = AzureStorage,  
      FILE_FORMAT = TextFileFormat
)  
AS
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```  

## <a name="view-polybase-objects-in-ssdt"></a>Afficher les objets PolyBase dans SSDT  

Dans SQL Server Data Tools, les tables externes sont affichées dans un dossier distinct **des Tables externes**. Les sources de données externes et les formats de fichiers externes figurent dans des sous-dossiers du dossier **Ressources externes**.  
  
![Objets PolyBase dans SSDT](media/polybase/external-tables-datasource.png)  

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur PolyBase, consultez le [What ' s PolyBase ?](../relational-databases/polybase/polybase-guide.md). 

