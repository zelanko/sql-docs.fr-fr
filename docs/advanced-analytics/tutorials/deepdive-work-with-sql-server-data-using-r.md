---
title: Créer une base de données et des autorisations pour les didacticiels de RevoScaleR - SQL Server Machine Learning
description: Didacticiel pas à pas sur la création d’une base de données SQL Server pour les didacticiels R...
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 84f78219bf4bb188f7a29e79718e107d7fa43347
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962169"
---
# <a name="create-a-database-and-permissions-sql-server-and-revoscaler-tutorial"></a>Créer une base de données et des autorisations (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie de la [RevoScaleR didacticiel](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Leçon 1 est sur la configuration d’une base de données SQL Server et les autorisations nécessaires pour suivre ce didacticiel. Utilisez [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) ou un autre éditeur de requête pour effectuer les tâches suivantes :

> [!div class="checklist"]
> * Créer une base de données pour stocker les données de formation et la notation des deux modèles R
> * Créez une connexion d’utilisateur de base de données avec des autorisations pour créer et utiliser des objets de base de données
  
## <a name="create-the-database"></a>Créer la base de données

Ce didacticiel requiert une base de données pour le stockage des données et le code. Si vous n’êtes pas un administrateur, demandez à votre administrateur pour créer la base de données et de la connexion pour vous. Vous aurez besoin des autorisations pour écrire et lire des données et à exécuter des scripts R.

1. Dans SQL Server Management Studio, connectez-vous à une instance de base de données prenant en charge de R.

2. Avec le bouton droit **bases de données**, puis sélectionnez **nouvelle base de données**.
  
2. Tapez un nom pour la nouvelle base de données : RevoDeepDive.
  

## <a name="create-a-login"></a>Créer un compte de connexion
  
1. Cliquez sur **Nouvelle requête**, et définissez le contexte de base de données sur la base de données master.
  
2. Dans la fenêtre **Nouvelle requête** , exécutez les commandes suivantes pour créer les comptes d’utilisateurs et les assigner à la base de données utilisée pour ce didacticiel. Le cas échéant, modifiez le nom de la base de données.

3. Pour vérifier la connexion, sélectionnez la nouvelle base de données, développez **sécurité**et développez **utilisateurs**.
  
**utilisateur Windows**
  
```sql
 -- Create server user based on Windows account
USE master
GO
CREATE LOGIN [<DOMAIN>\<user_name>] FROM WINDOWS WITH DEFAULT_DATABASE=[RevoDeepDive]

 --Add the new user to tutorial database
USE [RevoDeepDive]
GO
CREATE USER [<user_name>] FOR LOGIN [<DOMAIN>\<user_name>] WITH DEFAULT_SCHEMA=[db_datareader]
```

**Connexion SQL**

```sql
-- Create new SQL login
USE master
GO
CREATE LOGIN [DDUser01] WITH PASSWORD='<type password here>', CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF;

-- Add the new SQL login to tutorial database
USE RevoDeepDive
GO
CREATE USER [DDUser01] FOR LOGIN [DDUser01] WITH DEFAULT_SCHEMA=[db_datareader]
```

## <a name="assign-permissions"></a>Affecter des autorisations

Ce didacticiel montre le script R et les opérations DDL, notamment la création et suppression de tables et procédures stockées et en cours d’exécution de script R dans un processus externe sur SQL Server. Dans cette étape, affecter des autorisations pour permettre ces tâches.

Cet exemple suppose une connexion SQL (DDUser01), mais si vous avez créé un compte de connexion Windows, utilisez à la place.

```sql
USE RevoDeepDive
GO

EXEC sp_addrolemember 'db_owner', 'DDUser01'
GRANT EXECUTE ANY EXTERNAL SCRIPT TO DDUser01
GO
```

## <a name="troubleshoot-connections"></a>Résoudre les problèmes de connexions

Cette section répertorie quelques problèmes courants que vous pouvez rencontrer au cours de la configuration de la base de données.

- **Comment puis-je vérifier la connectivité de la base de données et vérifier les requêtes SQL ?**
  
    Avant d’exécuter le code R à l’aide du serveur, vous voudrez peut-être vérifier que la base de données est accessible à partir de votre environnement de développement R. L’ [Explorateur de serveurs de Visual Studio](https://docs.microsoft.com/previous-versions/x603htbk(v=vs.140)) et [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) sont des outils gratuits qui ont une connectivité de base de données et des fonctionnalités de gestion puissantes.
  
    Si vous ne souhaitez pas installer des outils de gestion de base de données supplémentaires, vous pouvez créer une connexion de test à l’instance de SQL Server à l’aide de [l’Administrateur de sources de données ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator?view=sql-server-2017) dans le Panneau de configuration. Si la base de données est correctement configurée et que vous entrez les nom d’utilisateur et mot de passe corrects, vous devriez pouvoir voir la base de données que vous venez de créer et la sélectionner comme base de données par défaut.
  
    Raisons courantes d’échecs de connexion des sites distants connexions ne sont pas activées pour le serveur et le protocole des canaux nommés n’est pas activé. Vous trouverez des conseils de dépannage plus dans cet article : [Résoudre les problèmes de connexion au moteur de base de données SQL Server](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine).
  
- **Pourquoi le nom de ma table est-il précédé de « datareader » ?**
  
    Lorsque vous spécifiez le schéma par défaut pour cet utilisateur en tant que **db_datareader**, toutes les tables et les autres nouveaux objets créés par cet utilisateur sont précédés de la *schéma* nom. Un schéma ressemble à un dossier que vous pouvez ajouter à une base de données pour organiser des objets. Le schéma définit également les privilèges d’un utilisateur dans la base de données.
  
    Lorsque le schéma est associé à un nom d’utilisateur particulier, l’utilisateur est le _propriétaire du schéma_. Quand vous créez un objet, vous le créez toujours dans votre propre schéma, sauf si vous demandez spécifiquement qu’il soit créé dans un autre schéma.
  
    Par exemple, si vous créez une table portant le nom **TestData**, et votre schéma par défaut est **db_datareader**, la table est créée avec le nom `<database_name>.db_datareader.TestData`.
  
    Pour cette raison, une base de données peut contenir plusieurs tables portant le même nom, tant que les tables appartiennent à des schémas différents.
   
    Si vous recherchez une table et que vous ne spécifiez pas de schéma, le serveur de base de données recherche un schéma dont vous êtes propriétaire. Ainsi, vous n’avez pas besoin de spécifier le nom de schéma pour accéder à des tables dans un schéma associé à votre compte de connexion.
  
- **Je ne dispose pas de privilèges DDL. Puis-je quand même suivre le didacticiel ?**
  
    Oui, mais vous devez demander à quelqu'un de précharger les données dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables, puis passez à l’avance à la leçon suivante. Les fonctions qui requièrent des privilèges DDL sont appelées dans le didacticiel dans la mesure du possible.

    En outre, demandez à votre administrateur de vous accorder l’autorisation EXECUTE ANY EXTERNAL SCRIPT. Il est nécessaire pour l’exécution du script R, si à distance ou à l’aide de `sp_execute_external_script`.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer des objets de données SQL Server à l’aide de RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)