---
title: Accès en bloc à des données dans Stockage Blob Azure
description: Exemples de Transact-SQL qui utilisent BULK INSERT et OPENROWSET pour accéder aux données dans un compte de stockage Azure Blob.
ms.date: 10/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], from Azure blob storage
- Azure blob storage, bulk import to SQL Server
- BULK INSERT, Azure blob storage
- OPENROWSET, Azure blob storage
ms.assetid: f7d85db3-7a93-400e-87af-f56247319ecd
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.custom: seo-lt-2019
ms.openlocfilehash: b067b668cfdf0dc42596d7fb6858240ad8d944e9
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91867715"
---
# <a name="examples-of-bulk-access-to-data-in-azure-blob-storage"></a>Exemples d’accès en bloc à des données dans Stockage Blob Azure

[!INCLUDE[sqlserver2017-asdb](../../includes/applies-to-version/sqlserver2017-asdb.md)]

Les instructions `BULK INSERT` et `OPENROWSET` peuvent accéder directement à un fichier dans Stockage Blob Azure. Les exemples suivants utilisent des données d’un fichier de valeurs séparées par des virgules (CSV) nommé `inv-2017-01-19.csv`, stocké dans un conteneur nommé `Week3` dans un compte de stockage nommé `newinvoices`. Le chemin du fichier de format peut être utilisé, mais il n’est pas inclus dans ces exemples.

L’accès en bloc au stockage Blob Azure à partir de SQL Server nécessite au moins [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.

> [!IMPORTANT]
> Tous les chemins du conteneur et des fichiers sur les objets blob sont `CASE SENSITIVE`. S’ils ne sont pas corrects, l’erreur suivante peut être retournée : « Chargement en masse impossible. Le fichier « fichier.csv » n’existe pas ou vous ne disposez pas des droits d’accès au fichier. »

## <a name="create-the-credential"></a>Créer les informations d’identification

Tous les exemples suivants nécessitent des informations d’identification incluses dans l’étendue de la base de données faisant référence à une signature d’accès partagé.

> [!IMPORTANT]
> La source de données externe doit être créée avec des informations d’identification incluses dans l’étendue de la base de données utilisant l’identité `SHARED ACCESS SIGNATURE`. Pour créer une signature d’accès partagé pour votre compte de stockage, examinez la propriété **Signature d’accès partagé** dans la page de propriétés du compte de stockage, dans le portail Azure. Pour plus d’informations sur les signatures d’accès partagé, consultez [Utilisation des signatures d’accès partagé (SAP)](/azure/storage/storage-dotnet-shared-access-signature-part-1). Pour plus d’informations sur les informations d’identification, consultez [CREATE DATABASE SCOPED CREDENTIAL](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

Créez des informations d’identification incluses dans l’étendue de la base de données avec `IDENTITY` qui doit avoir la valeur `SHARED ACCESS SIGNATURE`. Utilisez le jeton SAS généré pour le compte de stockage d’objets blob. Vérifiez que votre jeton SAS ne commence pas par `?`, que vous disposez au moins d’une autorisation de lecture sur l’objet qui doit être chargé et que la période d’expiration est valide (toutes les dates sont exprimées en heure UTC).

Par exemple :

```sql
CREATE DATABASE SCOPED CREDENTIAL UploadInvoices
WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
SECRET = 'sv=2018-03-28&ss=b&srt=sco&sp=rwdlac&se=2019-08-31T02:25:19Z&st=2019-07-30T18:25:19Z&spr=https&sig=KS51p%2BVnfUtLjMZtUTW1siyuyd2nlx294tL0mnmFsOk%3D';
```

## <a name="accessing-data-in-a-csv-file-referencing-an-azure-blob-storage-location"></a>Accès aux données dans un fichier CSV faisant référence à un emplacement de stockage Blob Azure

L’exemple suivant utilise une source de données externe qui pointe vers un compte de stockage Azure, nommé `MyAzureInvoices`.

```sql
CREATE EXTERNAL DATA SOURCE MyAzureInvoices
    WITH (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net',
        CREDENTIAL = UploadInvoices
    );
```

L’instruction `OPENROWSET` ajoute ensuite le nom du conteneur (`week3`) à la description du fichier. Le fichier est nommé `inv-2017-01-19.csv`.

```sql
SELECT * FROM OPENROWSET(
   BULK 'week3/inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoices',
   FORMAT = 'CSV',
   FORMATFILE='invoices.fmt',
   FORMATFILE_DATA_SOURCE = 'MyAzureInvoices'
   ) AS DataFile;   
```

À l’aide de `BULK INSERT`, utilisez le conteneur et la description du fichier :

```sql
BULK INSERT Colors2
FROM 'week3/inv-2017-01-19.csv'
WITH (DATA_SOURCE = 'MyAzureInvoices',
      FORMAT = 'CSV');
```

## <a name="accessing-data-in-a-csv-file-referencing-a-container-in-an-azure-blob-storage-location"></a>Accès aux données dans un fichier CSV faisant référence à un conteneur à un emplacement de stockage Blob Azure

L’exemple suivant utilise une source de données externe qui pointe vers un conteneur (nommé `week3`) dans un compte de stockage Azure.

```sql
CREATE EXTERNAL DATA SOURCE MyAzureInvoicesContainer
    WITH (
        TYPE = BLOB_STORAGE,
        LOCATION = 'https://newinvoices.blob.core.windows.net/week3',
        CREDENTIAL = UploadInvoices
    );
```

L’instruction `OPENROWSET` n’ajoute pas ensuite le nom du conteneur à la description du fichier :

```sql
SELECT * FROM OPENROWSET(
   BULK 'inv-2017-01-19.csv',
   DATA_SOURCE = 'MyAzureInvoicesContainer',
   FORMAT = 'CSV',
   FORMATFILE='invoices.fmt',
   FORMATFILE_DATA_SOURCE = 'MyAzureInvoices'
   ) AS DataFile;
```

À l’aide de `BULK INSERT`, n’utilisez pas le nom du conteneur dans la description du fichier :

```sql
BULK INSERT Colors2
FROM 'inv-2017-01-19.csv'
WITH (DATA_SOURCE = 'MyAzureInvoicesContainer',
      FORMAT = 'CSV');
```

## <a name="see-also"></a>Voir aussi

- [CREATE DATABASE SCOPED CREDENTIAL](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md)
- [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)
- [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)