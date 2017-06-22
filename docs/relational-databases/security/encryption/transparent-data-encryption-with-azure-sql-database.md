---
title: "Chiffrement transparent des données avec Azure SQL Database | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
- MSDN content
- MSDN - SQL DB
ms.date: 09/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TDE, SQL Database
- encryption (SQL Database), TDE
- Transparent Data Encryption, SQL Database
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1c607015f1ead5b19d4c32c5bac62eb624b0578b
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="transparent-data-encryption-with-azure-sql-database"></a>Chiffrement transparent des données avec Azure SQL Database
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx_md](../../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] Le chiffrement transparent des données vous protège contre les menaces d’activités malveillantes grâce à un chiffrement et à un déchiffrement en temps réel de la base de données, des sauvegardes associées et des fichiers journaux transactionnels inactifs, sans avoir à modifier l’application.  
  
 L'ensemble de la base de données est chiffré à l'aide d'une clé symétrique, appelée clé de chiffrement de base de données. Dans [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] , la clé de chiffrement de base de données est protégée par un certificat de serveur intégré. Le certificat de serveur intégré est unique pour chaque serveur [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] . Si une base de données a une relation GeoDR, elle est protégée par une clé différente sur chaque serveur. Si deux bases de données sont connectées au même serveur, elles partagent le même certificat intégré. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] fait alterner automatiquement ces certificats au moins tous les 90 jours. Pour obtenir une description générale du chiffrement transparent des données, consultez [Chiffrement transparent des données &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md).  
  
 [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] ne prend pas en charge l'intégration du coffre de clés Azure au chiffrement transparent des données. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] s'exécute sur une machine virtuelle Azure, il peut utiliser une clé asymétrique provenant du coffre de clés. Pour plus d’informations, consultez [Gestion de clés extensible à l’aide d’Azure Key Vault &#40;SQL Server&#41;](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
##  <a name="Permissions"></a> Autorisations  
 Pour configurer la fonctionnalité TDE via le portail Azure, en utilisant l’API REST ou PowerShell, vous devez être connecté en tant que propriétaire, collaborateur ou gestionnaire de sécurité SQL Azure.  
  
 La configuration de TDE à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)] requiert les conditions suivantes :  
  
-   L’exécution de l’instruction ALTER DATABASE avec l’option SET nécessite uniquement une appartenance au rôle **dbmanager** .  
  
##  <a name="Preview"></a> Activation du chiffrement transparent des données sur une base de données à l’aide du portail  
  
1.  Visitez le portail Azure à l’adresse [https://portal.azure.com](https://portal.azure.com) et connectez-vous avec votre compte administrateur ou collaborateur Azure.  
  
2.  Dans la bannière de gauche, cliquez sur **PARCOURIR**, puis cliquez sur **Bases de données SQL**.  
  
3.  Avec **Bases de données SQL** sélectionné dans le volet gauche, cliquez sur votre base de données utilisateur.  
  
4.  Dans le volet de la base de données, cliquez sur **Tous les paramètres**.  
  
5.  Dans le volet **Paramètres** , cliquez sur **Chiffrement transparent des données** pour ouvrir le volet **Chiffrement transparent des données** .  
  
6.  Dans le volet **Chiffrement des données** , basculez le bouton **Chiffrement des données** sur **Activé**, puis cliquez sur **Enregistrer** (en haut de la page) pour appliquer le paramètre. L'élément **État du chiffrement** indiquera approximativement la progression du chiffrement transparent des données.  
  
     ![Début de chiffrement TDE d’une base de données SQL](../../../relational-databases/security/encryption/media/sqldb-tde-encrypt.png "Début de chiffrement TDE d’une base de données SQL")  
  
     Vous pouvez également surveiller la progression du chiffrement en vous connectant à la [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] à l'aide d'un outil de requête comme [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] en tant qu'utilisateur de base de données avec l'autorisation **AFFICHER L'ÉTAT DE LA BASE DE DONNÉES** . Interrogez la colonne **encryption_state** de la vue [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) .  
  
##  <a name="Encrypt"></a> Activation de TDE sur [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] en utilisant Transact-SQL  
 Les étapes suivantes permettent d’activer le chiffrement transparent des données.  
  
###  <a name="TsqlProcedure"></a>  
  
1.  Connectez-vous à la base de données en utilisant une connexion correspondant à un administrateur ou à un membre du rôle **dbmanager** dans la base de données master.  
  
2.  Exécutez les instructions suivantes pour chiffrer la base de données.  
  
    ```  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;  
    GO  
    ```  
  
3.  Pour surveiller la progression du chiffrement sur [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], les utilisateurs de base de données avec l’autorisation **AFFICHER L’ÉTAT DE LA BASE DE DONNÉES** peuvent interroger la colonne **encryption_state** de la vue [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) .  
  
##  <a name="EncryptPS"></a> Activation et désactivation de TDE sur [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] à l’aide de PowerShell  
 En utilisant Azure PowerShell, vous pouvez exécuter la commande suivante pour activer ou désactiver TDE. Vous devez connecter votre compte dans la fenêtre PS avant d’exécuter la commande. Adaptez l’exemple en utilisant vos propres valeurs pour les paramètres `ServerName`, `ResourceGroupName`et `DatabaseName` . Pour plus d'informations sur PowerShell, consultez [Comment installer et configurer Azure PowerShell](http://azure.microsoft.com/documentation/articles/powershell-install-configure/).  
  
> [!NOTE]  
>  Pour continuer, vous devez installer et configurer la version 1.0 d’Azure PowerShell. La version 0.9.8 peut être utilisée, mais elle est déconseillée car elle suppose de basculer sur les applets de commande AzureResourceManager à l’aide de la commande `PS C:\> Switch-AzureMode -Name AzureResourceManager` .  
  
###  <a name="PSlProcedure"></a>  
  
1.  Pour activer TDE, retournez l’état de TDE et affichez l’activité de chiffrement :  
  
    ```  
    PS C:\> Set-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"  
  
    PS C:\> Get-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
  
    PS C:\> Get-AzureRMSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
    ```  
  
     Si vous utilisez la version 0.9.8, utilisez les commandes Get-AzureSqlDatabaseTransparentDataEncryptionActivity AzureSqlDatabaseTransparentDataEncryption-Set et Get-AzureSqlDatabaseTransparentDataEncryption.  
  
2.  Pour désactiver TDE :  
  
    ```  
    PS C:\> Set-AzureRMSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"  
  
    ```  
  
     Si vous utilisez la version 0.9.8, utilisez la commande Set-AzureSqlDatabaseTransparentDataEncryption.  
  
##  <a name="Decrypt"></a> Déchiffrement d'une base de données protégée par TDE sur la [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]  
  
#### <a name="to-disable-tde-by-using-the-azure-portal"></a>Pour désactiver TDE en utilisant le portail Azure  
  
1.  Visitez le portail Azure à l’adresse [https://portal.azure.com](https://portal.azure.com) et connectez-vous avec votre compte administrateur ou collaborateur Azure.  
  
2.  Dans la bannière de gauche, cliquez sur **PARCOURIR**, puis cliquez sur **Bases de données SQL**.  
  
3.  Avec **Bases de données SQL** sélectionné dans le volet gauche, cliquez sur votre base de données utilisateur.  
  
4.  Dans le volet de la base de données, cliquez sur **Tous les paramètres**.  
  
5.  Dans le volet **Paramètres** , cliquez sur **Chiffrement transparent des données** pour ouvrir le volet **Chiffrement transparent des données** .  
  
6.  Dans le volet **Chiffrement transparent des données** , basculez le bouton **Chiffrement des données** sur **Désactivé**, puis cliquez sur **Enregistrer** (en haut de la page) pour appliquer le paramètre. L'élément **État du chiffrement** indiquera approximativement la progression du déchiffrement transparent des données.  
  
     Vous pouvez également surveiller la progression du déchiffrement en vous connectant à la [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] à l'aide d'un outil de requête comme [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] en tant qu'utilisateur de base de données avec l'autorisation **AFFICHER L'ÉTAT DE LA BASE DE DONNÉES** . Interrogez la colonne **encryption_state** de la vue [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) .  
  
#### <a name="to-disable-tde-by-using-transact-sql"></a>Pour désactiver TDE en utilisant Transact-SQL  
  
1.  Connectez-vous à la base de données en utilisant une connexion correspondant à un administrateur ou à un membre du rôle **dbmanager** dans la base de données master.  
  
2.  Exécutez les instructions suivantes pour déchiffrer la base de données.  
  
    ```  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;  
    GO  
    ```  
  
3.  Pour surveiller la progression du chiffrement sur [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], les utilisateurs de base de données avec l’autorisation **AFFICHER L’ÉTAT DE LA BASE DE DONNÉES** peuvent interroger la colonne **encryption_state** de la vue [sys.dm_database_encryption_keys](../../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) .  
  
##  <a name="Working"></a> Déplacement d’une base de données protégée par le chiffrement transparent des données sur [!INCLUDE[ssSDS](../../../includes/sssds-md.md)]  
 Il n'est pas nécessaire de déchiffrer les bases de données pour effectuer des opérations dans Azure. La base de données cible hérite de façon transparente des paramètres de TDE sur la base de données source ou sur la base de données principale. Cela inclut les opérations impliquant :  
  
-   La géo-restauration  
  
-   La restauration à un moment donné en libre-service  
  
-   La restauration d'une base de données supprimée  
  
-   La géo-réplication active  
  
-   La création d'une copie de base de données  
  
 Lors de l’exportation d’une base de données protégée par TDE à l’aide de la fonction d’exportation de base de données dans le portail [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] ou à l’aide de l’Assistant Importation et exportation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , le contenu de la base de données n’est pas chiffré. Ce contenu exporté est stocké dans des fichiers .bacpac non chiffrés. Veillez à protéger les fichiers .bacpac de façon appropriée et à activer le TDE une fois l'importation de la base de données terminée. 
 
 Par exemple, si le fichier .bacpac est exporté à partir d’une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]locale, le contenu importé de la nouvelle base de données n’est pas automatiquement chiffré. Par exemple, si le fichier .bacpac est exporté à partir d’une instance [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] vers une instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]locale, la base de données n’est là non plus pas automatiquement chiffrée.  
 
 La seule exception concerne l’exportation vers et à partir de [!INCLUDE[ssSDSFull](../../../includes/sssdsfull-md.md)] . TDE est activé dans la nouvelle base de données, mais le fichier .bacpac n’est toujours pas chiffré.
  
## <a name="related-sql-server-topic"></a>Rubrique SQL Server connexes  
 [Activer le chiffrement transparent des données à l’aide de la gestion de clés extensible (EKM)](../../../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Chiffrement transparent des données &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../../t-sql/statements/create-credential-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-database-transact-sql.md)  
  
  

