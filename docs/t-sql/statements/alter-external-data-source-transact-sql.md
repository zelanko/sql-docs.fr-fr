---
title: "MODIFIER la SOURCE de données externe (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL DATA SOURCE
- ALTER_EXTERNAL_DATA_SOURCE
dev_langs:
- TSQL
helpviewer_keywords:
- polybase, alter external data source statement
- ALTER EXTERNAL DATA SOURCE statement
ms.assetid: a34b9e90-199d-46d0-817a-a7e69387bf5f
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c2a0a43aefe59bc11f16445b5ee0c781179a33fa
ms.openlocfilehash: f74a105226f1ae113287f1c337c1c33e81bb09ae
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="alter-external-data-source-transact-sql"></a>MODIFIER la SOURCE de données externe (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Modifie la source de données externe utilisée pour créer une table externe. La source de données externe peut être le stockage d’objets blob Hadoop ou Azure (WASB).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Modify an external data source
-- Applies to: SQL Server (2016 or later), Azure SQL Data Warehouse,
               Parallel Data Warehouse    
ALTER EXTERNAL DATA SOURCE data_source_name SET  
    {   
        LOCATION = 'server_name_or_IP' [,] |  
        RESOURCE_MANAGER_LOCATION = <'IP address;Port'> [,] |  
        CREDENTIAL = credential_name  
    }  
    [;]  

-- Modify an external data source pointing to Azure Blob storage
-- Applies to: SQL Server (starting with 2017), Azure SQL Database,
               Azure SQL Data Warehouse, Parallel Data Warehouse
ALTER EXTERNAL DATA SOURCE data_source_name  
    WITH (   
        TYPE = BLOB_STORAGE,  
        LOCATION = 'https://storage_account_name.blob.core.windows.net'
        [, CREDENTIAL = credential_name ]
    )  
```  
  
## <a name="arguments"></a>Arguments  
 data_source_name  
 Spécifie le nom défini par l’utilisateur pour la source de données. Le nom doit être unique.  
  
 EMPLACEMENT = 'server_name_or_IP'  
 Spécifie le nom du serveur ou une adresse IP.  
  
 RESOURCE_MANAGER_LOCATION = '\<adresse IP ; Port >'  
 Spécifie l’emplacement du Gestionnaire de ressources Hadoop. Si spécifié, l’optimiseur de requête peut choisir pré-traiter les données d’une requête PolyBase à l’aide des fonctionnalités de calcul de Hadoop. Il s’agit d’une décision basée sur les coûts. Appelé des prédicats, cela peut considérablement réduire le volume de données transférées entre SQL et Hadoop et par conséquent, améliorer les performances des requêtes.  
  
 Informations d’identification = Credential_Name  
 Spécifie les informations d’identification nommée. Consultez [CREATE DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).  

TYPE = BLOB_STORAGE   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].   
Pour les opérations en bloc uniquement, `LOCATION` doit être valide l’URL vers le stockage d’objets Blob Azure. Ne placez pas  **/** , nom de fichier ou partage les paramètres de signature d’accès à la fin de la `LOCATION` URL.   
Les informations d’identification utilisées, doivent être créés à l’aide de `SHARED ACCESS SIGNATURE` comme identité. Pour plus d’informations sur les signatures d’accès partagé, consultez [Utilisation des signatures d’accès partagé (SAP)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).

  
  
## <a name="remarks"></a>Notes  
 Uniquement une source unique peut être modifiée à la fois. Les demandes simultanées de la même source de provoquent une seule instruction d’attente. Toutefois, différentes sources peuvent être modifiés en même temps. De plus, cela cette instruction peut exécuter en même temps que les autres instructions.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’autorisation ALTER ANY EXTERNAL DATA SOURCE.  
 > [!IMPORTANT]  
 >  L’autorisation ALTER ANY EXTERNAL DATA SOURCE accorde à n’importe quel principal de la possibilité de créer et modifier n’importe quel objet de source de données externe, et par conséquent, elle autorise également la possibilité d’accéder à toutes les informations d’identification de base de données d’une étendue sur la base de données. Cette autorisation doit être considérée comme des privilèges très élevés et doit donc être accordé uniquement aux entités de confiance dans le système.

  
## <a name="examples"></a>Exemples  
 L’exemple suivant modifie l’emplacement et l’emplacement de gestionnaire de ressources d’une source de données existante.  
  
```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET  
     LOCATION = 'hdfs://10.10.10.10:8020',  
     RESOURCE_MANAGER_LOCATION = '10.10.10.10:8032'  
    ;  
  
```  
  
 L’exemple suivant modifie les informations d’identification pour se connecter à une source de données existante.  
  
```  
ALTER EXTERNAL DATA SOURCE hadoop_eds SET  
   CREDENTIAL = new_hadoop_user  
    ;  
```  
  
  

