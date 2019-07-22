---
title: Configurer Always Encrypted à l’aide de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
ms.assetid: 12f2bde5-e100-41fa-b474-2d2332fc7650
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 702bc2a5dd5578bff85d7e386e2abe3a4a0a658f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68050081"
---
# <a name="configure-always-encrypted-using-powershell"></a>Configurer Always Encrypted à l’aide de PowerShell
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Le module SqlServer PowerShell fournit des applets de commande pour la configuration [d’Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) dans Azure SQL Database et SQL Server 2016.

Les applets de commande Always Encrypted du module SqlServer fonctionnent avec des clés ou des données sensibles. Il est donc important d’exécuter ces applets de commande sur un ordinateur sécurisé. Quand vous gérez Always Encrypted, exécutez les applets de commande à partir d’un autre ordinateur que celui qui héberge votre instance de SQL Server.

L’objectif principal d’Always Encrypted étant de garantir la sécurité des données sensibles chiffrées même si le système de base de données est compromis, l’exécution d’un script PowerShell qui traite des clés ou des données sensibles sur l’ordinateur SQL Server peut réduire ou annuler les avantages de la fonctionnalité. Pour obtenir des recommandations supplémentaires relatives à la sécurité, consultez [Considérations en matière de sécurité pour la gestion des clés](overview-of-key-management-for-always-encrypted.md#security-considerations-for-key-management).

Vous trouverez des liens vers les articles sur les applets de commande au [bas de cette page](#aecmdletreference).

## <a name="prerequisites"></a>Conditions préalables requises

Installez le [module SqlServer](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/sqlserver) sur un ordinateur sécurisé qui n’est PAS un ordinateur qui héberge votre instance de SQL Server. Vous pouvez installer le module directement à partir de PowerShell Gallery.  Pour plus d’informations, consultez les instructions de [téléchargement](../../../ssms/download-sql-server-ps-module.md).


## <a name="importsqlservermodule"></a> Importation du module SqlServer 

Pour charger le module SqlServer

1.  Utilisez l’applet de commande **Set-ExecutionPolicy** pour définir la stratégie d’exécution de scripts appropriée.
2.  Utilisez l’applet de commande **Import-Module** pour importer le module SqlServer.

Cet exemple charge le module SQL Server.

```
# Import the SQL Server Module.  
Import-Module "SqlServer" 
```

## <a name="connectingtodatabase"></a> Connexion à une base de données

Certaines des applets de commande Always Encrypted fonctionnent avec des données ou des métadonnées dans la base de données et nécessitent que vous vous connectiez d’abord à la base de données. Il existe deux méthodes recommandées pour se connecter à une base de données lors de la configuration d’Always Encrypted à l’aide du module SqlServer : 
1. Se connecter à l’aide de SQL Server PowerShell.
2. Se connecter à l’aide de SQL Server Management Objects (SMO).

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

### <a name="using-sql-server-powershell"></a>Utilisation de SQL Server PowerShell

Cette méthode fonctionne uniquement pour SQL Server (elle n’est pas prise en charge dans Azure SQL Database).

Avec SQL Server PowerShell, vous pouvez parcourir les chemins à l’aide d’alias Windows PowerShell semblables aux commandes que vous utilisez généralement pour parcourir les chemins du système de fichiers. Une fois que vous accédez à l’instance cible et à la base de données, les applets de commande suivantes ciblent cette base de données, comme indiqué dans l’exemple suivant :

```
# Import the SqlServer module.
Import-Module "SqlServer"
# Navigate to the database in the remote instance.
cd SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
# List column master keys in the above database.
Get-SqlColumnMasterKey
```

 
Vous pouvez également spécifier un chemin de base de données à l’aide du paramètre générique **Path** , au lieu de naviguer dans la base de données.


```
# Import the SqlServer module.
Import-Module "SqlServer" 
# List column master keys for the specified database.
Get-SqlColumnMasterKey -Path SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
```
 
### <a name="using-smo"></a>Utilisation de SMO

Cette méthode fonctionne pour Azure SQL Database et SQL Server.
Avec SMO, vous pouvez créer un objet de la [Classe Database](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.database.aspx), puis passer l’objet à l’aide du paramètre **InputObject** d’une applet de commande qui se connecte à la base de données.


```
# Import the SqlServer module
Import-Module "SqlServer"  

# Connect to your database (Azure SQL database).
$serverName = "<Azure SQL server name>.database.windows.net"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Authentication = Active Directory Integrated"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName] 

# List column master keys for the specified database.
Get-SqlColumnMasterKey -InputObject $database
```


Vous pouvez également utiliser un canal :


```
$database | Get-SqlColumnMasterKey
```

## <a name="always-encrypted-tasks-using-powershell"></a>Tâches Always Encrypted à l’aide de PowerShell

- [Configurer des clés Always Encrypted à l’aide de PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell.md) 
- [Permuter des clés Always Encrypted à l’aide de PowerShell](../../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-powershell.md)
- [Configurer le chiffrement de colonne à l’aide de PowerShell](../../../relational-databases/security/encryption/configure-column-encryption-using-powershell.md)


##  <a name="aecmdletreference"></a> Référence des applets de commande Always Encrypted

Les applets de commande PowerShell suivantes sont disponibles pour Always Encrypted :

|APPLET DE COMMANDE |Description
|:---|:---
|**[Add-SqlAzureAuthenticationContext](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/add-sqlazureauthenticationcontext)**   |Effectue une authentification dans Azure et acquiert un jeton d’authentification.
|**[Add-SqlColumnEncryptionKeyValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/add-sqlcolumnencryptionkeyvalue)**   |Ajoute une nouvelle valeur chiffrée pour un objet de clé de chiffrement de colonne existant dans la base de données.
|**[Complete-SqlColumnMasterKeyRotation](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/complete-sqlcolumnmasterkeyrotation)**   |Met fin à la permutation d’une clé principale de colonne
|**[Get-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/get-sqlcolumnencryptionkey)** |Retourne tous les objets de clés de chiffrement de colonne définis dans la base de données, ou retourne un objet de clé de chiffrement de colonne portant le nom spécifié.
|**[Get-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/get-sqlcolumnmasterkey)** |Retourne les objets de clés principales de colonne définis dans la base de données, ou retourne un objet de clé principale de colonne portant le nom spécifié.
|**[Invoke-SqlColumnMasterKeyRotation](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/invoke-sqlcolumnmasterkeyrotation)**   |Lance la permutation d’une clé principale de colonne.
|**[New-SqlAzureKeyVaultColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlazurekeyvaultcolumnmasterkeysettings)**   |Crée un objet SqlColumnMasterKeySettings décrivant une clé asymétrique stockée dans Azure Key Vault.
|**[New-SqlCngColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcngcolumnmasterkeysettings)**   |Crée un objet SqlColumnMasterKeySettings décrivant une clé asymétrique stockée dans un magasin de clés prenant en charge l’API CNG (Cryptography Next Generation).
|**[New-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionkey)** |Crée un objet clé de chiffrement de colonne dans la base de données.
|**[New-SqlColumnEncryptionKeyEncryptedValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionkeyencryptedvalue)** |Génère une valeur chiffrée d’une clé de chiffrement de colonne.
|**[New-SqlColumnEncryptionSettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnencryptionsettings)**   |Crée un objet SqlColumnEncryptionSettings qui encapsule des informations sur le chiffrement d’une colonne unique, notamment le type de chiffrement et la clé de chiffrement de colonne.
|**[New-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnmasterkey)** |Crée un objet clé principale de colonne dans la base de données.
|**[New-SqlColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcolumnmasterkeysettings)**|Crée un objet SqlColumnMasterKeySettings pour une clé principale de colonne avec le fournisseur et le chemin d’accès à la clé spécifiés.
|**[New-SqlCspColumnMasterKeySettings](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/new-sqlcspcolumnmasterkeysettings)**   |Crée un objet SqlColumnMasterKeySettings décrivant une clé asymétrique stockée dans un magasin de clés avec un fournisseur de services de chiffrement prenant en charge l’API CAPI (Cryptography API).
|**[Remove-SqlColumnEncryptionKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnencryptionkey)**   |Supprime l’objet de clé de chiffrement de colonne de la base de données.
|**[Remove-SqlColumnEncryptionKeyValue](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnencryptionkeyvalue)** |Supprime une valeur chiffrée d’un objet de clé de chiffrement de colonne existant dans la base de données.
|**[Remove-SqlColumnMasterKey](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/remove-sqlcolumnmasterkey)**   |Supprime l’objet de clé principale de colonne de la base de données.
|**[Set-SqlColumnEncryption](https://docs.microsoft.com/powershell/sqlserver/sqlserver/vlatest/set-sqlcolumnencryption)**   |Chiffre, déchiffre ou rechiffre les colonnes spécifiées dans la base de données.



## <a name="additional-resources"></a>Ressources supplémentaires

- [Always Encrypted (moteur de base de données)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Vue d’ensemble de la gestion des clés pour Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Utilisation d’Always Encrypted avec le Fournisseur de données .NET Framework pour SQL Server](../../../relational-databases/security/encryption/always-encrypted-client-development.md)
- [Configurer Always Encrypted à l’aide de SQL Server Management Studio](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md)


