---
title: "CRÉER des informations d’identification (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREDENTIAL_TSQL
- SQL13.SWB.CREDENTIAL.GENERAL.F1
- CREATE CREDENTIAL
- CREATE_CREDENTIAL_TSQL
- CREDENTIAL
dev_langs: TSQL
helpviewer_keywords:
- SECRET clause
- authentication [SQL Server], credentials
- CREATE CREDENTIAL statement
- credentials [SQL Server], CREATE CREDENTIAL statement
ms.assetid: d5e9ae69-41d9-4e46-b13d-404b88a32d9d
caps.latest.revision: "51"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f0e46404d775da09f4aaeb7b9640dd2a35d3cfa2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="create-credential-transact-sql"></a>CREATE CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée une information d’identification au niveau du serveur. Informations d’identification sont un enregistrement qui contient les informations d’authentification qui sont requis pour se connecter à une ressource en dehors de SQL Server. La plupart des informations d'identification incluent un utilisateur et un mot de passe Windows. Par exemple, l’enregistrement d’une sauvegarde de base de données à un emplacement peut nécessiter SQL Server fournir des informations d’identification spéciale pour accéder à cet emplacement. Pour plus d’informations, consultez [informations d’identification (moteur de base de données)](../../relational-databases/security/authentication-access/credentials-database-engine.md).
  
> [!NOTE]  
>  Pour rendre les informations d’identification lors de l’utilisation du niveau de la base de données [CREATE DATABASE SCOPED CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-database-scoped-credential-transact-sql.md). Utiliser les informations d’identification au niveau du serveur lorsque vous avez besoin d’utiliser les mêmes informations d’identification pour plusieurs bases de données sur le serveur. Une information d’identification de l’étendue de base de données permet de rendre la base de données plus portable. Lorsqu’une base de données est déplacé vers un nouveau serveur, les informations d’identification de base de données applique seront déplacent avec elle. Informations d’identification d’une étendue de base de données utilisez sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE CREDENTIAL credential_name   
WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
        [ FOR CRYPTOGRAPHIC PROVIDER cryptographic_provider_name ]  
```  
  
## <a name="arguments"></a>Arguments  
 *credential_name*  
 Spécifie le nom des informations d'identification créées. *credential_name* ne peut pas commencer par le signe dièse (#). Les informations d'identification système commencent avec ##.  Lorsque vous utilisez une signature d’accès partagé (SAS), ce nom doit correspondre le chemin d’accès du conteneur, commencer par https et ne doit pas contenir une barre oblique. Consultez l’exemple D ci-dessous.  
  
 IDENTITÉ **='***identity_name***'**  
 Spécifie le nom du compte à utiliser lors d'une connexion en dehors du serveur. Lorsque les informations d’identification sont utilisée pour accéder au coffre de clés Azure, le **identité** est le nom de l’archivage de clé. Consultez l'exemple C ci-dessous. Lorsque les informations d’identification à l’aide de signature d’accès partagé (SAS), le **identité** est *la SIGNATURE d’accès partagé*. Consultez l’exemple D ci-dessous.  
  
 SECRET **='***secret***'**  
 Spécifie le secret requis pour l'authentification sortante.  
  
 Lorsque les informations d’identification sont utilisée pour accéder au coffre de clés Azure à le **SECRET** argument de **CREATE CREDENTIAL** requiert le  *\<ID Client >* (sans tirets) et  *\<Secret >* d’un **Principal du Service** dans Azure Active Directory soient passés ensemble sans espace entre eux. Consultez l'exemple C ci-dessous. Lorsque les informations d’identification à l’aide de signature d’accès partagé, le **SECRET** est le jeton de signature d’accès partagé. Consultez l’exemple D ci-dessous.  Pour plus d’informations sur la création d’une stratégie d’accès stockée et une signature d’accès partagé sur un conteneur Azure, consultez [leçon 1 : créer une stratégie d’accès stockée et une signature d’accès partagé sur un conteneur Azure](../../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md).  
  
 POUR le fournisseur de services cryptographiques *cryptographic_provider_name*  
 Spécifie le nom d’un *entreprise fournisseur EKM (Key Management)*. Pour plus d’informations sur la gestion de clés, consultez [gestion de clés Extensible &#40; Gestion de clés extensible &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Notes  

 Lorsque IDENTITY correspond à un utilisateur Windows, le secret peut être le mot de passe. Le secret est chiffré à l'aide de la clé principale de service. Si la clé principale de service est régénérée, le secret est chiffré de nouveau au moyen de la nouvelle clé principale de service.  
  
 Après avoir créé une information d’identification, vous pouvez mapper à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion à l’aide de [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) ou [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md). A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion peut être mappée à une seule information d’identification, mais une seule information d’identification peut être mappée à plusieurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexions. Pour plus d’informations, consultez [informations d’identification &#40; moteur de base de données &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md). Informations d’identification au niveau du serveur ne peuvent pas être mappée à une connexion, pas à un utilisateur de base de données. 
  
 Informations d’identification sont visibles dans le [sys.credentials](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md) affichage catalogue.  
  
 En l'absence d'une information d'identification mappée à une connexion pour le fournisseur, l'information d'identification mappée au compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est utilisée.  
  
 Une connexion peut avoir plusieurs informations d'identification mappées à elle, à condition qu'elles soient utilisées avec des fournisseurs distinctifs. Il ne doit y avoir qu'une seule information d'identification mappée par fournisseur par connexion. La même information d'identification peut être mappée à d'autres connexions.  
  
## <a name="permissions"></a>Permissions  
 Requiert **ALTER ANY CREDENTIAL** autorisation.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-basic-example"></a>A. Exemple de base  
 L'exemple ci-dessous crée des informations d'identification nommées `AlterEgo`. Les informations d'identification contiennent l'utilisateur Windows `Mary5` et un mot de passe.  
  
```  
CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
    SECRET = '<EnterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-credential-for-ekm"></a>B. Création d'informations d'identification pour EKM  
 L'exemple suivant utilise un compte précédemment créé, `User1OnEKM`, sur un module EKM au moyen des outils d'administration EKM, avec un type de compte de base et un mot de passe. Le **sysadmin** compte sur le serveur crée des informations d’identification sont utilisée pour se connecter au compte de gestion de clés extensible et l’affecte à la `User1` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte :  
  
```  
CREATE CREDENTIAL CredentialForEKM  
    WITH IDENTITY='User1OnEKM', SECRET='<EnterStrongPasswordHere>'  
    FOR CRYPTOGRAPHIC PROVIDER MyEKMProvider;  
GO  
  
/* Modify the login to assign the cryptographic provider credential */  
ALTER LOGIN Login1  
ADD CREDENTIAL CredentialForEKM;  
  
/* Modify the login to assign a non cryptographic provider credential */   
ALTER LOGIN Login1  
WITH CREDENTIAL = AlterEgo;  
GO  
```  
  
### <a name="c-creating-a-credential-for-ekm-using-the-azure-key-vault"></a>C. Création d'informations d'identification pour EKM à l'aide d’Azure Key Vault  
 L’exemple suivant crée un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des informations d’identification pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)] à utiliser lors de l’accès le coffre de clés Azure à l’aide de la **connecteur SQL Server pour Microsoft Azure Key Vault**. Pour obtenir un exemple complet de l’utilisation de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connecteur, consultez [Extensible Key Management à l’aide de Azure Key Vault &#40; SQL Server &#41; ](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
> [!IMPORTANT]  
>  L'argument **IDENTITY** de **CREATE CREDENTIAL** nécessite le nom du coffre de clés. Le **SECRET** argument de **CREATE CREDENTIAL** requiert le  *\<ID Client >* (sans tirets) et  *\<Secret >* soient passés ensemble sans espace entre eux.  
  
 Dans l'exemple suivant, l' **ID client** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) est débarrassé des tirets et entré comme chaîne `EF5C8E094D2A4A769998D93440D8115D` , tandis que la **clé secrète** est représentée par la chaîne *SECRET_DBEngine*.  
  
```  
USE master;  
CREATE CREDENTIAL Azure_EKM_TDE_cred   
    WITH IDENTITY = 'ContosoKeyVault',   
    SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine'   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
```  
  
 L’exemple suivant crée les mêmes informations d’identification à l’aide de variables pour le **ID Client** et **Secret** chaînes, qui sont ensuite concaténées pour former le **SECRET** argument. Le **remplacer** fonction est utilisée pour supprimer les tirets de l’ID Client.  
  
```  
DECLARE @AuthClientId uniqueidentifier = 'EF5C8E09-4D2A-4A76-9998-D93440D8115D';  
DECLARE @AuthClientSecret varchar(200) = 'SECRET_DBEngine';  
DECLARE @pwd varchar(max) = REPLACE(CONVERT(varchar(36), @AuthClientId) , '-', '') + @AuthClientSecret;  
  
EXEC ('CREATE CREDENTIAL Azure_EKM_TDE_cred   
    WITH IDENTITY = 'ContosoKeyVault', SECRET = ''' + @PWD + '''   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;');  
```  
  
### <a name="d-creating-a-credential-using-a-sas-token"></a>D. Création d’une information d’identification à l’aide d’un jeton SAS  
 **S’applique aux**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] via [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
 L’exemple suivant crée une information d’identification d’accès partagé signature à l’aide d’un jeton SAP.  Pour un didacticiel sur la création d’une stratégie d’accès stockée et une signature d’accès partagé sur un conteneur Azure, puis en créant une information d’identification à l’aide de la signature d’accès partagé, consultez [didacticiel : à l’aide du service de stockage d’objets Blob Microsoft Azure avec les bases de données SQL Server 2016](Tutorial:%20Using%20the%20Microsoft%20Azure%20Blob%20storage%20service%20with%20SQL%20Server%202016%20databases.md).  
  
> [!IMPORTANT]  
>  LE **nom d’identification** argument requiert que le nom correspond le chemin d’accès du conteneur, commencer par https et ne contient pas une barre oblique. Le **identité** argument requiert le nom, *SIGNATURE d’accès partagé*. Le **SECRET** argument requiert le jeton de signature d’accès partagé.  
  
```  
USE master  
CREATE CREDENTIAL [https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>] -- this name must match the container path, start with https and must not contain a trailing forward slash.  
   WITH IDENTITY='SHARED ACCESS SIGNATURE' -- this is a mandatory string and do not change it.   
   , SECRET = 'sharedaccesssignature' –- this is the shared access signature token   
GO    
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations d’identification &#40; moteur de base de données &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [ALTER CREDENTIAL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-credential-transact-sql.md)   
 [SUPPRIMER les informations d’identification &#40; Transact-SQL &#41;](../../t-sql/statements/drop-credential-transact-sql.md)   
 [CRÉER des informations d’identification inclus dans l’étendue de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [Leçon 2 : Créer des informations d’identification SQL Server à l’aide d’une signature d’accès partagé](../../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)   
 [Signatures d’accès partagé](https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/)  
  
  
