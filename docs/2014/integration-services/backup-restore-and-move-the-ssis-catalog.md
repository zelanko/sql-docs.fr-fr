---
title: Sauvegarder, restaurer et déplacer le catalogue SSIS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bf806aef-8556-48ab-aed5-e95de9a2204e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 66cbc5b8b54ec2507bb4fbe96443afa25386de96
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68670507"
---
# <a name="backup-restore-and-move-the-ssis-catalog"></a>Sauvegarder, restaurer et déplacer le catalogue SSIS
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] comprend la base de données SSISDB. Interrogez les vues de la base de données SSISDB pour inspecter les objets, les paramètres et les données opérationnelles stockés dans le catalogue **SSISDB** . Cette rubrique fournit des instructions sur la sauvegarde et la restauration de la base de données.  
  
 Le catalogue **SSISDB** stocke les packages que vous avez déployés sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Pour plus d’informations sur le catalogue, consultez [Catalogue SSIS](catalog/ssis-catalog.md).  
  
##  <a name="to-back-up-the-ssis-database"></a><a name="backup"></a>Pour sauvegarder la base de données SSIS  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
2.  Sauvegardez la clé principale de la base de données SSISDB, à l'aide de l'instruction Transact-SQL BACKUP MASTER KEY. La clé est stockée dans un fichier que vous spécifiez. Utilisez un mot de passe pour chiffrer la clé principale dans le fichier.  
  
     Pour plus d’informations sur l’instruction, consultez [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).  
  
     Dans l’exemple suivant, la clé principale est exportée vers le fichier `c:\temp directory\RCTestInstKey` . Le mot de passe `LS2Setup!` est utilisé pour chiffrer la clé principale.  
  
    ```  
    backup master key to file = 'c:\temp\RCTestInstKey'  
           encryption by password = 'LS2Setup!'  
  
    ```  
  
3.  Sauvegardez la base de données SSISDB à l’aide de la boîte de dialogue **Sauvegarder la base de données** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Procédure : sauvegarder une base de données (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=231812).  
  
4.  Générez le script CREATE LOGIN pour ##MS_SSISServerCleanupJobLogin## en procédant comme suit. Pour plus d’informations, consultez [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).  
  
    1.  Dans l’Explorateur d’objets de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], développez le nœud **Sécurité** , puis le nœud **Connexions** .  
  
    2.  Cliquez avec le bouton droit sur **##MS_SSISServerCleanupJobLogin##**, puis cliquez sur **Générer un script de la connexion en tant que** > **CREATE To** > **Nouvelle fenêtre d’éditeur de requête**.  
  
5.  Si vous devez restaurer la base de données SSISDB sur une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] où le catalogue SSISDB n’a jamais été créé, générez le script CREATE PROCEDURE pour sp_ssis_startup en effectuant les opérations suivantes. Pour plus d’informations, consultez [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).  
  
    1.  Dans l’Explorateur d’objets, développez le nœud **bases de données** , puis développez le nœud **bases de données système de** > la**programmabilité** > **principale** > **procédures stockées** .  
  
    2.  Cliquez avec le bouton droit sur **dbo.sp_ssis_startup**, puis cliquez sur **Générer un script de la procédure stockée en tant que** > **CREATE To** > **Nouvelle fenêtre d’éditeur de requête**.  
  
6.  Assurez-vous que Le SQL Server Agent a démarré.  
  
7.  Si vous devez restaurer la base de données SSISDB sur une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] où le catalogue SSISDB n’a jamais été créé, générez un script pour la tâche de maintenance de serveur SSIS en effectuant les opérations suivantes. Le script est créé automatiquement dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent quand le catalogue SSISDB est créé. Le travail permet de nettoyer les journaux d'opérations de nettoyage en dehors de la période de conservation et de supprimer les versions antérieures des projets.  
  
    1.  Dans l’Explorateur d’objets, développez le nœud **SQL Server Agent** , puis le nœud **Travaux** .  
  
    2.  Cliquez avec le bouton droit sur travail de maintenance du serveur SSIS, puis cliquez sur créer un **travail** > **de** > script dans une**nouvelle fenêtre**de l’éditeur de requête.  
  
### <a name="to-restore-the-ssis-database"></a>Pour restaurer la base de données SSIS  
  
1.  Si vous restaurez la base de données SSISDB sur une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] où le catalogue SSISDB n'a jamais été créé, activez le CLR en exécutant la procédure stockée sp_configure. Pour plus d’informations, consultez [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) et [clr enabled (option de configuration de serveur)](https://go.microsoft.com/fwlink/?LinkId=231855).  
  
    ```  
    use master   
           sp_configure 'clr enabled', 1  
           reconfigure  
  
    ```  
  
2.  Vous restaurez la base de données SSISDB sur une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] où le catalogue SSISDB n'a jamais été créé, créez la clé asymétrique et la connexion à partir de la clé asymétrique et accordez l'autorisation UNSAFE à la connexion.  
  
    ```  
    Create Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey  
           FROM Executable File = 'C:\Program Files\Microsoft SQL Server\110\DTS\Binn\Microsoft.SqlServer.IntegrationServices.Server.dll'  
  
    ```  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Les procédures stockées CLR exigent l’octroi d’autorisations UNSAFE à la connexion, car cette dernière nécessite un accès supplémentaire aux ressources restreintes, par exemple l’API Win32 de Microsoft. Pour plus d’informations sur l’autorisation de code UNSAFE, consultez [Création d’un assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md).  
  
    ```  
    Create Login MS_SQLEnableSystemAssemblyLoadingUser  
           FROM Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey   
  
           Grant unsafe Assembly to MS_SQLEnableSystemAssemblyLoadingUser  
  
    ```  
  
3.  Restaurez la base de données SSISDB à partir de la sauvegarde, à l’aide de la boîte de dialogue **Restaurer la base de données** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, voir les rubriques suivantes :  
  
    -   [Restaurer la base de données &#40;page Général&#41;](general-page-of-integration-services-designers-options.md)  
  
    -   [Restaurer la base de données &#40;page Fichiers&#41;](../relational-databases/backup-restore/restore-database-files-page.md)  
  
    -   [Restaurer la base de données &#40;page Options&#41;](../relational-databases/backup-restore/restore-database-options-page.md)  
  
4.  Exécutez les scripts que vous avez créés dans la procédure [Pour sauvegarder la base de données SSIS](#backup) pour ##MS_SSISServerCleanupJobLogin##, sp_ssis_startup et le travail de maintenance de serveur SSIS. Assurez-vous que SQL Server Agent a démarré.  
  
5.  Exécutez l'instruction suivante afin de définir la procédure sp_ssis_startup pour l'exécution automatique. Pour plus d’informations, consultez [sp_procoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql).  
  
    ```  
    EXEC sp_procoption N'sp_ssis_startup','startup','on'  
    ```  
  
6.  Mappez l’utilisateur SSISDB ##MS_SSISServerCleanupJobUser## (base de données SSISDB) à ##MS_SSISServerCleanupJobLogin##, à l’aide de la boîte de dialogue **Propriétés de la connexion** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
7.  Restaurez la clé principale à l'aide de l'une des méthodes suivantes. Pour plus d’informations sur le chiffrement, consultez [Hiérarchie de chiffrement](../relational-databases/security/encryption/encryption-hierarchy.md).  
  
    -   **Méthode 1**  
  
         Utilisez cette méthode si vous avez déjà effectué une sauvegarde de la clé principale de base de données et si vous disposez du mot de passe de chiffrement de la clé principale.  
  
        ```  
               Restore master key from file = 'c:\temp\RCTestInstKey'  
               Decryption by password = 'LS2Setup!' -- 'Password used to encrypt the master key during SSISDB backup'  
               Encryption by password = 'LS3Setup!' -- 'New Password'  
               Force  
  
        ```  
  
        > [!NOTE]  
        >  Assurez-vous que le compte de service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dispose des autorisations nécessaires pour lire le fichier de clé de sauvegarde.  
  
        > [!NOTE]  
        >  Le message d’avertissement suivant s’affiche dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] si la clé principale de base de données n’a pas encore été chiffrée par la clé principale du service. Ignorez le message d'avertissement.  
        >   
        >  **Impossible de déchiffrer la clé principale active. L’erreur a été ignorée parce que l’option FORCE a été spécifiée.**  
        >   
        >  L'argument FORCE spécifie que le processus de restauration doit continuer même si la clé principale de base de données actuelle n'est pas ouverte. Pour le catalogue SSISDB, comme la clé principale de base de données n'a pas été ouverte sur l'instance où vous restaurez la base de données, vous voyez s'afficher ce message.  
  
    -   **Méthode 2**  
  
         Utilisez cette méthode si vous disposez du mot de passe d'origine utilisé pour créer SSISDB.  
  
        ```  
        open master key decryption by password = 'LS1Setup!' --'Password used when creating SSISDB'  
               Alter Master Key Add encryption by Service Master Key  
        ```  
  
8.  Déterminez si le schéma de catalogue SSISDB et les binaires [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (assembly SQLCLR et ISServerExec) sont compatibles en exécutant [catalog.check_schema_version](/sql/integration-services/system-stored-procedures/catalog-check-schema-version).  
  
9. Pour vérifier que la base de données SSISDB a été restaurée correctement, effectuez des opérations sur le catalogue SSISDB, par exemple exécutez des packages déployés sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Pour plus d’informations, consultez [Exécuter un package sur le serveur SSIS à l’aide de SQL Server Management Studio](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md).  
  
### <a name="to-move-the-ssis-database"></a>Pour déplacer la base de données SSIS  
  
-   Suivez les instructions pour déplacer les bases de données utilisateur. Pour plus d’informations, consultez [Déplacer des bases de données utilisateur](../relational-databases/databases/move-user-databases.md).  
  
     Veillez à sauvegarder la clé principale de la base de données SSISDB et à protéger le fichier de sauvegarde. Pour plus d’informations, consultez [Pour sauvegarder la base de données SSIS](#backup).  
  
     Vérifiez que les objets Integration Services (SSIS) appropriés sont créés dans la nouvelle instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] où le catalogue SSISDB n’a pas encore été créé.  
  
  
