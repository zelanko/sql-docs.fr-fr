---
title: "CRÉER des informations d’identification inclus dans l’étendue de base de données (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE SCOPED CREDENTIAL
- DATABASE_SCOPED_CREDENTIAL_TSQL
- SCOPED_TSQL
- CREATE_DATABASE_SCOPED_CREDENTIAL
- CREATE_DATABASE_SCOPED_CREDENTIAL_TSQL
- SCOPED_CREDENTIAL_TSQL
- SCOPED_CREDENTIAL
helpviewer_keywords:
- DATABASE SCOPED CREDENTIAL statement
- credentials [SQL Server], DATABASE SCOPED CREDENTIAL statement
ms.assetid: fe830577-11ca-44e5-953b-2d589d54d045
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: 49ff2aa300fc8f8e74424ae6e334bee823e8176c
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---
# <a name="create-database-scoped-credential-transact-sql"></a>CRÉER des informations d’identification inclus dans l’étendue de base de données (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Crée une information d’identification de base de données. Informations d’identification de la base de données ne sont pas mappée à un utilisateur de connexion ou de la base de données du serveur. Les informations d’identification sont utilisée par la base de données pour l’accès à l’emplacement externe à chaque fois que la base de données est une opération qui requiert l’accès.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 
CREATE DATABASE SCOPED CREDENTIAL credential_name   
WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
  
```  
  
## <a name="arguments"></a>Arguments  
 *credential_name*  
 Spécifie le nom de l’information d’identification de l’étendue de la base de données en cours de création. *credential_name* ne peut pas commencer par le signe dièse (#). Les informations d'identification système commencent avec ##.  
  
 IDENTITÉ **='***identity_name***'**  
 Spécifie le nom du compte à utiliser lors d'une connexion en dehors du serveur. Pour importer un fichier à partir du stockage d’objets Blob Azure, le nom de l’identité doit être `SHARED ACCESS SIGNATURE`.  Pour plus d’informations sur les signatures d’accès partagé, consultez [à l’aide d’accès partagé des Signatures (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).  
  
 SECRET **='***secret***'**  
 Spécifie le secret requis pour l'authentification sortante. `SECRET`est requis pour importer un fichier de stockage d’objets Blob Azure.   
>  [!WARNING]
>  La valeur de clé SAS pourrait commencer par un ' ?' (point d’interrogation). Lorsque vous utilisez la clé SAS, vous devez supprimer l’interligne ' ?'. Dans le cas contraire, vos efforts risque d’être bloqués.  
  
## <a name="remarks"></a>Notes  
 Informations d’identification d’une étendue de la base de données sont un enregistrement qui contient les informations d’authentification qui sont requis pour se connecter à une ressource en dehors de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La plupart des informations d'identification incluent un utilisateur et un mot de passe Windows.  
  
 Avant de créer une base de données étendus aux informations d’identification, la base de données doit avoir une clé principale pour protéger les informations d’identification. Pour plus d’informations, consultez [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md).  
  
 Lorsque IDENTITY correspond à un utilisateur Windows, le secret peut être le mot de passe. Le secret est chiffré à l'aide de la clé principale de service. Si la clé principale de service est régénérée, le secret est chiffré de nouveau au moyen de la nouvelle clé principale de service.  
   
 Informations d’identification de base de données d’une étendue sont visibles dans le [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) affichage catalogue.  
  
 
 Hereare certaines applications de base de données étendue des informations d’identification :  
  
- [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]utilise les informations d’identification d’une étendue de la base de données pour accéder au stockage d’objets blob Azure de non public ou clusters Hadoop sécurisé Kerberos avec PolyBase. Pour plus d’informations, consultez [créer une SOURCE de données externe (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md).  

- [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]utilise les informations d’identification d’une étendue de la base de données pour le stockage d’objets blob Azure de non public de l’accès avec PolyBase. Pour plus d’informations, consultez [créer une SOURCE de données externe (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md).
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]utilise la base de données des informations d’identification incluses dans l’étendue pour sa fonctionnalité de requête globale. Ceci est la possibilité d’interroger plusieurs partitions de base de données.  
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]utilise les informations d’identification de la portée de la base de données pour écrire des fichiers d’événements étendus pour le stockage d’objets blob Azure.  
  
- [!INCLUDE[ssSDS](../../includes/sssds-md.md)]utilise les informations d’identification incluses dans l’étendue pour les pools élastiques de base de données. Pour plus d’informations, consultez [maîtriser la croissance des bases de données élastiques](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)  

- [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) et [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) utilisation de base de données étendue des informations d’identification pour accéder aux données depuis le stockage blob Azure. Pour plus d’informations, consultez [exemples d’accès en bloc à des données dans le stockage d’objets Blob Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md). 
  
## <a name="permissions"></a>Permissions  
 Requiert **contrôle** autorisation sur la base de données.  
  
## <a name="examples"></a>Exemples  
### <a name="a-creating-a-database-scoped-credential-for-your-application"></a>A. Création d’une base de données d’une étendue d’informations d’identification pour votre application.
 L’exemple suivant crée les informations d’identification de la portée de la base de données appelée `AppCred`. Les informations d’identification de base de données applique contient l’utilisateur Windows `Mary5` et un mot de passe.  
  
```tsql  
-- Create a db master key if one does not already exist, using your own password.  
CREATE MASTER KEY ENCRYPTION BY PASSWORD='<EnterStrongPasswordHere>';  
  
-- Create a database scoped credential.  
CREATE DATABASE SCOPED CREDENTIAL AppCred WITH IDENTITY = 'Mary5',   
    SECRET = '<EnterStrongPasswordHere>';  
GO  
```  

### <a name="b-creating-a-database-scoped-credential-for-a-shared-access-signature"></a>B. Création d’une base de données d’une étendue d’informations d’identification d’une signature d’accès partagé.   
L’exemple suivant crée une information d’identification de la portée de la base de données qui peut être utilisée pour créer un [source de données externe](../../t-sql/statements/create-external-data-source-transact-sql.md), ce qui peut faire opérations en bloc, telles que [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) et [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md). Signatures d’accès partagé ne peut pas être utilisés avec PolyBase dans SQL Server, de points d’accès ou d’entrepôt de données SQL.
```tsql
CREATE DATABASE SCOPED CREDENTIAL MyCredentials  
WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
SECRET = 'QLYMgmSXMklt%2FI1U6DcVrQixnlU5Sgbtk1qDRakUBGs%3D';
```
  
### <a name="c-creating-a-database-scoped-credential-for-polybase-connectivity-to-azure-data-lake-store"></a>C. Création d’une base de données d’une étendue d’informations d’identification pour la connectivité PolyBase à Azure Data Lake Store.  
L’exemple suivant crée une information d’identification de la portée de la base de données qui peut être utilisée pour créer un [source de données externe](../../t-sql/statements/create-external-data-source-transact-sql.md), qui peut être utilisé par PolyBase dans Azure SQL Data Warehouse.

Azure Data Lake Store utilise une Application Active Directory de Azure pour l’authentification de Service.
Veuillez [créer une application AAD](https://docs.microsoft.com/en-us/azure/data-lake-store/data-lake-store-authenticate-using-active-directory) client_id, OAuth_2.0_Token_EndPoint et clé de document avant d’essayer de créer des informations d’identification d’une étendue de la base de données.

```tsql
CREATE DATABASE SCOPED CREDENTIAL ADL_User
WITH
    IDENTITY = '<client_id>@\<OAuth_2.0_Token_EndPoint>'
    SECRET = '<key>'
;
```  
  
  
  
## <a name="more-information"></a>Informations complémentaires  
 [Informations d’identification &#40; moteur de base de données &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [MODIFIER les informations d’identification inclus dans l’étendue de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [SUPPRIMER les informations d’identification inclus dans l’étendue de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [Sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

