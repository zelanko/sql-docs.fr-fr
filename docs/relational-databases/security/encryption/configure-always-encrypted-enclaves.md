---
title: Configurer Always Encrypted avec enclaves sécurisées | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 866d71333297b609642707a793b27c735d29057d
ms.sourcegitcommit: c6e71ed14198da67afd7ba722823b1af9b4f4e6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54327885"
---
# <a name="configure-always-encrypted-with-secure-enclaves"></a>Configurer Always Encrypted avec enclaves sécurisées

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[Always Encrypted avec enclaves sécurisés](always-encrypted-enclaves.md) étend la fonctionnalité [Always Encrypted](always-encrypted-database-engine.md) existante pour activer des fonctionnalités plus complexes sur les données sensibles tout en préservant la confidentialité des données.

Pour configurer Always Encrypted avec enclaves sécurisées, utilisez le flux de travail suivant :

1. Configurez l’attestation de Service de Guardian hôte (SGH).
2. Installez [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] sur l’ordinateur SQL Server.
3. Installez les outils sur l’ordinateur client/développement.
4. Configurez le type d’enclave dans votre instance SQL Server.
5. Approvisionnez les clés prenant en charge les enclaves.
6. Chiffrez des colonnes qui contiennent des données sensibles.

> [!NOTE]
> Pour obtenir un tutoriel pas à pas sur la manière de tester votre environnement de test et d’essayer la fonctionnalité Always Encrypted avec enclaves sécurisées dans SSMS, consultez [Tutoriel : bien démarrer avec Always Encrypted avec enclaves sécurisées en utilisant SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md).

## <a name="configure-your-environment"></a>Configurer votre environnement

Pour utiliser des enclaves sécurisées avec Always Encrypted, votre environnement requiert Windows Server 2019 (préversion), SQL Server Management Studio (SSMS) 18.0 (préversion), .NET Framework et plusieurs autres composants. Les sections suivantes fournissent des détails et des liens pour obtenir les composants requis.

### <a name="sql-server-computer-requirements"></a>Configuration requise de SQL Server

L’ordinateur qui exécute SQL Server a besoin du système d’exploitation et de la version de SQL Server suivants :

*SQL Server* :

- [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)] ou ultérieur

*Windows* :

- Windows 10 Enterprise, version 1809
- Windows Server DataCenter (canal semi-annuel), version 1809
- Windows Server 2019 Datacenter

> [!IMPORTANT]
> L’ordinateur SQL Server doit être configuré comme hôte Service Guardian attesté par SGH. L’attestation TPM est la méthode de l’attestation d’enclave recommandée pour les environnements de production et nécessite que SQL Server s’exécute sur une machine physique et non sur une machine virtuelle. Les machines virtuelles conviennent uniquement aux environnements de préproduction.

### <a name="hgs-computer-requirements"></a>Configuration requise de l’ordinateur SGH

Un seul ordinateur SGH est suffisant durant les tests et le prototypage. Pour la production, un cluster de basculement Windows avec 3 ordinateurs est fortement recommandé.

Service Guardian hôte (SGH) Windows doit être installé sur des ordinateurs SGH distincts et non sur le même ordinateur que SQL Server. Pour plus d’informations sur la configuration requise des ordinateurs SGH et la configuration, consultez [Configuration du Service Guardian hôte pour Always Encrypted dans SQL Server](https://docs.microsoft.com/windows-server/security/set-up-hgs-for-always-encrypted-in-sql-server).


### <a name="determine-your-attestation-service-url"></a>Déterminer votre URL de service d’attestation

Pour déterminer l’URL du service d’attestation, vous devez configurer vos outils et applications :

1. Connectez-vous à votre ordinateur SQL Server en tant qu’administrateur.
2. Démarrez PowerShell en tant qu'administrateur.
3. Exécutez [Get-HGSClientConfiguration](https://docs.microsoft.com/powershell/module/hgsclient/get-hgsclientconfiguration).
4. Écrire et enregistrez la propriété AttestationServerURL. Cela devrait ressembler à ceci : `https://x.x.x.x/Attestation`.


### <a name="install-tools"></a>Installer des outils

Installez les outils suivants sur l’ordinateur client/développement :

1. [.NET Framework 4.7.2](https://www.microsoft.com/net/download/dotnet-framework-runtime).
2. [SSMS 18.0 ou version ultérieure](../../../ssms/download-sql-server-management-studio-ssms.md).
3. [Module SQL Server PowerShell](../../../powershell/download-sql-server-ps-module.md), version 21.1 oui ultérieure.
4. [Visual Studio (version 2017 ou ultérieure recommandée)](https://visualstudio.microsoft.com/downloads/).
5. [Pack développeur pour .NET Framework 4.7.2](https://www.microsoft.com/net/download/visual-studio-sdks).
6. [Package NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider](https://www.nuget.org/packages/Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider), version 2.2.0 ou ultérieure.
7. [Package NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders](https://www.nuget.org/packages?q=Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders).

Les packages NuGet sont destinés à être utilisés dans des projets Visual Studio pour développer des applications utilisant Always Encrypted avec enclaves sécurisées. Le premier package est requis uniquement si vous stockez vos clés principales de colonne dans Azure Key Vault. Pour plus d’informations, consultez [Développer des applications](#develop-applications-issuing-rich-queries-in-visual-studio).

### <a name="configure-a-secure-enclave"></a>Configurer une enclave sécurisée

Sur l’ordinateur client/développement :

1. Ouvrez SSMS et connectez-vous à votre instance SQL Server en tant qu’un administrateur Active Directory (AD).
2. Pour vérifier qu’Always Encrypted avec enclaves sécurisées est pris en charge dans votre instance, exécutez la requête suivante :

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type'
   ```

    La requête doit retourner une ligne qui se présente comme suit :  

    | NAME                           | valeur | value_in_use |
    | ------------------------------ | ----- | -------------|
    | column encryption enclave type | 0     | 0            |

3. Configurez le type d’enclave sécurisée pour les enclaves VBS.

   ```sql
   EXEC sys.sp_configure 'column encryption enclave type', 1
   RECONFIGURE
   ```

4. Redémarrez votre instance SQL Server pour que la modification précédente entre en vigueur. Vous pouvez redémarrer l’instance dans SSMS en cliquant dessus avec le bouton droit dans l’Explorateur d’objets et en sélectionnant Redémarrer. Une fois que l’instance a redémarré, connectez-vous à nouveau.

5. Vérifiez que l’enclave sécurisée est maintenant chargée en exécutant la requête suivante :

   ```sql
   SELECT [name], [value], [value_in_use] FROM sys.configurations
   WHERE [name] = 'column encryption enclave type'
   ```   

    La requête doit retourner une ligne qui se présente comme suit :  

    | NAME                           | valeur | value_in_use |
    | ------------------------------ | ----- | -------------- |
    | column encryption enclave type | 1     | 1              |

6. Pour activer les calculs complexes dans les colonnes chiffrées, exécutez la requête suivante :

   ```sql
   DBCC traceon(127,-1)
   ```

    > [!NOTE]
    > Les calculs complexes sont désactivés par défaut dans [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)]. Ils doivent être activés à l’aide de l’instruction ci-dessus après chaque redémarrage de votre instance SQL Server.

## <a name="provision-enclave-enabled-keys"></a>Approvisionner des clés prenant en charge les enclaves

L’introduction de clés prenant en charge les enclaves ne change pas fondamentalement les [flux de travail d’approvisionnement et de gestion des clés pour Always Encrypted](overview-of-key-management-for-always-encrypted.md). La seule modification concerne le flux de travail d’approvisionnement de clés principales de colonne, où vous pouvez désormais marquer la clé comme prenant en charge les enclaves (par défaut, les clés principales de colonne ne prennent pas en charge les enclaves). Lorsque vous spécifiez que la nouvelle clé principale de colonne doit prendre en charge les enclaves (avec SSMS ou PowerShell), les événements suivants se produisent :

- La propriété **ENCLAVE_COMPUTATIONS** dans les métadonnées de clé principale de colonne de la base de données est définie.
- Les valeurs de propriété de la clé principale de colonne (notamment le paramétrage de **ENCLAVE_COMPUTATIONS**) sont signées numériquement. L’outil ajoute la signature, qui est générée à l’aide de la clé principale de colonne actuelle, aux métadonnées. L’objectif de la signature est d’empêcher des administrateurs de bases de données et d’ordinateurs malveillants de falsifier le paramètre **ENCLAVE_COMPUTATIONS**. Les pilotes du client SQL vérifient les signatures avant d’autoriser l’utilisation de l’enclave. Cela permet aux administrateurs de sécurité de contrôler des données de la colonne pouvant être calculées à l’intérieur de l’enclave.

La propriété **ENCLAVE_COMPUTATIONS** d’une clé principale de colonne est immuable : vous ne pouvez pas la modifier après que la clé a été provisionnée. Vous pouvez, cependant, remplacer la clé principale de colonne par une nouvelle clé dont la valeur de la propriété **ENCLAVE_COMPUTATIONS** est différente de celle de la clé d’origine, via un processus appelé [remplacement de clé principale de colonne](#initiate-the-rotation-from-the-current-column-master-key-to-the-new-column-master-key). Pour plus d’informations sur la propriété **ENCLAVE_COMPUTATIONS**, consultez [CREATE COLUMN MASTER KEY](../../../t-sql/statements/create-column-master-key-transact-sql.md).

Pour approvisionner une clé de chiffrement de colonne prenant en charge les enclaves, vous devez vous assurer que la clé principale de colonne qui chiffre la clé de chiffrement de colonne prend en charge les enclaves.

Les limitations suivantes s’appliquent actuellement à l’approvisionnement des clés prenant en charge les enclaves :

- Les **clés principales de colonne prenant en charge les enclaves doivent être stockées dans le magasin de certificats Windows ou dans Azure Key Vault**. Le stockage de clés principales de colonne prenant en charge les enclaves dans d’autres types de magasins de clés (modules de sécurité matériels ou magasins de clés personnalisés) n’est actuellement pas pris en charge.

### <a name="provision-enclave-enabled-keys-using-sql-server-management-studio-ssms"></a>**Approvisionner des clés prenant en charge les enclaves à l’aide de SQL Server Management Studio (SSMS)**

Les étapes suivantes créent des clés prenant en charge les enclaves (requiert SSMS 18.0 ou version ultérieure) :

1. Vous connecter à votre base de données avec SSMS.
2. Dans l’**Explorateur d’objets**, développez votre base de données et accédez à **Sécurité** > **Clés Always Encrypted**.
3. Provisionnez une nouvelle clé principale de colonne prenant en charge les enclaves :

    1. Cliquez avec le bouton droit sur **Clés Always Encrypted** et sélectionnez **Nouvelle clé principale de colonne...**.
    2. Sélectionnez le nom de votre clé principale de colonne.
    3. Assurez-vous que vous sélectionnez **Magasin de certificats Windows (utilisateur actuel ou ordinateur local)** ou **Azure Key Vault**.
    4. Sélectionnez **Autoriser les calculs d’enclave**.
    5. Si vous avez sélectionné Azure Key Vault, connectez-vous à Azure et sélectionnez votre coffre de clés. Pour plus d’informations sur la création d’un coffre de clés pour Always Encrypted, consultez [Gérer vos coffres de clés à partir du portail Azure](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/).
    6. Sélectionnez votre clé si elle existe déjà ou créez-en une en suivant les instructions du formulaire.
    7. Cliquez sur **OK**.

        ![Autoriser les calculs d’enclave](./media/always-encrypted-enclaves/allow-enclave-computations.png)

4. Créer une nouvelle clé de chiffrement de colonne prenant en charge les enclaves :

    1. Cliquez avec le bouton droit sur **Clés Always Encrypted** et sélectionnez **Nouvelle clé de chiffrement de colonne**.
    2. Entrez un nom pour la nouvelle clé de chiffrement de colonne.
    3. Dans le menu déroulant **Clé principale de colonne**, sélectionnez la clé principale de colonne que vous avez créée aux étapes précédentes.
    4. Cliquez sur **OK**.

### <a name="provision-enclave-enabled-keys-using-powershell"></a>**Approvisionner des clés prenant en charge les enclaves avec PowerShell**

Les sections suivantes fournissent des exemples de scripts PowerShell pour l’approvisionnement des clés prenant en charge les enclaves. Les étapes qui sont spécifiques à Always Encrypted (nouvelles) avec des enclaves sécurisées sont mises en surbrillance. Pour plus d’informations (non spécifiques à Always Encrypted avec enclaves sécurisées) sur l’approvisionnement des clés à l’aide de PowerShell, consultez [Configurer des clés Always Encrypted à l’aide de PowerShell](https://docs.microsoft.com/sql/relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell).

**Provisionnement des clés prenant en charge l’enclave - Magasin de certificats Windows**

Sur l’ordinateur client/développement, ouvrez Windows PowerShell ISE et exécutez le script suivant.

Il est important de noter l’utilisation du paramètre `-AllowEnclaveComputations` dans l’applet de commande [**New-SqlCertificateStoreColumnMasterKeySettings**](https://docs.microsoft.com/powershell/module/sqlserver/new-sqlcertificatestorecolumnmasterkeysettings).

```powershell
# Create a column master key in Windows Certificate Store.
$cert = New-SelfSignedCertificate -Subject "\<Subject Name\>" -CertStoreLocation Cert:CurrentUser\\My -KeyExportPolicy Exportable -Type DocumentEncryptionCert -KeyUsage DataEncipherment -KeySpec KeyExchange

# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database. Provide the server/db name. Modify the connection string, if needed.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " + $databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Create a SqlColumnMasterKeySettings object for your column master key
# using the -AllowEnclaveComputations parameter.
$cmkSettings = New-SqlCertificateStoreColumnMasterKeySettings -CertificateStoreLocation "CurrentUser" -Thumbprint $cert.Thumbprint -AllowEnclaveComputations

# Create column master key metadata in the database.
$cmkName = "<column master key name in the database>"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database.
$cekName = "<column encryption key name in the database>"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName
```


### <a name="provisioning-enclave-enabled-keys---azure-key-vault"></a>Provisionnement des clés prenant en charge l’enclave - Azure Key Vault

Sur l’ordinateur client/développement, ouvrez Windows PowerShell ISE et exécutez le script suivant.

**Étape 1 : provisionner une clé principale de colonne dans Azure Key Vault**

Cela est également possible à l’aide du portail Azure. Pour plus d’informations, consultez [Gérer vos coffres de clés à partir du portail Azure](https://blogs.technet.microsoft.com/kv/2016/09/12/manage-your-key-vaults-from-new-azure-portal/).


```powershell
Import-Module Az
Connect-AzAccount

# User values
$SubscriptionId = "<Azure SubscriptionId>"
$resourceGroup = "<resource group name>"
$azureLocation = "<datacenter location>"
$akvName = "<key vault name>"
$akvKeyName = "<key name>"

# Set the context to the specified subscription.
$azureCtx = Set-AzContext -SubscriptionId $SubscriptionId

# Create a new resource group - skip, if your desired group already exists.
New-AzResourceGroup -Name $resourceGroup -Location $azureLocation

# Create a new key vault - skip if your vault already exists.
New-AzKeyVault -VaultName $akvName -ResourceGroupName $resourceGroup -Location $azureLocation

# Grant yourself permissions needed to create and use the column master key.
Set-AzKeyVaultAccessPolicy -VaultName $akvName -ResourceGroupName $resourceGroup -PermissionsToKeys get, create, list, update, wrapKey,unwrapKey, sign, verify -UserPrincipalName $azureCtx.Account

# Create a column master key in Azure Key Vault.
$akvKey = Add-AzureKeyVaultKey -VaultName $akvName -Name $akvKeyName -Destination "Software"
```

**Étape 2 : créer des métadonnées de clé principale de colonne dans la base de données, créer une clé de chiffrement de colonne et créer des métadonnées de clé de chiffrement de colonne dans la base de données**


```powershell
# Import the SqlServer module.
Import-Module "SqlServer" -Version

# Connect to your database. Provide the server and db name. If needed, modify the connection string.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " + $databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Authenticate to Azure before calling New-SqlAzureKeyVaultColumnMasterKeySettings,
# because -AllowEnclaveComputations causes a call to Azure Key Vault
# to generate the signature of the column master key.
Add-SqlAzureAuthenticationContext -Interactive

# Create a SqlColumnMasterKeySettings object for your column master key.
$cmkSettings = New-SqlAzureKeyVaultColumnMasterKeySettings -KeyURL $akvKey.ID -AllowEnclaveComputations

# Create column master key metadata in the database.
$cmkName = "<column master key name in the database>"
New-SqlColumnMasterKey -Name $cmkName -InputObject $database -ColumnMasterKeySettings $cmkSettings

# Generate a column encryption key, encrypt it with the column master key and create column encryption key metadata in the database.
$cekName = "<column encryption key name in the database>"
New-SqlColumnEncryptionKey -Name $cekName -InputObject $database -ColumnMasterKey $cmkName
```


## <a name="identify-enclave-enabled-keys-and-columns"></a>Identifier les colonnes et clés prenant en charge les enclaves

Pour répertorier les clés principales de colonne configurées dans votre base de données, vous pouvez interroger la vue de catalogue [sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md)(par exemple, dans SSMS). La nouvelle colonne **allow_enclave_computations** a été ajoutée à l’affichage. Il indique si une clé principale de colonne prend en charge les enclaves.

```sql
SELECT name, allow_enclave_computations
FROM sys.column_master_keys
```

Pour déterminer quelles clés de chiffrement de colonne sont chiffrées avec des clés de chiffrement de colonne prenant en charge des enclaves (et, par conséquent, prennent en charge les enclaves), vous devez joindre [sys.column_master_keys](../../system-catalog-views/sys-column-master-keys-transact-sql.md), [sys.column_encryption_key_values](../../system-catalog-views/sys-column-encryption-key-values-transact-sql.md) et [sys.column_encryption_keys](../../system-catalog-views/sys-column-encryption-keys-transact-sql.md).


```sql
SELECT cek.name AS [cek_name]
, cmk.name AS [cmk_name]
, cmk.allow_enclave_computations
FROM sys.column_master_keys cmk
JOIN sys.column_encryption_key_values cekv
   ON cmk.column_master_key_id = cekv.column_master_key_id
JOIN sys.column_encryption_keys cek
   ON cekv.column_encryption_key_id = cek.column_encryption_key_id
```

Pour déterminer les colonnes prenant en charge les enclaves (les colonnes qui sont chiffrées avec des clés de chiffrement de colonne prenant en charge les enclaves), utilisez la requête suivante :

```sql
SELECT c.name AS column_name
, cek.name AS cek_name
, cmk.name AS [cmk_name]
, cmk.allow_enclave_computations
from sys.columns c
JOIN sys.column_encryption_keys cek 
ON c.column_encryption_key_id = cek.column_encryption_key_id 
JOIN sys.column_encryption_key_values cekv 
ON cekv.column_encryption_key_id = cek.column_encryption_key_id 
JOIN sys.column_master_keys cmk 
ON cmk.column_master_key_id = cekv.column_master_key_id
```


## <a name="manage-collations"></a>Gérer les classements

Depuis sa version initiale, Always Encrypted a présenté une restriction concernant l’utilisation des classements : les classements non-BIN2 ne sont pas autorisés pour les colonnes de chaînes de caractères chiffrées à l’aide du chiffrement déterministe. Cette restriction s’applique également aux colonnes de chaînes prenant en charge les enclaves.

L’utilisation de classements non-BIN2 est autorisée pour les colonnes de chaînes de caractères chiffrées avec un chiffrement aléatoire et les clés de chiffrement de colonne prenant en charge les enclaves. Toutefois, la seule fonctionnalité nouvelle activée pour ces colonnes est le chiffrement sur place. Pour activer les calculs complexes (critères spéciaux, opérations de comparaison), vous devez vérifier que la colonne utilise un classement BIN2.

Le tableau ci-dessous récapitule les fonctionnalités pour les colonnes de chaînes prenant en charge les enclaves en fonction du type de chiffrement et de l’ordre de tri du classement.

| **Ordre de tri du classement** | **Chiffrement déterministe** | **Chiffrement aléatoire**                 |
| ------------------------ | ---------------------------- | ----------------------------------------- |
| **Non-BIN2**             | Non pris en charge                | Chiffrement sur place                       |
| **BIN2**                 | Comparaison d’égalité          | Chiffrement sur place et calculs complexes |

### <a name="determining-and-changing-collations"></a>Détermination et modification des classements

Dans SQL Server, les classements peuvent être définis au niveau du serveur, de la base de données ou de la colonne. Pour obtenir des instructions générales sur la façon de déterminer le classement actuel et de modifier un classement au niveau du serveur, de la base de données ou de la colonne, consultez [Prise en charge d'Unicode et du classement](https://docs.microsoft.com/sql/relational-databases/collations/collation-and-unicode-support).

**Considérations spéciales pour les colonnes de chaînes non UNICODE** :

La restriction supplémentaire suivante, imposée par une limitation des pilotes du client SQL (sans rapport avec Always Encrypted), s’applique aux colonnes de chaînes autres qu’UNICODE (ASCII). Si vous remplacez le classement de base de données par une colonne de chaîne non-UNICODE (char, varchar), vous devez vérifier que le classement de la colonne utilise la même page de codes que le classement de base de données.
Pour répertorier tous les classements ainsi que leurs identificateurs de page de codes, utilisez la requête suivante :

```sql
SELECT [Name]
   , [Description]
   , [CodePage] = COLLATIONPROPERTY([Name], 'CodePage')
FROM ::fn_helpcollations()
```

Par exemple, Chinese_Traditional_Stroke_Order_100_CI_AI_WS et Chinese_Traditional_Stroke_Order_100_BIN2 ont la même page de codes (950), mais Chinese_Traditional_Stroke_Order_100_CI_AI_WS et Latin1_General_100_BIN2 ont différentes pages de codes (950 et 1252, respectivement). La restriction ci-dessus ne s’applique pas aux colonnes de chaînes UNICODE (nchar, nvarchar). Par conséquent, une solution de contournement peut consister à envisager la définition d’un type de données UNICODE pour vos nouvelles colonnes chiffrées, en créant ou en transformant le type en type UNICODE avant de chiffrer une colonne existante.


## <a name="create-a-new-table-with-enclave-enabled-columns"></a>Créer une table avec des colonnes prenant en charge les enclaves

Vous pouvez créer une table avec des colonnes chiffrées à l’aide de l’instruction [CREATE TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/create-table-transact-sql). Always Encrypted avec enclaves sécurisées ne modifie pas la syntaxe de cette instruction.

1. À l’aide de SSMS, connectez-vous à votre base de données et ouvrez une fenêtre de requête.
   
     > [!NOTE]
     > Always Encrypted ne devra pas être activé dans la chaîne de connexion pour cette tâche.

2. Dans la fenêtre de requête, émettez une instruction CREATE TABLE pour créer votre table, en spécifiant la clause ENCRYPTED WITH dans la [définition de colonne](https://docs.microsoft.com/sql/t-sql/statements/alter-table-column-definition-transact-sql) pour chaque colonne à chiffrer. Pour qu’une colonne prenne en charge les enclaves, veillez à spécifier une clé de chiffrement de colonne prenant en charge les enclaves. Vous devrez également peut-être spécifier un classement BIN2 pour les colonnes de chaînes si le classement par défaut pour votre base de données n’est pas un classement BIN2. Consultez la section de configuration de classement pour plus d’informations.

### <a name="example"></a> Exemple

L’instruction ci-dessous instruction crée une table avec deux colonnes chiffrées, SSN et Salary. En supposant que CEK1 soit une clé de chiffrement de colonne prenant en charge les enclaves, le moteur SQL Server prend en charge le chiffrement sur place et les calculs complexes pour les deux colonnes, puisque celles-ci utilisent le chiffrement aléatoire. L’instruction définit le classement Latin1\_Général\_ BIN2 pour la colonne UNICODE SSN, ce qui est nécessaire en supposant que le classement de base de données par défaut soit un classement Latin1 non-BIN2.

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [int] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY]
GO
```


## <a name="add-a-new-enclave-enabled-column-to-an-existing-table"></a>Ajouter une nouvelle colonne prenant en charge les enclaves à une table existante

Vous pouvez ajouter une nouvelle colonne chiffrée à une table existante avec l’instruction [ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) / ADD. Always Encrypted avec enclaves sécurisées ne modifie pas la syntaxe de cette instruction.

1. À l’aide de SSMS, connectez-vous à votre base de données et ouvrez une fenêtre de requête.
    
   Always Encrypted ne devra pas être activé dans la chaîne de connexion pour cette tâche.

2. Dans la fenêtre de requête, émettez l’instruction ALTER TABLE avec la clause ADD en spécifiant la clause ENCRYPTED WITH dans la [définition de colonne](https://docs.microsoft.com/sql/t-sql/statements/alter-table-column-definition-transact-sql) et en utilisant une clé de chiffrement de colonne prenant en charge les enclaves. Vous devrez également peut-être spécifier un classement BIN2 si votre nouvelle colonne est une colonne de chaînes et si le classement par défaut pour votre base de données n’est pas un classement BIN2. Consultez la section de configuration de classement pour plus d’informations.

### <a name="example"></a> Exemple

En supposant que CEK1 soit une clé de chiffrement de colonne prenant en charge les enclaves, l’instruction ci-dessous ajoute une nouvelle colonne chiffrée, nommée BirthDate, qui prend en charge des requêtes complexes et le chiffrement sur place (puisque la colonne utilise le chiffrement aléatoire).

```sql
ALTER TABLE [dbo].[Employees]
ADD [BirthDate] [Date] ENCRYPTED WITH (
COLUMN_ENCRYPTION_KEY = [CEK1],
ENCRYPTION_TYPE = Randomized,
ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NULL
```


## <a name="prepare-an-ssms-query-window-with-always-encrypted-enabled"></a>Préparer une fenêtre de requête SSMS prenant en charge Always Encrypted

Pour ajouter les paramètres de connexion requis afin de prendre en charge les calculs d’enclaves :

1. Ouvrez SSMS.
2. Après avoir spécifié le nom de votre serveur et un nom de base de données dans la boîte de dialogue Se connecter au serveur, cliquez sur **Options**. Accédez à l’onglet **Always Encrypted**, sélectionnez **Activer Always Encrypted** et spécifiez l’URL de l’attestation d’enclave.
    
    ![Paramètre de chiffrement de colonne](./media/always-encrypted-enclaves/column-encryption-setting.png)

3. Cliquez sur Se connecter.
4. Ouvrez une fenêtre de nouvelle requête.

Si vous avez déjà ouvert une fenêtre de requête, voici comment vous pouvez mettre à jour sa connexion de base de données pour activer Always Encrypted :

1. Avec le bouton droit, cliquez n’importe où dans une fenêtre de requête existante.
2. Sélectionnez Connexion \> Modifier la connexion.
3. Cliquez sur **Options**. Accédez à l’onglet **Always Encrypted**, sélectionnez **Activer Always Encrypted** et spécifiez l’URL de l’attestation d’enclave.
4. Cliquez sur Se connecter.


## <a name="work-with-encrypted-columns"></a>Utiliser des colonnes chiffrées

### <a name="encrypt-an-existing-plaintext-column-in-place"></a>Chiffrer une colonne au texte en clair existante sur place

Vous pouvez chiffrer une colonne au texte en clair existante sur place avec l’instruction [ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) / ALTER COLUMN, à condition d’utiliser une clé de chiffrement de colonne prenant en charge les enclaves.

Pour chiffrer une colonne à l’aide d’une clé ne prenant pas en charge les enclaves, vous devez utiliser des outils côté client, tels que l’Assistant Always Encrypted dans SSMS, ou l’applet de commande Set-SqlColumnEncryption dans le module SqlServer PowerShell. Pour plus d’informations, consultez :

- [Assistant Always Encrypted](always-encrypted-wizard.md)
- [Configurer le chiffrement de colonne à l’aide de PowerShell](configure-column-encryption-using-powershell.md)


### <a name="prerequisites"></a>Conditions préalables requises

- Votre colonne existante n’est pas chiffrée.
- Vous avez approvisionné des clés prenant en charge les enclaves.
- Vous avez accès à la clé principale de colonne.

#### <a name="steps"></a>Étapes

1. Préparez une fenêtre de requête SSMS avec Always Encrypted et des calculs d’enclave activés dans la connexion de base de données. Pour plus d’informations, consultez [Préparer une fenêtre de requête SSMS prenant en charge Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).
2. Dans la fenêtre de requête, émettez l’instruction ALTER TABLE avec la clause ALTER COLUMN en spécifiant une clé de chiffrement de colonne prenant en charge les enclaves dans la clause ENCRYPTED WITH. Si votre colonne est une colonne de chaînes (par exemple, char, varchar, nchar, nvarchar), vous devrez peut-être modifier le classement et utiliser un classement BIN2. Consultez la section de configuration de classement pour plus d’informations.
    
    > [!NOTE]
    > Si votre clé principale de colonne est stockée dans Azure Key Vault, vous serez peut-être invité à vous connecter à Azure.

3. L’effacement du cache de plan avec [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md) afin de garantir les plans pour toute requête sur les colonnes chiffrées par vos soins est recréé à la première exécution de la requête (facultatif).
  
    > [!NOTE]
    > Si vous ne supprimez pas le plan de la requête affectée à partir du cache, la première exécution de la requête après le chiffrement peut échouer.

    > [!NOTE]
    > Utilisez DBCC FREEPROCCACHE pour effacer soigneusement le cache du plan, car cela peut entraîner une dégradation temporaire des performances de requête. Pour limiter l’impact négatif de l’effacement du cache, vous pouvez supprimer uniquement les plans sélectionnés des requêtes concernées.

4.  Appelez [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) afin de mettre à jour les métadonnées pour les paramètres de chaque module (procédure stockée, fonction, affichage, déclencheur) qui peuvent avoir été invalidés lors du chiffrement des colonnes (facultatif).

#### <a name="example"></a> Exemple

L’exemple ci-dessous suppose que :

  - CEK1 est une clé de chiffrement de colonne prenant en charge les enclaves.

  - Le texte de la colonne SSN est en clair et utilise actuellement un classement Latin1 non-BIN2 (par exemple, Latin1\_général\_CI\_AI\_KS\_WS).

L’instruction chiffre la colonne SSN à l’aide d’un chiffrement aléatoire et d’une clé de chiffrement de colonne prenant en charge les enclaves. Elle remplace également le classement de base de données par défaut avec le classement BIN2 correspondant (dans la même page de codes).

L’opération est effectuée en ligne (ONLINE = ON). Notez également l’appel à **DBCC FREEPROCCACHE**, qui recrée les plans des requêtes affectées par la modification de schéma de table.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char] COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
WITH
(ONLINE = ON)
GO
DBCC FREEPROCCACHE
GO
```


### <a name="make-an-existing-encrypted-column-enclave-enabled"></a>Faire prendre en charge les enclaves par une colonne chiffrée existante

Il existe plusieurs façons d’activer la fonctionnalité d’enclave pour une colonne existante ne prenant pas en charge les enclaves. La méthode choisie dépend de plusieurs facteurs :

- **Étendue/granularité :** voulez-vous activer la fonctionnalité d’enclave pour une partie des colonnes ou pour toutes les colonnes protégées par une clé principale de colonne donnée ?
- **Taille des données :** quelle est la taille des tables contenant les colonnes dont vous souhaitez qu’elles prennent en charge des enclaves ?
- Voulez-vous également modifier le type de chiffrement pour vos colonnes ? N’oubliez pas que seul le chiffrement aléatoire prend en charge les calculs complexes (critères spéciaux, les opérateurs de comparaison). Si votre colonne est chiffrée à l’aide du chiffrement déterministe, vous devrez également la chiffrer à nouveau avec le chiffrement aléatoire pour déverrouiller toutes les fonctionnalités de l’enclave.

Voici les trois approches de prise en charge d’enclaves pour des colonnes existantes :

#### <a name="option-1-rotate-the-column-master-key-to-replace-it-with-an-enclave-enabled-column-master-key"></a>Option n°1 : remplacer la clé principale de colonne par une clé principale de colonne prenant en charge les enclaves.
  
- Avantages :
  - N’implique pas de nouveau chiffrement des données et est donc généralement l’approche la plus rapide. Cette approche est recommandée pour les colonnes contenant de grandes quantités de données, à condition que toutes les colonnes dont vous avez besoin pour permettre des calculs complexes utilisent déjà le chiffrement déterministe et, par conséquent, ne doivent pas faire l’objet d’un nouveau chiffrement.
  - Permet d’activer la fonctionnalité d’enclave pour plusieurs colonnes à l’échelle, puisqu’elle permet à toutes les clés de chiffrement de colonne et à toutes les colonnes chiffrées, associées à la clé principale de colonne d’origine, de prendre en charge les enclaves.
  
- Inconvénients :
  - Ne prend pas en charge le passage du type de chiffrement déterministe au type aléatoire et ne permet donc pas les calculs complexes lors du déverrouillage du chiffrement sur place pour les colonnes chiffrées de façon déterministe.
  - Ne vous permet pas de convertir certaines colonnes de manière sélective en liaison avec une clé principale de colonne donnée.
  - Surcroît de travail lié à la gestion des clés : vous devez créer une clé principale de colonne et la mettre à la disposition des applications qui interrogent les colonnes affectées.  


#### <a name="option-2-this-approach-involves-two-steps-1-rotating-the-column-master-key-as-in-option-1-and-2-re-encrypting-a-subset-of-deterministically-encrypted-columns-using-randomized-encryption-to-enable-rich-computations-for-those-columns"></a>Option 2 : Cette approche implique deux étapes : 1) remplacement de la clé principale de colonne (comme dans l’option 1) et 2) nouveau chiffrement d’un sous-ensemble de colonnes chiffrées de façon déterministe avec le chiffrement aléatoire afin d’y permettre des calculs complexes.
  
- Avantages :
  - Chiffre à nouveau les données sur place, ce qui en fait une méthode recommandée pour permettre les requêtes complexes pour des colonnes chiffrées de façon déterministe qui contiennent de grandes quantités de données. Notez que l’étape 1 déverrouille le chiffrement sur place pour les colonnes à l’aide du chiffrement déterministe, afin que l’étape 2 puisse être effectuée sur place.
  - Peut activer la fonctionnalité d’enclave pour plusieurs colonnes à l’échelle.
  
- Inconvénients :
  - Ne vous permet pas de convertir certaines colonnes de manière sélective en liaison avec une clé principale de colonne donnée.
  - Surcroît de travail lié à la gestion des clés : vous devez créer une clé principale de colonne et la mettre à la disposition des applications qui interrogent les colonnes affectées.

#### <a name="option-3-re-encrypting-selected-columns-with-a-new-enclave-enabled-column-encryption-key-and-randomized-encryption-if-needed-on-the-client-side"></a>Option 3 : nouveau chiffrement des colonnes sélectionnées avec une nouvelle clé de chiffrement de colonne prenant en charge les enclaves et le chiffrement aléatoire (le cas échéant) côté client.
  
- Avantages de cette méthode :
  - Vous permet d’activer de manière sélective la fonctionnalité d’enclave pour une colonne ou pour un petit sous-ensemble de colonnes.
  - Elle permet d’activer des calculs complexes pour une colonne chiffrée de façon déterministe en une seule étape.
  - Il ne nécessite pas la création d’une nouvelle clé principale de colonne et a donc un impact moindre sur les applications.
  
- Inconvénients :
  - Tout le contenu de la table qui contient la colonne doit être déplacé en dehors de la base de données pour le nouveau chiffrement. Cette option est donc recommandée uniquement pour les petites tables. 

Pour plus d'informations, consultez les sections suivantes :
  - [Faire prendre en charge les enclaves par des colonnes en remplaçant leur clé principale de colonne](#make-columns-enclave-enabled-by-rotating-their-column-master-key)
  - [Nouveau chiffrement des colonnes sur place](#re-encrypt-columns-in-place)
  - [Nouveau chiffrement des colonnes côté client](#re-encrypt-columns-on-the-client-side)

### <a name="make-columns-enclave-enabled-by-rotating-their-column-master-key"></a>Faire prendre en charge les enclaves par des colonnes en remplaçant leur clé principale de colonne

Le remplacement d’une clé principale de colonne est le processus de remplacement d’une clé principale de colonne existante par une nouvelle clé principale de colonne. Il implique le nouveau chiffrement des clés de chiffrement de colonne associées à l’ancienne clé principale de colonne avec la nouvelle clé principale de colonne. Ce flux de travail existe depuis la version initiale d’Always Encrypted pour prendre en charge le remplacement d’une clé principale de colonne pour des raisons de sécurité ou de conformité (au cas où la clé principale de colonne existante est compromise).

À l’aide d’enclaves, Always Encrypted ajoute un nouvel objectif au workflow de remplacement de clé principale de colonne. En supposant que l’ancienne clé principale de colonne ne prenne pas en charge les enclaves, contrairement à la nouvelle clé principale de colonne, le processus de remplacement permet efficacement à toutes les clés de chiffrement de colonne associées à la clé principale de colonne de prendre en charge les enclaves. Le remplacement d’une clé principale de colonne n’implique pas de nouveau chiffrement des données et est, par conséquent, un processus recommandé pour la prise en charge des fonctionnalités d’enclave pour les colonnes existantes.

Le remplacement de la clé principale de colonne ne modifie pas le type de chiffrement des colonnes concernées. Par conséquent, il peut uniquement déverrouiller le chiffrement sur place pour les colonnes chiffrées de façon déterministe. Pour déverrouiller des calculs complexes dans des colonnes à l’aide du chiffrement déterministe, vous devez les chiffrer à nouveau (sur place) après avoir remplacé la clé principale de colonne.

Vous devrez peut-être également transformer le classement pour les colonnes de chaînes en classement BIN2 à l’aide d’un chiffrement aléatoire pour déverrouiller les calculs complexes. Consultez la section de configuration de classement pour plus d’informations.

Le processus de modification de la clé principale de colonne est le même si l’une des clés impliquées prend en charge les enclaves. Vous trouverez plus d’informations sur la manière de remplacer la clé principale de colonne dans les articles suivants :

- [Remplacer une clé principale de colonne avec SSMS](configure-always-encrypted-using-sql-server-management-studio.md)
- [Remplacement d’une clé principale de colonne avec PowerShell](rotate-always-encrypted-keys-using-powershell.md)

Pour votre commodité, un exemple de script PowerShell pour le remplacement d’une clé principale de colonne est fourni ci-dessous.

#### <a name="pre-requisites"></a>Conditions préalables

- Vous avez approvisionné une clé principale de colonne prenant en charge les enclaves.
- Vous avez accès à l’ancienne et à la nouvelle clé principale de colonne.
- Toutes les colonnes de chaîne protégées avec l’ancienne clé principale de colonne utilisent les classements BIN2. (Remarque : Vous pouvez également modifier le classement des colonnes de chaînes après le remplacement de la clé principale de colonne).

#### <a name="steps"></a>Étapes

Collez le script suivant dans Windows PowerShell ISE, remplacez les \<espaces réservés\> par vos propres valeurs :


```powershell
# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database. Modify server/db name or/and the connection string, if needed.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Data Source = " + $serverName + "; Initial Catalog = " +
$databaseName + "; Integrated Security = true"
$database = Get-SqlDatabase -ConnectionString $connStr

# Set the names of the old/current column master key and the new/target enclave-enabled column master key. (Change the names, if needed).
$oldCmkName = "<old column master key name>"
$newCmkName = "<new column master key name>"

# Authenticate to Azure. Needed only of either column master key is stored in Azure Key Vault.
Add-SqlAzureAuthenticationContext -Interactive

# Initiate the rotation from the current column master key to the new column master key.
Invoke-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName $oldCmkName
-TargetColumnMasterKeyName $newCmkName -InputObject $database

# Complete the rotation of the old column master key.
Complete-SqlColumnMasterKeyRotation -SourceColumnMasterKeyName
$oldCmkName -InputObject $database

# Remove the old column master key metadata.
Remove-SqlColumnMasterKey -Name $oldCmkName -InputObject $database
```


### <a name="re-encrypt-columns-in-place"></a>Chiffrer à nouveau les colonnes sur place 

Une fois que votre colonne prend en charge les enclaves, vous pouvez effectuer les opérations suivantes sur place (à l’intérieur de l’enclave, sans avoir à déplacer les données en dehors de la base de données) :

- Remplacement de la clé de chiffrement de colonne (par une nouvelle clé), par exemple, pour respecter les réglementations de conformité, dont certaines exigent le remplacement périodique des clés, ou pour des raisons de sécurité (en cas de compromission de la clé de chiffrement de votre colonne).
- Modification du type de chiffrement, par exemple, à partir d’un chiffrement déterministe pour le chiffrement aléatoire, pour déverrouiller des calculs riches pour la colonne.

#### <a name="prerequisites"></a>Conditions préalables requises

- Votre colonne est chiffrée à l’aide d’une clé de chiffrement de colonne prenant en charge les enclaves.
- Vous avez approvisionné une nouvelle clé de chiffrement de colonne prenant en charge les enclaves (si votre objectif est de remplacer la clé de chiffrement de colonne prenant en charge les enclaves et de protéger la colonne).
- Vous avez accès à la clé principale de colonne.

#### <a name="steps"></a>Étapes

1. Préparez une fenêtre de requête SSMS avec Always Encrypted et des calculs d’enclave activés pour la connexion de base de données. Pour plus d’informations, consultez [Préparer une fenêtre de requête SSMS prenant en charge Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2. Dans la fenêtre de requête, émettez l’instruction d’utilisation d’[ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) avec la clause ALTER COLUMN en spécifiant la clause ENCRYPTED WITH suivante :
    
    1. Le nom de la nouvelle clé de chiffrement de colonne prenant en charge les enclaves si vous modifiez la clé actuelle. Si vous ne modifiez pas la clé de chiffrement de colonne, vous devez spécifier le nom de la clé actuelle.
    
    2. Le nouveau type de chiffrement si vous le modifiez. Si vous ne modifiez pas le type de chiffrement, vous devez spécifier le type de chiffrement actuel.
        
       Si la colonne que vous chiffrez à nouveau utilise un classement (BIN2) différent du classement de base de données par défaut, vous devez inclure la phrase COLLATE et spécifier le classement actuel de la colonne dans la définition de colonne (pour conserver le classement).
        
       > [!NOTE]
       > Si votre clé principale de colonne est stockée dans Azure Key Vault, vous serez peut-être invité à vous connecter à Azure.

3. L’effacement du cache de plan avec [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md) afin de garantir les plans pour toute requête sur les colonnes chiffrées à nouveau par vos soins est recréé à la première exécution de la requête (facultatif).
    
    Si vous ne supprimez pas le plan de la requête affectée à partir du cache, la première exécution de la requête après le nouveau chiffrement peut échouer.
    
    > [!NOTE]
    > Utilisez DBCC FREEPROCCACHE pour effacer soigneusement le cache du plan, car cela peut entraîner une dégradation temporaire des performances de requête. Pour limiter l’impact négatif de l’effacement du cache, vous pouvez supprimer uniquement les plans sélectionnés des requêtes concernées. Consultez [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md).aspx) pour plus d’informations.

4. Appelez [sp_refresh_parameter_encryption](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-refresh-parameter-encryption-transact-sql) afin de mettre à jour les métadonnées pour les paramètres de chaque module (procédure stockée, fonction, affichage, déclencheur) qui peuvent avoir été invalidés lors du nouveau chiffrement des colonnes (facultatif).

#### <a name="examples"></a>Exemples

En supposant que la colonne SSN soit actuellement chiffrée de façon déterministe à l’aide d’une clé de chiffrement de colonne, nommée CEK1, prenant en charge les enclaves et que le classement actuel, défini au niveau de la colonne, soit Latin1\_général\_BIN2, l’instruction ci-dessous chiffre à nouveau la colonne de façon aléatoire avec la même clé.


```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
GO
DBCC FREEPROCCACHE
GO
```


En supposant que la colonne SSN soit actuellement chiffrée de façon déterministe à l’aide d’une clé de chiffrement de colonne (nommée CEK1) prenant en charge les enclaves et que le classement de base de données par défaut soit un classement BIN2 (qui n’a pas été défini au niveau de la colonne), l’instruction ci-dessous d’instruction chiffre à nouveau la colonne avec une nouvelle clé (nommée CEK2) prenant en charge les enclaves (sans modifier le type de chiffrement).

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK2]
, ENCRYPTION\_TYPE = Deterministic
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
GO
DBCC FREEPROCCACHE
GO
```

En supposant que la colonne SSN soit actuellement chiffrée de façon déterministe à l’aide d’une clé de chiffrement de colonne (nommée CEK1) prenant en charge les enclaves et que le classement de base de données par défaut soit un classement BIN2 (qui n’a pas été défini au niveau de la colonne), l’instruction ci-dessous chiffre à nouveau la colonne avec une nouvelle clé prenant en charge les enclaves et un chiffrement aléatoire. Par ailleurs, l’opération est effectuée en mode en ligne.


```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) 
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL 
WITH (ONLINE = ON)
GO
DBCC FREEPROCCACHE
GO
```


### <a name="re-encrypt-columns-on-the-client-side"></a>Chiffrer à nouveau les colonnes côté client 

La méthode héritée pour le nouveau chiffrement (ainsi que pour le chiffrement ou le déchiffrement) de colonnes utilise des outils côté client, tels que l’Assistant Always Encrypted ou PowerShell. En règle générale, l’utilisation de cette méthode est déconseillée, sauf si la table contenant les colonnes (à nouveau chiffrées) est de petite taille et si votre objectif est de combiner le nouveau chiffrement d’une colonne et une nouvelle clé prenant en charge les enclaves et la modification du type de chiffrement (de déterministe à aléatoire).

Notez que si vous chiffrez à nouveau une colonne à chiffrement aléatoire, vous devrez peut-être transformer son classement en classement BIN2 (avant ou après le nouveau chiffrement) pour déverrouiller les calculs complexes. Consultez la section de configuration de classement pour plus d’informations.

Pour plus d’informations, consultez :

  - Modification de clés de chiffrement de colonnes avec SSMS : <https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-wizard>
  - Modification de clés de chiffrement de colonnes avec PowerShell : <https://docs.microsoft.com/sql/relational-databases/security/encryption/configure-column-encryption-using-powershell>

### <a name="decrypt-a-column-in-place"></a>Déchiffrer une colonne sur place

Si votre colonne est chiffrée avec une clé de chiffrement de colonne prenant en charge les enclaves, vous pouvez la déchiffrer (convertir en une colonne de texte en clair) sur place à l’aide de l’instruction ALTER TABLE. Par ailleurs, l’opération est effectuée en mode en ligne.

#### <a name="prerequisites"></a>Conditions préalables requises

- Votre colonne est chiffrée à l’aide d’une clé de chiffrement de colonne prenant en charge les enclaves.
- Vous avez accès à la clé principale de colonne.



#### <a name="steps"></a>Étapes

1.  Préparez une fenêtre de requête SSMS avec Always Encrypted et des calculs d’enclave activés pour la connexion de base de données. Pour plus d’informations, consultez [Préparer une fenêtre de requête SSMS prenant en charge Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2.  Dans la fenêtre de requête, émettez l’instruction d’utilisation d’[ALTER TABLE (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-table-transact-sql) avec la clause ALTER COLUMN en spécifiant la configuration de colonne souhaitée **sans** la clause ENCRYPTED WITH.
    
    > [!NOTE]
    > Si votre clé principale de colonne est stockée dans Azure Key Vault, vous serez peut-être invité à vous connecter à Azure.

3.  L’effacement du cache de plan avec [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md) afin de garantir les plans pour toute requête sur les colonnes déchiffrées par vos soins est recréé à la première exécution de la requête (facultatif).
    
    > [!NOTE]
    > Si vous ne supprimez pas le plan de la requête affectée à partir du cache, la première exécution de la requête après le déchiffrement peut échouer.
    
    > [!NOTE]
    > Utilisez DBCC FREEPROCCACHE pour effacer soigneusement le cache du plan, car cela peut entraîner une dégradation temporaire des performances de requête. Pour limiter l’impact négatif de l’effacement du cache, vous pouvez supprimer uniquement les plans sélectionnés des requêtes concernées. Consultez [DBCC FREEPROCCACHE](../../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md) pour plus d’informations.

4.  Appelez [sp\_refresh\_parameter\_encryption](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-refresh-parameter-encryption-transact-sql) afin de mettre à jour les métadonnées pour les paramètres de chaque module (procédure stockée, fonction, affichage, déclencheur) qui peuvent avoir été invalidés lors du déchiffrement des colonnes (facultatif).

#### <a name="example"></a> Exemple

En supposant que la colonne SSN soit chiffrée et que le classement actuel défini au niveau de la colonne soit Latin1\_général\_BIN2, l’instruction ci-dessous déchiffre la colonne (sans modifier le classement ; vous pouvez également choisir de transformer le classement, par exemple en classement non-BIN2, dans la même instruction).


```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
WITH (ONLINE = ON)
GO
DBCC FREEPROCCACHE
GO
```


## <a name="issue-rich-queries-against-encrypted-columns-using-ssms"></a>Émettre des requêtes complexes sur des colonnes chiffrées à l’aide de SSMS

Le moyen le plus rapide d’essayer des requêtes complexes sur vos colonnes prenant en charge les enclaves est de partir d’une fenêtre de requête SSMS avec paramétrage d’Always Encrypted activé. Pour plus d’informations sur cette fonctionnalité utile dans SSMS, consultez :

- [Paramétrage d’Always Encrypted : utilisation de SSMS pour Insérer dans, Mettre à jour et Filtrer par colonne chiffrée](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/)
- [Interrogation de colonnes chiffrées](configure-always-encrypted-using-sql-server-management-studio.md#querying-encrypted-columns)



### <a name="prerequisites"></a>Conditions préalables requises

- Les colonnes à interroger prennent en charge les enclaves.
- Vous avez accès à la clé (ou aux clés) principale(s) de colonne.

### <a name="steps"></a>Étapes

1.  Préparez une fenêtre de requête SSMS avec Always Encrypted et des calculs d’enclave activés pour la connexion de base de données. Pour plus d’informations, consultez [Préparer une fenêtre de requête SSMS prenant en charge Always Encrypted](#prepare-an-ssms-query-window-with-always-encrypted-enabled).

2.  Activer le paramétrage d’Always Encrypted
    
    1.  Sélectionnez **Requête** dans le menu principal de SSMS.
    2.  Sélectionnez **Options de requête…**.
    3.  Accédez à **Exécution** > **Avancé**.
    4.  Sélectionnez ou désélectionnez Activer le paramétrage d’Always Encrypted.
    5.  Cliquez sur OK.

3.  Créez et exécutez vos requêtes à l’aide de calculs complexes sur des colonnes chiffrées. Vous devez déclarer une variable Transact-SQL pour chaque valeur ciblant une colonne chiffrée dans votre requête. Les variables doivent utiliser des initialisations incluses (ne peut pas être définie via l’instruction SET).
    
    > [!NOTE]
    > Si votre clé principale de colonne est stockée dans Azure Key Vault, vous serez peut-être invité à vous connecter à Azure.

### <a name="example"></a> Exemple

Cet exemple suppose que votre base de données contient une table créée à l’aide de l’instruction suivante.

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [int] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY]
GO
```


CEK1 est une clé de chiffrement de colonne prenant en charge les enclaves.

Voici un exemple de requête qui respecte les règles du paramétrage, par rapport à cette table :


```sql
DECLARE @SSNPattern CHAR(11) = '%1111%'
DECLARE @MinSalary INT = 1000
SELECT *
FROM [dbo].[Employees]
WHERE SSN LIKE @SSNPattern
    AND [Salary] >= @MinSalary;
GO;
```


## <a name="develop-applications-issuing-rich-queries-in-visual-studio"></a>Développer des Applications qui lancent des requêtes complexes dans Visual Studio

### <a name="set-up-your-you-visual-studio-project"></a>Configurez votre projet Visual Studio

Pour utiliser Always Encrypted avec enclaves sécurisées dans une application .NET Framework, vous devez vous assurer que votre application repose sur .NET Framework 4.7.2 et est intégrée avec le package NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders. En outre, si vous stockez votre clé principale de colonne dans Azure Key Vault, vous devez également intégrer votre application avec le package NuGet Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider, version 2.2.0 ou ultérieure. 

1. Ouvrez Visual Studio.
2. Créez un projet VisualC\#, ou ouvrez un projet existant.
3. Assurez-vous que votre projet cible au moins .NET Framework 4.7.2. Cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions, sélectionnez Propriétés et définissez l’infrastructure cible sur .NET Framework 4.7.2.

4. Installez le package NuGet suivant en accédant à **Outils** (menu principal) > **Gestionnaire de Package NuGet** > **Console du gestionnaire de package**. Exécutez le code suivant dans la Console du gestionnaire de Package.

  ```powershell
  Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider --IncludePrerelease 
  ```

5. Si vous utilisez Azure Key Vault pour stocker vos clés principales de colonne, installez les packages NuGet suivants en accédant à **Outils** (menu principal) > **Gestionnaire de package NuGet** > **Console de gestionnaire de package**. Exécutez le code suivant dans la Console du gestionnaire de Package.

  ```powershell
  Install-Package Microsoft.SqlServer.Management.AlwaysEncrypted.AzureKeyVaultProvider --IncludePrerelease -Version 2.2.0
  Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
  ```

6. Sélectionnez votre projet et cliquez sur Installer.
7. Ouvrez le fichier de configuration à partir de votre projet (par exemple, App.config ou Web.config).
8. Localisez la section de \<configuration\>. Dans la section de \<configuration\>, recherchez la section \<configSections\>. Ajoutez la section suivante dans le \<configSections\> :

  ```
  <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" /\>
  ```

9. À l’intérieur de la section de configuration, sous \<configSections\>, ajoutez la section suivante, qui spécifie un fournisseur d’enclave à utiliser pour attester et interagir avec les enclaves Intel SGX :

  ```
  \<SqlColumnEncryptionEnclaveProviders\>
      \<providers\>
      \<add name="VBS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders.VirtualizationBasedSecurityEnclaveProvider, Microsoft.SqlServer.Management.AlwaysEncrypted.EnclaveProviders,   Version=15.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91"/\>
      \</SqlColumnEncryptionEnclaveProviders\>
  ```
 

### <a name="develop-and-test-your-app"></a>Développer et tester votre application 

Pour utiliser Always Encrypted et les calculs d’enclave, votre application doit se connecter à la base de données avec les mots deux clés suivants dans la chaîne de connexion : `Column Encryption Setting = Enabled; Enclave Attestation Url=https://x.x.x.x/Attestation` (où xxxx peut être une adresse ip, un domaine, etc.).

De plus, votre application doit se conformer aux instructions courantes qui s’appliquent aux applications utilisant Always Encrypted. Par exemple, votre application doit avoir accès aux clés principales de colonnes associées aux colonnes de base de données référencées dans les requêtes de l’application.

Pour plus d’informations sur le développement d’applications .NET Framework à l’aide d’Always Encrypted, consultez les articles suivants :

- [Développer à l’aide d’Always Encrypted avec le fournisseur de données .NET Framework](develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Always Encrypted : protéger les données sensibles de la base de données SQL et stocker vos clés de chiffrement dans Azure Key Vault](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

#### <a name="example"></a> Exemple

Le code ci-dessous est un exemple simple d’une application de c\#onsole émettant une requête LIKE sur la table avec le schéma suivant :

```sql
CREATE TABLE [dbo].[Employees]
(
    [EmployeeID] [int] IDENTITY(1,1) NOT NULL,
    [SSN] [char](11) ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    [FirstName] [nvarchar](50) NOT NULL,
    [LastName] [nvarchar](50) NOT NULL,
    [Salary] [int] ENCRYPTED WITH (
        COLUMN_ENCRYPTION_KEY = [CEK1],
        ENCRYPTION_TYPE = Randomized,
        ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL,
    CONSTRAINT [PK_dbo.Employees] PRIMARY KEY CLUSTERED (
[EmployeeID] ASC
)
) ON [PRIMARY]
GO
```

CEK1 est supposée être une clé de chiffrement de colonne prenant en charge les enclaves.


```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Data.SqlClient;
using System.Data;
namespace ConsoleApp1
{
   class Program
   {
      static void Main(string\[\] args)
   {

   string connectionString = "Data Source = myserver; Initial Catalog = ContosoHR; Column Encryption Setting = Enabled;Enclave Attestation Url = https://10.193.16.185/Attestation/attestationservice.svc/signingCertificates; Integrated Security = true";

using (SqlConnection connection = new SqlConnection(connectionString))
{
   connection.Open();
   
   SqlCommand cmd = connection.CreateCommand();
   cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [Salary] FROM [dbo].[Employees] WHERE [SSN] LIKE @SSNPattern AND [Salary] > @MinSalary;";
   
   SqlParameter paramSSNPattern = cmd.CreateParameter();
   
   paramSSNPattern.ParameterName = @"@SSNPattern";
   paramSSNPattern.DbType = DbType.AnsiStringFixedLength;
   paramSSNPattern.Direction = ParameterDirection.Input;
   paramSSNPattern.Value = "%1111";
   paramSSNPattern.Size = 11;
   
   cmd.Parameters.Add(paramSSNPattern);
   
   SqlParameter MinSalary = cmd.CreateParameter();
   
   MinSalary.ParameterName = @"@MinSalary";
   MinSalary.DbType = DbType.Int32;
   MinSalary.Direction = ParameterDirection.Input;
   MinSalary.Value = 900;
   
   cmd.Parameters.Add(MinSalary);
   cmd.ExecuteNonQuery();
   
   SqlDataReader reader = cmd.ExecuteReader();
   while (reader.Read())
   
   {
     Console.WriteLine(reader);
     Console.WriteLine(reader\[0\] + ", " + reader\[1\] + ", " + reader\[2\] + ", " + reader\[3\]);
   }

   Console.ReadKey();

   }
  }
 }
}
```
