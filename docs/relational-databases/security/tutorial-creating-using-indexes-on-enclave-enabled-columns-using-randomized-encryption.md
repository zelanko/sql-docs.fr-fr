---
title: 'Tutoriel : Créer et utiliser des index sur des colonnes prenant en charge les enclaves à l’aide d’un chiffrement aléatoire | Microsoft Docs'
ms.custom: ''
ms.date: 12/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 3f5d85128dd242b9499b31ad928a00a17d2b5571
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75258317"
---
# <a name="tutorial-create-and-use-indexes-on-enclave-enabled-columns-using-randomized-encryption"></a>Tutoriel : Créer et utiliser des index sur des colonnes prenant en charge les enclaves à l’aide d’un chiffrement aléatoire
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

Ce didacticiel vous apprend à créer et utiliser des index sur des colonnes prenant en charge les enclaves à l’aide de la prise en charge dans le chiffrement aléatoire [Always Encrypted avec enclaves sécurisées](encryption/always-encrypted-enclaves.md). Il vous montre comment :

- Comment créer un index lorsque vous avez accès aux clés (la clé principale de colonne et la clé de chiffrement de colonne) protection de la colonne.
- Comment créer un index lorsque vous n’avez pas accès aux clés de protection de la colonne.

## <a name="prerequisites"></a>Conditions préalables requises

Ce didacticiel est la continuation du [Didacticiel : Prise en main d’Always Encrypted avec enclaves sécurisées en utilisant SSMS](./tutorial-getting-started-with-always-encrypted-enclaves.md). Assurez-vous que vous avez terminé, avant de suivre les étapes ci-dessous.

## <a name="step-1-enable-accelerated-database-recovery-adr-in-your-database"></a>Étape 1 : Activer la récupération accélérée de la base de données (ADR) dans votre base de données

Microsoft recommande fortement d'activer ADR dans votre base de données avant de créer le premier index sur une colonne prenant en charge les enclaves à l’aide d’un chiffrement aléatoire. Consultez la section [Récupération de base de données](./encryption/always-encrypted-enclaves.md#database-recovery) dans [Always Encrypted avec enclaves sécurisées](./encryption/always-encrypted-enclaves.md).

1. Fermez toutes les instances de SSMS utilisées dans le didacticiel précédent. Ceci permet de fermer les connexions de base de données que vous avez ouvert, ce qui est nécessaire pour activer ADR.
1. Ouvrez une nouvelle instance de SSMS et connectez-vous à votre instance de SQL Server en tant que sysadmin **sans** Always Encrypted activé pour la connexion de base de données.
    1. Démarrer SSMS.
    1. Dans la boîte de dialogue **Se connecter au serveur**, spécifiez le nom de votre serveur, sélectionnez une méthode d’authentification et spécifiez vos informations d’identification.
    1. Cliquez sur **Options >>** et sélectionnez l’onglet **Always Encrypted**.
    1. Assurez-vous que la case **Activer Always Encrypted (chiffrement de colonne)** n’est **pas** cochée.
    1. Sélectionnez **Connecter**.
1. Ouvrez une nouvelle fenêtre de requête et exécutez l’instruction ci-dessous pour activer ADR.

   ```sql
   ALTER DATABASE ContosoHR SET ACCELERATED_DATABASE_RECOVERY = ON;
   ```

## <a name="step-2-create-and-test-an-index-without-role-separation"></a>Étape 2 : Créer et tester un index sans séparation des rôles

Dans cette étape, vous allez créer et tester un index sur une colonne chiffrée. Vous allez agir en tant qu’utilisateur unique qui assume les rôles de DBA, qui gère la base de données et de propriétaire des données qui a accès aux clés, en protection des données.

1. Ouvrez une nouvelle instance SSMS et connectez-vous à votre instance SQL Server **avec** Always Encrypted activé pour la connexion de base de données.
   1. Démarrez une nouvelle instance SSMS.
   1. Dans la boîte de dialogue **Se connecter au serveur**, spécifiez le nom de votre serveur, sélectionnez une méthode d’authentification et spécifiez vos informations d’identification.
   1. Cliquez sur **Options >>** et sélectionnez l’onglet **Always Encrypted**.
   1. Cochez la case **Activer Always Encrypted (chiffrement de colonne)** et spécifiez l’URL de votre attestation d’enclave (par exemple ht<span>tp://<   span>hgs.bastion.local/Attestation).
   1. Sélectionnez **Connecter**.
   1. S’il vous est demandé d’activer le paramétrage des requêtes Always Encrypted, cliquez sur **Activer**.
1. Si vous n’êtes pas invité à activer le Paramétrage pour Always Encrypted, vérifiez qu’il est activé.
   1. Sélectionnez **Outils** dans le menu principal de SSMS.
   2. Sélectionnez **Options...** .
   3. Accédez à **Exécution de la requête** > **SQL Server** > **Avancé**.
   4. Vérifiez que la case **Activer Paramétrage pour Always Encrypted** est cochée.
   5. Sélectionnez **OK**.
1. Ouvrez une fenêtre de requête et exécutez les instructions ci-dessous pour chiffrer la colonne **LastName** dans la table **Employés**. Vous allez créer et utiliser un index sur cette colonne dans les étapes suivantes.

   ```sql
   USE [ContosoHR];
   GO   
   ALTER TABLE [dbo].[Employees]
   ALTER COLUMN [LastName] [nvarchar](50) COLLATE Latin1_General_BIN2 
   ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized    ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL;
   GO   
   ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
   GO
   ```

1. Créez un index sur la colonne **LastName**. Étant donné que vous êtes connecté à la base de données avec Always Encrypted activé, le pilote du client à l’intérieur de SSMS fournit en toute transparence **CEK1** (la clé de chiffrement de colonne protégeant la colonne **LastName**) pour l’enclave, nécessaire pour créer l’index.

   ```sql
   USE [ContosoHR];
   GO

   CREATE INDEX IX_LastName ON [Employees] ([LastName])
   INCLUDE ([EmployeeID], [FirstName], [SSN], [Salary]);
   GO
   ```

1. Exécutez une requête enrichie sur la colonne **LastName** et vérifiez que SQL Server utilise l’index lors de l’exécution de la requête.
   1. Dans la même fenêtre de requête ou dans une nouvelle fenêtre de requête, assurez-vous que le bouton de la barre d’outils **Inclure les statistiques des requêtes actives** est activé.
   1. Exécutez la requête ci-dessous.

       ```sql
       USE [ContosoHR];
       GO

       DECLARE @LastNamePrefix NVARCHAR(50) = 'Aber%';
       SELECT * FROM [dbo].[Employees] WHERE [LastName] LIKE @LastNamePrefix;
       GO
      ```

   1. Dans l’onglet **Statistiques des requêtes actives** (dans la partie inférieure de la fenêtre de requête), observez que la requête utilise l’index.

## <a name="step-3-create-an-index-with-role-separation"></a>Étape 3 : Créer un index avec séparation des rôles

Dans cette étape, vous allez créer un index sur une colonne chiffrée, prétendant être deux utilisateurs différents. Un utilisateur est un DBA, qui doit créer un index, mais n’a pas accès aux clés. L’autre utilisateur est un propriétaire de données, qui a accès aux clés.

1. À l’aide de l’instance SSMS **sans** Always Encrypted activé, exécutez l’instruction ci-dessous pour déposer l’index sur la colonne **LastName**.

   ```sql
   USE [ContosoHR];
   GO

   DROP INDEX IX_LastName ON [Employees]; 
   GO
   ```

1. En agissant en tant que propriétaire de données (ou une application qui a accès aux clés), vous remplissez le cache à l’intérieur de l’enclave avec **CEK1**.

   > [!NOTE]
   > À moins d’avoir redémarré votre instance après **Étape 2 : Créer et tester un index sans séparation des rôles**, cette étape est redondante car le **CEK1** est déjà présent dans le cache. Nous l’avons ajouté pour démontrer comment un propriétaire de données peut fournir une clé à l’enclave, si elle n’est pas déjà présente dans l’enclave.

   1. Dans l’instance de SSMS **avec** Always Encrypted activé, exécutez les instructions suivantes dans une fenêtre de requête. L’instruction envoie toutes les clés de chiffrement de colonne prenant en charge les enclaves à l’enclave. Consultez [sp_enclave_send_keys](../system-stored-procedures/sp-enclave-send-keys-sql.md) pour plus d’informations.

        ```sql
        USE [ContosoHR];
        GO

        EXEC sp_enclave_send_keys;
        GO
        ```

   1. Comme alternative à l’exécution de la procédure stockée ci-dessus, vous pouvez exécuter une requête DML qui utilise l’enclave contre la colonne **LastName**. Cela remplira l’enclave uniquement avec **CEK1**.

        ```sql
        USE [ContosoHR];
        GO

        DECLARE @LastNamePrefix NVARCHAR(50) = 'Aber%';
        SELECT * FROM [dbo].[Employees] WHERE [LastName] LIKE @LastNamePrefix;
        GO
        ```

1. Agissant en tant que DBA, créez l’index.
    1. Dans l’instance de SSMS **sans** Always Encrypted activé, exécutez les instructions suivantes dans une fenêtre de requête.

        ```sql
        USE [ContosoHR];
        GO

        CREATE INDEX IX_LastName ON [Employees] ([LastName])
        INCLUDE ([EmployeeID], [FirstName], [SSN], [Salary]);
        GO
        ```

1. En tant que propriétaire des données, exécutez une requête enrichie sur la colonne **LastName** et vérifiez que SQL Server utilise l’index lors de l’exécution de la requête.
   1. Dans l’instance de SSMS **avec** Always Encrypted activé, sélectionnez une fenêtre de requête existante ou ouvrez une nouvelle fenêtre de requête et assurez-vous que le bouton de la barre d’outils **Inclure les statistiques des requêtes actives** est activé.
   1. Exécutez la requête ci-dessous. 

        ```sql
        USE [ContosoHR];
        GO

        DECLARE @LastNamePrefix NVARCHAR(50) = 'Aber%';
        SELECT * FROM [dbo].[Employees] WHERE [LastName] LIKE @LastNamePrefix;
        GO
        ```

   1. Dans **Statistiques des requêtes actives** (dans la partie inférieure de la fenêtre de requête), observez que la requête utilise l’index.

## <a name="next-steps"></a>Étapes suivantes
- [Tutoriel : Développer une application .NET Framework avec Always Encrypted avec enclaves sécurisées](tutorial-always-encrypted-enclaves-develop-net-framework-apps.md)

## <a name="see-also"></a>Voir aussi
- [Créer et utiliser des index sur des colonnes à l’aide d’Always Encrypted avec enclaves sécurisées](encryption/always-encrypted-enclaves-create-use-indexes.md)
