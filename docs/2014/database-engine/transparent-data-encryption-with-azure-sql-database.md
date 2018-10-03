---
title: Chiffrement transparent des données avec Azure SQL Database | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TDE, SQL Database
- Transparent Data Encryption, SQL Database
- encryption (SQL Database) TDE
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3551cf4db3ab1b84f04ba13dea414943fbb2ef44
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049779"
---
# <a name="transparent-data-encryption-with-azure-sql-database"></a>Chiffrement transparent des données avec Azure SQL Database
  [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] chiffrement transparent des données (version préliminaire) protège contre les menaces d’activités malveillantes en effectuant un chiffrement en temps réel et déchiffrement de la base de données, les sauvegardes associées et les fichiers journaux des transactions au repos sans nécessiter de modifications de l’application.  
  
 L'ensemble de la base de données est chiffré à l'aide d'une clé symétrique, appelée clé de chiffrement de base de données. Dans [!INCLUDE[ssSDS](../includes/sssds-md.md)] , la clé de chiffrement de base de données est protégée par un certificat de serveur intégré. Le certificat de serveur intégré est unique pour chaque serveur [!INCLUDE[ssSDS](../includes/sssds-md.md)] . Si une base de données a une relation GeoDR, elle est protégée par une clé différente sur chaque serveur. Si deux bases de données sont connectées au même serveur, elles partagent le même certificat intégré. [!INCLUDE[msCoName](../includes/msconame-md.md)] fait alterner automatiquement ces certificats au moins tous les 90 jours. Pour obtenir une description générale du chiffrement transparent des données, consultez [Chiffrement transparent des données &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md).  
  
 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] ne prend pas en charge l'intégration du coffre de clés Azure au chiffrement transparent des données. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s'exécute sur une machine virtuelle Azure, il peut utiliser une clé asymétrique provenant du coffre de clés. Pour plus d’informations, consultez [exemple a : chiffrement Transparent des données à l’aide d’une clé asymétrique dans le coffre de clés](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA).  
  
||  
|-|  
|**S’applique aux**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([Aperçu dans certaines régions](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).|  
  
> [!IMPORTANT]  
>  Il s'agit actuellement d'une fonctionnalité d'aperçu. Je reconnais et accepte que l’implémentation de [!INCLUDE[ssSDS](../includes/sssds-md.md)] transparent data encryption dans mes bases de données est soumise aux conditions de version préliminaire dans mon contrat de licence (par exemple, le contrat entreprise, contrat Microsoft Azure ou abonnement en ligne Microsoft Contrat), ainsi qu’à toutes [conditions d’utilisation supplémentaires de Microsoft Azure Preview](http://azure.microsoft.com/support/legal/preview-supplemental-terms/).  
  
 L'aperçu de l'état du chiffrement transparent des données s'applique même au sous-ensemble des régions géographiques où la famille de versions V12 de [!INCLUDE[ssSDS](../includes/sssds-md.md)] est annoncée comme ayant l'état de disponibilité générale. Le chiffrement transparent des données (TDE) pour [!INCLUDE[ssSDS](../includes/sssds-md.md)] n'est pas destiné à être utilisé dans les bases de données de production tant que [!INCLUDE[msCoName](../includes/msconame-md.md)] n'annonce pas qu'il est promu de l'aperçu à l'état de disponibilité générale. Pour plus d'informations sur la [!INCLUDE[ssSDS](../includes/sssds-md.md)] V12, consultez [Nouveautés de la base de données SQL Azure](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).  
  
##  <a name="Permissions"></a> Permissions  
 Pour vous inscrire à la version Preview et configurer TDE via le portail Azure, en utilisant l'API REST ou en utilisant PowerShell, vous devez être connecté en tant que propriétaire, collaborateur ou gestionnaire de sécurité SQL Azure.  
  
 La configuration de TDE à l'aide de [!INCLUDE[tsql](../includes/tsql-md.md)] requiert les conditions suivantes :  
  
-   Vous devez être déjà inscrit pour TDE en version Preview.  
  
-   Pour créer la clé de chiffrement de base de données, vous devez être un [!INCLUDE[ssSDS](../includes/sssds-md.md)] administrateur ou vous devez être membre du **dbmanager** rôle dans le maître de base de données et ont le **contrôle** autorisation sur la base de données.  
  
-   L'exécution de l'instruction ALTER DATABASE avec l'option SET requiert seulement l'appartenance au rôle **dbmanager** .  
  
##  <a name="Preview"></a> S’inscrire pour la préversion du chiffrement transparent des données et activer TDE sur une base de données  
  
1.  Visitez le portail Azure à [ https://portal.azure.com ](https://portal.azure.com) et connectez-vous avec votre compte administrateur ou collaborateur Azure.  
  
2.  Dans la bannière de gauche, cliquez sur **PARCOURIR**, puis cliquez sur **Bases de données SQL**.  
  
3.  Avec **Bases de données SQL** sélectionné dans le volet gauche, cliquez sur votre base de données utilisateur.  
  
4.  Dans le volet de la base de données, cliquez sur **Tous les paramètres**.  
  
5.  Dans le volet **Paramètres** , cliquez sur **Chiffrement des données transparent (version Preview)** pour ouvrir le volet **Chiffrement transparent des données – version PREVIEW** . Si vous ne vous êtes pas déjà inscrit à la version Preview de TDE, les paramètres de chiffrement de données seront désactivés jusqu'à ce que vous soyez inscrit.  
  
6.  Cliquez sur **CONDITIONS D'UTILISATION DE LA VERSION PREVIEW**.  
  
7.  Lire les termes du contrat de la version préliminaire et si vous acceptez les termes du contrat, sélectionnez le **termes du contrat de données Transparent encryptionPreview** case à cocher, puis cliquez sur **OK** près du bas de la page. Retour à la **données encryptionPREVIEW** panneau, où le **Data encryption** bouton doit maintenant être activé.  
  
8.  Dans le volet **Chiffrement des données, version PREVIEW** , changez le bouton **Chiffrement des données** en **Activé**, puis cliquez sur **Enregistrer** (en haut de la page) pour appliquer le paramètre. L'élément **État du chiffrement** indiquera approximativement la progression du chiffrement transparent des données.  
  
     ![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")  
  
     Vous pouvez également surveiller la progression du chiffrement en vous connectant à la [!INCLUDE[ssSDS](../includes/sssds-md.md)] à l'aide d'un outil de requête comme [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] en tant qu'utilisateur de base de données avec l'autorisation **AFFICHER L'ÉTAT DE LA BASE DE DONNÉES** . Requête la `encryption_state` colonne de la [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) vue.  
  
##  <a name="Encrypt"></a> Activation de TDE sur [!INCLUDE[ssSDS](../includes/sssds-md.md)] en utilisant Transact-SQL  
 Les étapes suivantes supposent que vous êtes déjà inscrit à la version Preview.  
  
###  <a name="TsqlProcedure"></a>  
  
1.  Connectez-vous à la base de données en utilisant une connexion correspondant à un administrateur ou à un membre du rôle **dbmanager** dans la base de données master.  
  
2.  Exécutez les instructions suivantes pour créer une clé de chiffrement de base de données et pour chiffrer la base de données.  
  
    ```  
    -- Create the database encryption key that will be used for TDE.  
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE ##MS_TdeCertificate##;  
  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;  
    GO  
    ```  
  
3.  Pour surveiller la progression du chiffrement sur [!INCLUDE[ssSDS](../includes/sssds-md.md)], les utilisateurs disposant de la base de données le **VIEW DATABASE STATE** autorisation peut interroger le `encryption_state` colonne de la [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) vue.  
  
## <a name="enabling-tde-on-sql-database-by-using-powershell"></a>Activation de TDE sur SQL Database en utilisant PowerShell  
 En utilisant Azure PowerShell, vous pouvez exécuter la commande suivante pour activer ou désactiver TDE. Vous devez connecter votre compte dans la fenêtre PS avant d'exécuter la commande. Les étapes suivantes supposent que vous êtes déjà inscrit à la version Preview. Pour plus d'informations sur PowerShell, consultez [Comment installer et configurer Azure PowerShell](http://azure.microsoft.com/documentation/articles/powershell-install-configure/).  
  
1.  Pour activer TDE, retournez l'état de TDE et affichez l'activité de chiffrement.  
  
    ```  
    PS C:\> Switch-AzureMode -Name AzureResourceManager  
  
    PS C:\> Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"  
  
    PS C:\> Get-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
  
    PS C:\> Get-AzureSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
  
    ```  
  
2.  Pour désactiver TDE :  
  
    ```  
    PS C:\> Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"  
  
    PS C:\> Switch-AzureMode -Name AzureServiceManagement  
    ```  
  
##  <a name="Decrypt"></a> Déchiffrement d'une base de données protégée par TDE sur la [!INCLUDE[ssSDS](../includes/sssds-md.md)]  
  
#### <a name="to-disable-tde-by-using-the-azure-portal"></a>Pour désactiver TDE en utilisant le portail Azure  
  
1.  Visitez le portail Azure à [ https://portal.azure.com ](https://portal.azure.com) et connectez-vous avec votre compte administrateur ou collaborateur Azure.  
  
2.  Dans la bannière de gauche, cliquez sur **PARCOURIR**, puis cliquez sur **Bases de données SQL**.  
  
3.  Avec **Bases de données SQL** sélectionné dans le volet gauche, cliquez sur votre base de données utilisateur.  
  
4.  Dans le volet de la base de données, cliquez sur **Tous les paramètres**.  
  
5.  Dans le volet **Paramètres** , cliquez sur **Chiffrement des données transparent (version Preview)** pour ouvrir le volet **Chiffrement transparent des données – version PREVIEW** .  
  
6.  Dans le volet **Chiffrement transparent des données, version PREVIEW** , changez le bouton **Chiffrement des données** en **Désactivé**, puis cliquez sur **Enregistrer** (en haut de la page) pour appliquer le paramètre. L'élément **État du chiffrement** indiquera approximativement la progression du déchiffrement transparent des données.  
  
     Vous pouvez également surveiller la progression du déchiffrement en vous connectant à la [!INCLUDE[ssSDS](../includes/sssds-md.md)] à l'aide d'un outil de requête comme [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] en tant qu'utilisateur de base de données avec l'autorisation **AFFICHER L'ÉTAT DE LA BASE DE DONNÉES** . Requête la `encryption_state` colonne de la [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)vue.  
  
#### <a name="to-disable-tde-by-using-transact-sql"></a>Pour désactiver TDE en utilisant Transact-SQL  
  
1.  Connectez-vous à la base de données en utilisant une connexion correspondant à un administrateur ou à un membre du rôle **dbmanager** dans la base de données master.  
  
2.  Exécutez les instructions suivantes pour déchiffrer la base de données.  
  
    ```  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;  
    GO  
    ```  
  
3.  Pour surveiller la progression du chiffrement sur [!INCLUDE[ssSDS](../includes/sssds-md.md)], les utilisateurs disposant de la base de données le **VIEW DATABASE STATE** autorisation peut interroger le `encryption_state` colonne de la [sys.dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) vue.  
  
##  <a name="Working"></a> Utilisation de chiffrement transparent des données des bases de données protégées sur [!INCLUDE[ssSDS](../includes/sssds-md.md)]  
 Il n'est pas nécessaire de déchiffrer les bases de données pour effectuer des opérations dans Azure. La base de données cible hérite de façon transparente des paramètres de TDE sur la base de données source ou sur la base de données principale. Cela inclut les opérations impliquant :  
  
-   La géo-restauration  
  
-   La restauration à un moment donné en libre-service  
  
-   La restauration d'une base de données supprimée  
  
-   La géo-réplication active  
  
-   La création d'une copie de base de données  
  
##  <a name="Moving"></a> Passer une base de données protégé par chiffrement transparent des données à l’aide. Fichiers Bacpac  
 Lorsque l’exportation d’une chiffrement transparent des données protégée de la base de données à l’aide de la fonction d’exporter la base de données dans le [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] portail ou le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Assistant Importation et exportation, le contenu de la base de données n’est pas chiffré. Le contenu est stocké dans des fichiers .bacpac qui ne sont pas chiffrés.  Veillez à protéger les fichiers .bacpac de façon appropriée et à activer le TDE une fois l'importation de la base de données terminée.  
  
## <a name="related-sql-server-topic"></a>Rubrique SQL Server connexes  
 [Activer le chiffrement transparent des données à l’aide de la gestion de clés extensible (EKM)](../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Chiffrement transparent des données &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)   
 [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
