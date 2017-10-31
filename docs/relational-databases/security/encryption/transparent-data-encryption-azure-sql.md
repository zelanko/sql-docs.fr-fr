---
title: TDE pour Azure SQL Database et Data Warehouse | Microsoft Docs
description: "Fournit une vue d’ensemble de la fonctionnalité Transparent Data Encryption pour SQL Database et Data Warehouse. Le document décrit les avantages de cette fonctionnalité, ainsi que les options de configuration disponibles, comme le TDE géré par le service et Bring Your Own Key (Apportez votre propre clé)."
keywords: 
services: sql-database
documentationcenter: 
author: becczhang
manager: cguyer
editor: 
ms.assetid: 
ms.service: sql-database
ms.custom: security
ms.workload: On Demand
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 08/07/2017
ms.author: rebeccaz
ms.translationtype: HT
ms.sourcegitcommit: 46b16dcf147dbd863eec0330e87511b4ced6c4ce
ms.openlocfilehash: 35c94a39989fda76ea023588b2d7a3aa4e463262
ms.contentlocale: fr-fr
ms.lasthandoff: 09/05/2017

---


# <a name="transparent-data-encryption-for-azure-sql-database-and-data-warehouse"></a>Transparent Data Encryption pour Azure SQL Database et Data Warehouse

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Transparent Data Encryption (TDE) vous permet de mieux protéger votre environnement Azure SQL Database et Data Warehouse contre les menaces d’activités malveillantes. Cette protection est assurée par le chiffrement et le déchiffrement en temps réel de la base de données, les sauvegardes associées et l’utilisation de fichiers journaux de transactions au repos, sans avoir à modifier l’application.

TDE chiffre le stockage d’une base de données entière à l’aide d’une clé symétrique appelée clé de chiffrement de la base de données (« clé DEK »). Cette clé de chiffrement de la base de données est protégée par le protecteur TDE, qui est un certificat géré par le service (« TDE géré par le service ») ou une clé asymétrique stockée dans Azure Key Vault (« Bring Your Own Key »). Le protecteur TDE est défini au niveau du serveur. 

Au démarrage de la base de données, la clé DEK chiffrée est déchiffrée, puis elle est utilisée pour déchiffrer et rechiffrer les fichiers de la base de données dans le processus du moteur SQL. TDE effectue le chiffrement et le déchiffrement des données d’E/S en temps réel au niveau de la page. Chaque page est déchiffrée quand elle est lue en mémoire et chiffrée avant d’être écrite sur le disque. Pour obtenir une description générale de TDE, consultez [Transparent Data Encryption (TDE)](transparent-data-encryption.md).

Quand SQL Server est exécuté sur une machine virtuelle Azure, il peut également utiliser une clé asymétrique fournie par Key Vault. Les étapes de configuration sont différentes par rapport à l’utilisation d’une clé asymétrique dans Azure SQL Database. Pour plus d’informations, consultez [Gestion de clés extensible à l’aide d’Azure Key Vault (SQL Server)](extensible-key-management-using-azure-key-vault-sql-server.md).

## <a name="service-managed-tde"></a>TDE géré par le service

Dans Azure, la configuration par défaut de TDE spécifie que la clé de chiffrement de la base de données est protégée par un certificat de serveur intégré. Chaque serveur est associé à un certificat de serveur intégré unique. Si une base de données est dans une relation de géoréplication, la base de données primaire et la base de données géosecondaire sont toutes les deux protégées par la clé primaire du serveur parent. Si deux bases de données sont connectées au même serveur, elles partagent le même certificat intégré. Microsoft fait automatiquement alterner ces certificats au moins tous les 90 jours.

Microsoft déplace et gère également de façon transparente les clés en fonction des besoins pour la géoréplication et les restaurations. 

> [!IMPORTANT]
> Toutes les nouvelles bases de données SQL sont chiffrées par défaut à l’aide du TDE géré par le service. Les bases de données antérieures à mai 2017 ou celles ayant été créées par restauration, géoréplication ou copie de base de données ne sont pas chiffrées par défaut.
>

## <a name="bring-your-own-key"></a>Bring Your Own Key

Grâce à la prise en charge de la fonctionnalité BYOK (Bring Your Own Key), l’utilisateur peut gérer lui-même ses clés de chiffrement TDE et déterminer quels autres utilisateurs sont autorisés à y accéder, et à quels moments. Azure Key Vault (AKV), qui est le système de gestion des clés externes sur le cloud d’Azure, est le premier service de gestion de clés ayant intégré TDE avec la prise en charge de BYOK. Avec BYOK, la clé de chiffrement de la base de données est protégée par une clé asymétrique stockée dans AKV. La clé asymétrique ne quitte jamais Key Vault. Une fois que le serveur a obtenu les autorisations d’accès à un coffre de clés, il envoie les demandes d’opérations de clé de base à ce coffre par le biais du service Key Vault. La clé asymétrique est définie au niveau du serveur et est héritée par toutes les bases de données sur ce serveur. Avec la prise en charge de BYOK, les utilisateurs peuvent maintenant gérer diverses tâches de gestion des clés, y compris les rotations de clés, les autorisations d’accès à Key Vault, la suppression des clés, ainsi que l’audit et le reporting sur toutes les clés de chiffrement. Key Vault centralise la gestion des clés, utilise des modules de sécurité matériel (HSM) étroitement surveillés, et promeut la séparation de la gestion des clés et des données conformément aux réglementations. Pour en savoir plus sur le service Key Vault, consultez la [page de documentation de Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault).

Pour en savoir plus sur TDE avec prise en charge de BYOK pour Azure SQL Database et Data Warehouse, consultez [Transparent Data Encryption avec prise en charge de Bring Your Own Key](transparent-data-encryption-byok-azure-sql.md).

Pour commencer à utiliser TDE avec prise en charge de BYOK, consultez le guide pratique [Activer Transparent Data Encryption avec votre propre clé Key Vault à l’aide de PowerShell](transparent-data-encryption-byok-azure-sql-configure.md).

## <a name="moving-a-tde-protected-database"></a>Déplacement d’une base de données protégée par TDE

Il n'est pas nécessaire de déchiffrer les bases de données pour effectuer des opérations dans Azure. La base de données cible hérite de façon transparente des paramètres de TDE sur la base de données source ou sur la base de données principale. Cela inclut les opérations impliquant :
- La géorestauration
- La restauration libre-service dans le temps
- La restauration d’une base de données supprimée
- La géoréplication active
- La création d’une copie de base de données

Quand vous exportez une base de données protégée par TDE, le contenu exporté de la base de données n’est pas chiffré. Ce contenu exporté est stocké dans des fichiers BACPAC non chiffrés. Vous devez donc protéger les fichiers BACPAC de façon appropriée et activer TDE une fois l’importation de la nouvelle base de données terminée.

Par exemple, si le fichier BACPAC est exporté à partir d’une instance SQL Server locale, le contenu importé de la nouvelle base de données n’est pas automatiquement chiffré. De la même façon, si le fichier BACPAC est exporté vers une instance SQL Server locale, la nouvelle base de données n’est pas automatiquement chiffrée.

La seule exception est quand l’exportation est effectuée entre deux instances Azure SQL Database. TDE est activé dans la nouvelle base de données, mais le fichier PACPAC proprement dit n’est pas chiffré.

## <a name="managing-transparent-data-encryption-in-the-azure-portal"></a>Gestion de Transparent Data Encryption dans le portail Azure

Pour configurer TDE par le biais du portail Azure, vous devez être connecté en tant que Propriétaire, Collaborateur ou Gestionnaire de sécurité SQL Azure. 

Transparent Data Encryption est défini au niveau de la base de données. Pour activer TDE sur une base de données, accédez au [portail Azure](https://portal.azure.com) et connectez-vous avec votre compte Administrateur ou Collaborateur Azure. Accédez aux paramètres TDE pour votre base de données utilisateur. Par défaut, le TDE géré par le service est utilisé, et un certificat TDE est automatiquement généré pour le serveur contenant la base de données. 

![TDE géré par le service](./media/transparent-data-encryption-azure-sql/service-managed-tde.png)  

La clé principale TDE, également appelée *protecteur TDE*, est définie au niveau du serveur. Pour utiliser TDE avec prise en charge de Bring Your Own Key et protéger vos bases de données à l’aide d’une clé fournie par Azure Key Vault, accédez aux paramètres TDE définis pour votre serveur. 

![TDE avec prise en charge de BYOK](./media/transparent-data-encryption-azure-sql/tde-byok-support.png) 

## <a name="managing-transparent-data-encryption-using-powershell"></a>Gestion de Transparent Data Encryption à l’aide de PowerShell

Pour configurer TDE par le biais de PowerShell, vous devez être connecté en tant que Propriétaire, Collaborateur ou Gestionnaire de sécurité SQL Azure. 

| Applet de commande |  Description |
| --- | --- |
| [Set-AzureRmSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/set-azurermsqldatabasetransparentdataencryption) |Active ou désactive TDE pour une base de données.|
| [Get-AzureRmSqlDatabaseTransparentDataEncryption](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryption) |Obtient l’état de TDE pour une base de données. |
| [Get-AzureRmSqlDatabaseTransparentDataEncryptionActivity](/powershell/module/azurerm.sql/get-azurermsqldatabasetransparentdataencryptionactivity) |Vérifie la progression du chiffrement pour une base de données. |
| [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) |Ajoute une clé Key Vault à un serveur SQL Server. |
| [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) |Obtient les clés Key Vault d’un serveur SQL Server. |
| [Set-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/set-azurermsqlservertransparentdataencryptionprotector) |Définit le protecteur TDE pour un serveur SQL Server. |
| [Get-AzureRmSqlServerTransparentDataEncryptionProtector](/powershell/module/azurerm.sql/get-azurermsqlservertransparentdataencryptionprotector) |Obtient le protecteur TDE. |
| [Remove-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/remove-azurermsqlserverkeyvaultkey) |Supprime une clé Key Vault sur un serveur SQL Server. |
|  | |

## <a name="managing-transparent-data-encryption-using-transact-sql"></a>Gestion de Transparent Data Encryption à l’aide de Transact-SQL

Connectez-vous à la base de données en tant qu’administrateur ou membre du rôle **dbmanager** dans la base de données MASTER.

| Command |  Description |
| --- | --- |
| [ALTER DATABASE (Azure SQL Database)](/sql/t-sql/statements/alter-database-azure-sql-database) | Utilisez SET ENCRYPTION ON/OFF pour chiffrer ou déchiffrer une base de données. |
| [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) |Retourne des informations sur l'état de chiffrement d'une base de données et de ses clés de chiffrement de base de données associées. |
| [sys.dm_pdw_nodes_database_encryption_keys](https://docs.microsoft.com/en-us/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql) |Retourne des informations sur l’état de chiffrement de chaque nœud Data Warehouse et des clés de chiffrement de base de données associées. | 
|  | |

Vous ne pouvez pas utiliser Transact-SQL pour remplacer le protecteur TDE par une clé Azure Key Vault. Utilisez PowerShell ou le portail Azure à la place.

## <a name="managing-transparent-data-encryption-using-rest-api"></a>Gestion de Transparent Data Encryption à l’aide de l’API REST
 
Pour configurer TDE par le biais de l’API REST, vous devez être connecté en tant que Propriétaire, Collaborateur ou Gestionnaire de sécurité SQL Azure. 

| Command |  Description |
| --- | --- |
|[Créer ou mettre à jour un serveur](/rest/api/sql/servers/createorupdate)|Ajoute une identité AAD à un serveur SQL Server (utilisé pour accorder l’accès à Key Vault).|
|[Créer ou mettre à jour une clé serveur](/rest/api/sql/serverkeys/createorupdate)|Ajoute une clé Key Vault à un serveur SQL Server.|
|[Supprimer une clé serveur](/rest/api/sql/serverkeys/delete)|Supprime une clé Key Vault sur un serveur SQL Server.|
|[Obtenir des clés serveur](/rest/api/sql/serverkeys/get)|Obtient une clé Key Vault spécifique d’un serveur SQL Server.|
|[Afficher les clés serveur par serveur](/rest/api/sql/serverkeys/listbyserver)|Obtient les clés Key Vault d’un serveur SQL Server.|
|[Créer ou mettre à jour le protecteur de chiffrement](/rest/api/sql/encryptionprotectors/createorupdate)|Définit le protecteur TDE pour un serveur SQL Server.|
|[Obtenir le protecteur de chiffrement](/rest/api/sql/encryptionprotectors/get)|Obtient le protecteur TDE pour un serveur SQL Server.|
|[Afficher les protecteurs de chiffrement par serveur](/rest/api/sql/encryptionprotectors/listbyserver)|Obtient les protecteurs TDE d’un serveur SQL Server.|
|[Créer ou mettre à jour la configuration de TDE](/rest/api/sql/transparentdataencryptions/createorupdate)|Active ou désactive TDE pour une base de données.|
|[Obtenir la configuration de TDE](/rest/api/sql/transparentdataencryptions/get)|Obtient la configuration de TDE pour une base de données.|
|[Afficher le résultat de la configuration de TDE](/rest/api/sql/transparentdataencryptionactivities/ListByConfiguration)|Obtient le résultat du chiffrement d’une base de données.|

## <a name="next-steps"></a>Étapes suivantes

- Pour obtenir une description générale de TDE, consultez [Transparent Data Encryption (TDE)](transparent-data-encryption.md).

- Pour en savoir plus sur TDE avec prise en charge de BYOK pour Azure SQL Database et Data Warehouse, consultez [Transparent Data Encryption (TDE) avec prise en charge de Bring Your Own Key](transparent-data-encryption-byok-azure-sql.md).

- Pour commencer à utiliser TDE avec prise en charge de BYOK, consultez le guide pratique [Activer Transparent Data Encryption avec votre propre clé Key Vault à l’aide de PowerShell](transparent-data-encryption-byok-azure-sql-configure.md).

- Pour plus d’informations sur Key Vault, consultez la [page de documentation de Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault).

