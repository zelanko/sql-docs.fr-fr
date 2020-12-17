---
title: Base de données de tutoriels pour RevoScaleR
description: Créez une base de données SQL Server et définissez les autorisations nécessaires pour suivre les autres tutoriels R.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: ae05adf9876b572bd01c9b7f239ef8aa08e67337
ms.sourcegitcommit: 3bd188e652102f3703812af53ba877cce94b44a9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97489969"
---
# <a name="create-a-database-and-permissions-sql-server-and-revoscaler-tutorial"></a>Créer une base de données et des autorisations (tutoriel SQL Server et RevoScaleR)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Il s’agit du tutoriel 1 de la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Ce tutoriel décrit comment créer une base de données SQL Server et définir les autorisations nécessaires pour suivre les autres tutoriels de cette série. Utilisez [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) ou un autre éditeur de requête pour effectuer les tâches suivantes :

> [!div class="checklist"]
> * Créer une base de données pour stocker les données de formation et d’évaluation de deux modèles R
> * Créer une connexion d’utilisateur de base de données avec des autorisations pour créer et utiliser des objets de base de données
  
## <a name="create-the-database"></a>Création de la base de données

Ce tutoriel nécessite une base de données pour le stockage des données et du code. Si vous n’êtes pas administrateur, demandez à votre administrateur de base de données de créer la base de données et la connexion pour vous. Vous aurez besoin d’autorisations pour écrire et lire des données, et pour exécuter des scripts R.

1. Dans SQL Server Management Studio, connectez-vous à une instance de base de données compatible avec R.

2. Cliquez avec le bouton droit sur **Bases de données** et sélectionnez **Nouvelles bases de données**.
  
2. Tapez un nom pour la nouvelle base de données : RevoDeepDive.
  
## <a name="create-a-login"></a>Créer un compte de connexion
  
1. Cliquez sur **Nouvelle requête**, et définissez le contexte de base de données sur la base de données master.
  
2. Dans la fenêtre **Nouvelle requête** , exécutez les commandes suivantes pour créer les comptes d’utilisateurs et les assigner à la base de données utilisée pour ce didacticiel. Le cas échéant, modifiez le nom de la base de données.

3. Pour vérifier la connexion, sélectionnez la nouvelle base de données, développez **Sécurité**, puis développez **Utilisateurs**.
  
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

Ce tutoriel présente les opérations DDL et script R, notamment la création et la suppression de tables et de procédures stockées, ainsi que l’exécution de script R dans un processus externe sur SQL Server. Dans cette étape, affectez des autorisations pour autoriser ces tâches.

Cet exemple suppose une connexion SQL (DDUser01), mais si vous avez créé une connexion Windows, utilisez-la à la place.

```sql
USE RevoDeepDive
GO

EXEC sp_addrolemember 'db_owner', 'DDUser01'
GRANT EXECUTE ANY EXTERNAL SCRIPT TO DDUser01
GO
```

## <a name="troubleshoot-connections"></a>Résoudre les problèmes de connexion

Cette section répertorie quelques problèmes courants que vous pouvez rencontrer au cours de la configuration de la base de données.

- **Comment puis-je vérifier la connectivité de la base de données et vérifier les requêtes SQL ?**
  
    Avant d’exécuter le code R à l’aide du serveur, vous voudrez peut-être vérifier que la base de données est accessible à partir de votre environnement de développement R. L’ [Explorateur de serveurs de Visual Studio](/previous-versions/x603htbk(v=vs.140)) et [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) sont des outils gratuits qui ont une connectivité de base de données et des fonctionnalités de gestion puissantes.
  
    Si vous ne souhaitez pas installer des outils de gestion de base de données supplémentaires, vous pouvez créer une connexion de test à l’instance de SQL Server à l’aide de [l’Administrateur de sources de données ODBC](../../odbc/admin/odbc-data-source-administrator.md) dans le Panneau de configuration. Si la base de données est correctement configurée et que vous entrez les nom d’utilisateur et mot de passe corrects, vous devriez pouvoir voir la base de données que vous venez de créer et la sélectionner comme base de données par défaut.
  
    Les causes courantes d’échecs de connexion incluent les connexions à distance qui ne sont pas activées pour le serveur, et le protocole de canaux nommés qui n’est pas activé. Vous trouverez d’autres conseils de résolution dans cet article : [Résoudre les problèmes de connexion au moteur de base de données SQL Server](../../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).
  
- **Pourquoi le nom de ma table est-il précédé de « datareader » ?**
  
    Quand vous spécifiez le schéma par défaut pour cet utilisateur en tant que **db_datareader**, toutes les tables et autres objets créés par cet utilisateur sont précédés du nom du *schéma*. Un schéma ressemble à un dossier que vous pouvez ajouter à une base de données pour organiser des objets. Le schéma définit également les privilèges d’un utilisateur dans la base de données.
  
    Quand le schéma est associé à un nom d’utilisateur, l’utilisateur est appelé le _propriétaire du schéma_. Quand vous créez un objet, vous le créez toujours dans votre propre schéma, sauf si vous demandez spécifiquement qu’il soit créé dans un autre schéma.
  
    Par exemple, si vous créez une table avec le nom **TestData** et que votre schéma par défaut est **db_datareader**, la table est créée avec le nom `<database_name>.db_datareader.TestData`.
  
    Pour cette raison, une base de données peut contenir plusieurs tables portant le même nom, tant que les tables appartiennent à des schémas différents.
   
    Si vous recherchez une table et que vous ne spécifiez pas de schéma, le serveur de base de données recherche un schéma dont vous êtes propriétaire. Ainsi, vous n’avez pas besoin de spécifier le nom de schéma pour accéder à des tables dans un schéma associé à votre compte de connexion.
  
- **Je ne dispose pas de privilèges DDL. Puis-je quand même suivre le didacticiel ?**
  
    Oui, mais vous devez demander à quelqu’un de précharger les données dans les tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et passer directement au tutoriel suivant. Les fonctions qui nécessitent des privilèges DDL sont généralement appelées en dehors du tutoriel.

    En outre, demandez à votre administrateur de vous accorder l’autorisation,EXECUTE ANY EXTERNAL SCRIPT. Elle est nécessaire pour l’exécution de script R, à distance ou à l’aide de `sp_execute_external_script`.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Créer des objets de données SQL Server à l’aide de RxSqlServerData](../../machine-learning/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
