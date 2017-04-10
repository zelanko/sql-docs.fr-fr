---
title: "Configurer Always Encrypted &#224; l’aide de PowerShell | Microsoft Docs"
ms.custom: ""
ms.date: "09/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-security"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12f2bde5-e100-41fa-b474-2d2332fc7650
caps.latest.revision: 15
author: "stevestein"
ms.author: "sstein"
manager: "jhubbard"
caps.handback.revision: 13
---
# Configurer Always Encrypted &#224; l’aide de PowerShell
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Le module SqlServer PowerShell fournit des applets de commande pour la configuration [d’Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) dans Azure SQL Database et SQL Server 2016.

La plupart des applets de commande pour Always Encrypted dans le module SQL Server fonctionnent avec des clés Always Encrypted ou des données sensibles stockées dans des colonnes chiffrées. Il est donc important d’exécuter ces applets de commande sur un ordinateur sécurisé. Lors de la gestion d’Always Encrypted, exécutez les applets de commande à partir d’un ordinateur autre que celui qui héberge votre instance de SQL Server. 

L’objectif principal d’Always Encrypted étant de garantir la sécurité des données sensibles chiffrées même si le système de base de données est compromis, l’exécution d’un script PowerShell qui traite des clés ou des données sensibles sur l’ordinateur SQL Server peut réduire ou annuler les avantages de la fonctionnalité. Pour obtenir des recommandations supplémentaires relatives à la sécurité, consultez [Considérations en matière de sécurité pour la gestion des clés](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md#SecurityForKeyManagement).

Vous trouverez des liens vers les articles sur les applets de commande au [bas de cette page](#aecmdletreference).

## Conditions préalables

Installez le [module SqlServer](https://msdn.microsoft.com/library/mt740629.aspx) sur un ordinateur sécurisé qui n’est PAS un ordinateur qui héberge votre instance de SQL Server. 

Installez le module SqlServer en installant la dernière version de [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx).
Notez que le module *SqlServer* est différent du module *sqlps*, qui ne prend pas en charge Always Encrypted. Pour plus d’informations, consultez le billet de blog [SQL PowerShell : mise à jour de juillet 2016](https://blogs.technet.microsoft.com/dataplatforminsider/2016/06/30/sql-powershell-july-2016-update) de l’équipe.

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

### Utilisation de SQL Server PowerShell

Cette méthode fonctionne uniquement pour SQL Server (elle n’est pas prise en charge dans Azure SQL Database).

Avec SQL Server PowerShell, vous pouvez parcourir les chemins à l’aide d’alias Windows PowerShell semblables aux commandes que vous utilisez généralement pour parcourir les chemins du système de fichiers. Une fois que vous avez accédé à l’instance cible et à la base de données, les applets de commande suivantes cibleront cette base de données, comme illustré dans l’exemple suivant :

```
# Import the SqlServer module.
Import-Module "SqlServer"
# Navigate to the database in the remote instance.
cd SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
# List column master keys in the above database.
Get-SqlColumnMasterKey
```

 
Vous pouvez également spécifier un chemin de base de données à l’aide du paramètre générique **Path**, au lieu de naviguer dans la base de données.


```
# Import the SqlServer module.
Import-Module "SqlServer" 
# List column master keys for the specified database.
Get-SqlColumnMasterKey -Path SQLSERVER:\SQL\servercomputer\DEFAULT\Databases\yourdatabase
```
 
### Utilisation de SMO

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

## Tâches Always Encrypted à l’aide de PowerShell

- [Configurer des clés Always Encrypted à l’aide de PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell.md) 
- [Permuter des clés Always Encrypted à l’aide de PowerShell](../../../relational-databases/security/encryption/rotate-always-encrypted-keys-using-powershell.md)
- [Configurer le chiffrement de colonne à l’aide de PowerShell](../../../relational-databases/security/encryption/configure-column-encryption-using-powershell.md)


##  <a name="aecmdletreference"></a> Référence des applets de commande Always Encrypted

Les applets de commande PowerShell suivantes sont disponibles pour Always Encrypted :

|APPLET DE COMMANDE |Description
|:---|:---
|**[Add-SqlAzureAuthenticationContext](https://msdn.microsoft.com/library/mt759815.aspx)**  |Effectue une authentification dans Azure et acquiert un jeton d’authentification.
|**[Add-SqlColumnEncryptionKeyValue](https://msdn.microsoft.com/library/mt759817.aspx)**    |Ajoute une nouvelle valeur chiffrée pour un objet de clé de chiffrement de colonne existant dans la base de données.
|**[Complete-SqlColumnMasterKeyRotation](https://msdn.microsoft.com/library/mt759791.aspx)**    |Met fin à la permutation d’une clé principale de colonne
|**[Get-SqlColumnEncryptionKey](https://msdn.microsoft.com/library/mt759814.aspx)** |Retourne tous les objets de clés de chiffrement de colonne définis dans la base de données, ou retourne un objet de clé de chiffrement de colonne portant le nom spécifié.
|**[Get-SqlColumnMasterKey](https://msdn.microsoft.com/library/mt759782.aspx)** |Retourne les objets de clés principales de colonne définis dans la base de données, ou retourne un objet de clé principale de colonne portant le nom spécifié.
|**[Invoke-SqlColumnMasterKeyRotation](https://msdn.microsoft.com/library/mt759810.aspx)**  |Lance la permutation d’une clé principale de colonne.
|**[New-SqlAzureKeyVaultColumnMasterKeySettings](https://msdn.microsoft.com/library/mt759795.aspx)**    |Crée un objet SqlColumnMasterKeySettings décrivant une clé asymétrique stockée dans Azure Key Vault.
|**[New-SqlCngColumnMasterKeySettings](https://msdn.microsoft.com/library/mt759818.aspx)**  |Crée un objet SqlColumnMasterKeySettings décrivant une clé asymétrique stockée dans un magasin de clés prenant en charge l’API CNG (Cryptography Next Generation).
|**[New-SqlColumnEncryptionKey](https://msdn.microsoft.com/library/mt759808.aspx)** |Crée un objet de clé de chiffrement de colonne dans la base de données.
|**[New-SqlColumnEncryptionKeyEncryptedValue](https://msdn.microsoft.com/library/mt759794.aspx)**   |Génère une valeur chiffrée d’une clé de chiffrement de colonne.
|**[New-SqlColumnEncryptionSettings](https://msdn.microsoft.com/library/mt759825.aspx)**    |Crée un objet SqlColumnEncryptionSettings qui encapsule des informations sur le chiffrement d’une colonne unique, notamment le type de chiffrement et la clé de chiffrement de colonne.
|**[New-SqlColumnMasterKey](https://msdn.microsoft.com/library/mt759813.aspx)** |Crée un objet de clé principale de colonne dans la base de données.
|**New-SqlColumnMasterKeySettings**|Crée un objet SqlColumnMasterKeySettings pour une clé principale de colonne avec le fournisseur et le chemin d’accès à la clé spécifiés.
|**[New-SqlCspColumnMasterKeySettings](https://msdn.microsoft.com/library/mt759784.aspx)**  |Crée un objet SqlColumnMasterKeySettings décrivant une clé asymétrique stockée dans un magasin de clés avec un fournisseur de services de chiffrement prenant en charge l’API CAPI (Cryptography API).
|**[Remove-SqlColumnEncryptionKey](https://msdn.microsoft.com/library/mt759786.aspx)**  |Supprime l’objet de clé de chiffrement de colonne de la base de données.
|**[Remove-SqlColumnEncryptionKeyValue](https://msdn.microsoft.com/library/mt759783.aspx)** |Supprime une valeur chiffrée d’un objet de clé de chiffrement de colonne existant dans la base de données.
|**[Remove-SqlColumnMasterKey](https://msdn.microsoft.com/library/mt759800.aspx)**  |Supprime l’objet de clé principale de colonne de la base de données.
|**[Set-SqlColumnEncryption](https://msdn.microsoft.com/library/mt759790.aspx)**    |Chiffre, déchiffre ou rechiffre les colonnes spécifiées dans la base de données.



## Ressources supplémentaires

- [Always Encrypted (moteur de base de données)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Vue d’ensemble de la gestion des clés pour Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Utilisation d’Always Encrypted avec le Fournisseur de données .NET Framework pour SQL Server](../../../relational-databases/security/encryption/always-encrypted-client-development.md)
- [Configurer Always Encrypted à l’aide de SQL Server Management Studio](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md)

