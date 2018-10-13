---
title: Autoriser les utilisateurs à SQL Server Machine Learning Services | Microsoft Docs
description: Comment autoriser les utilisateurs à SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/05/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: ad5c3fa3bf94bb88041c9ec81773b2a26013e517
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100330"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>Autoriser les utilisateurs à SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment vous pouvez autoriser les utilisateurs à exécuter des scripts externes dans SQL Server Machine Learning Services et donner des autorisations language (DDL) aux bases de données en lecture, écriture ou définition de données.

Une connexion SQL Server ou compte d’utilisateur Windows est requis pour exécuter des scripts externes qui utilisent des données SQL Server ou qui s’exécutent avec SQL Server comme contexte de calcul.

Le compte d’utilisateur ou de connexion identifie le *principal de sécurité*, qui peut ont besoin de plusieurs niveaux d’accès, selon les besoins de script externe :

+ Autorisation d’accéder à la base de données où les scripts externes sont activés.
+ Autorisations pour lire les données d’objets sécurisés tels que des tables.
+ La capacité d’écrire de nouvelles données à une table, comme un modèle ou de score des résultats.
+ La possibilité de créer de nouveaux objets, tels que des tables, des procédures stockées qui utilisent le script externe, ou les fonctions personnalisées qui utilisent R ou un travail Python.
+ Le droit d’installer de nouveaux packages sur l’ordinateur SQL Server, ou utiliser des packages fournis à un groupe d’utilisateurs.

Par conséquent, chaque personne qui exécute un script externe à l’aide de SQL Server en tant que le contexte d’exécution doit être mappé à un utilisateur dans la base de données. Sous la sécurité de SQL Server, il est plus facile de créer des rôles pour gérer des ensembles d’autorisations et affecter des utilisateurs à ces rôles, au lieu de définir individuellement les autorisations utilisateur.

Si l’utilisateur a besoin pour exécuter un script externe en base de données, ou les objets de base de données access et les données, même les utilisateurs qui sont à l’aide de R ou Python dans un outil externe doivent être mappés à un compte dans la base de données ou de connexion. Les mêmes autorisations sont nécessaires si le script externe est envoyé à partir d’un client de science des données distantes ou démarré à l’aide d’une procédure stockée T-SQL.

Par exemple, supposons que vous avez créé un script externe qui s’exécute sur votre ordinateur local, et que vous souhaitez exécuter ce code sur SQL Server. Vous devez veiller à ce que les conditions suivantes soient réunies :

+ La base de données autorise les connexions à distance.
+ La connexion SQL ou un compte Windows que vous avez utilisé pour l’accès de base de données a été ajoutée à SQL Server au niveau de l’instance.
+ Le compte de connexion SQL ou l’utilisateur de Windows doit avoir l’autorisation d’exécuter des scripts externes. En règle générale, cette autorisation ne peut être ajoutée que par un administrateur de base de données.
+ La connexion SQL ou l’utilisateur Windows doit être ajouté en tant qu’utilisateur, avec les autorisations appropriées, dans chaque base de données où le script externe effectue l’une de ces opérations :
  + Récupération de données.
  + Écriture ou la mise à jour des données.
  + Création d’objets, tels que des tables ou des procédures stockées.

Une fois la connexion ou un compte d’utilisateur Windows a été mis en service et les autorisations nécessaires, vous pouvez exécuter un script externe sur SQL Server à l’aide d’un objet de source de données dans R ou **revoscalepy** bibliothèque dans Python, ou en appelant un stockée procédure qui contient le script externe.

Chaque fois qu’un script externe est lancé à partir de SQL Server, la sécurité du moteur de base de données obtient le contexte de sécurité de l’utilisateur qui a démarré la tâche et gère les mappages de l’utilisateur ou d’une connexion à des objets sécurisables.

Par conséquent, tous les scripts externes qui sont lancées à partir d’un client distant doivent spécifier les informations de connexion ou un utilisateur dans le cadre de la chaîne de connexion.

<a name="permissions-external-script"></a> 

## <a name="permission-to-run-scripts"></a>Autorisation d’exécuter des scripts

Si vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous-même et que vous exécutez des scripts R ou Python dans votre propre instance, en général, vous exécutez les scripts en tant qu’administrateur. Par conséquent, vous avez une autorisation implicite sur différentes opérations et toutes les données dans la base de données.

La plupart des utilisateurs, toutefois, n’ont pas de ces autorisations élevées. Par exemple, les utilisateurs d’une organisation qui utilisent des connexions SQL pour accéder à la base de données généralement n’ont pas des autorisations élevées. Par conséquent, pour chaque utilisateur qui est à l’aide de R ou Python, vous devez accorder aux utilisateurs des Services Machine Learning l’autorisation d’exécuter des scripts externes dans chaque base de données où la langue est utilisée. Voici comment :

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> Autorisations ne sont pas spécifiques au langage de script pris en charge. En d’autres termes, il ne sont pas des niveaux d’autorisation distincts pour le script R et le script Python. Si vous avez besoin de mettre à jour les autorisations distinctes pour ces langues, vous devez installer R et Python sur des instances distinctes.

<a name="permissions-db"></a> 

## <a name="grant-databases-permissions"></a>Accorder des autorisations de bases de données

Pendant l’exécution de scripts est un utilisateur, l’utilisateur devra peut-être lire les données à partir d’autres bases de données. L’utilisateur peut également besoin créer des tables pour stocker les résultats et écrire des données dans des tables.

Pour chaque compte d’utilisateur Windows ou un compte de connexion SQL qui est en cours d’exécution des scripts R ou Python, vérifiez qu’il possède les autorisations appropriées sur la base de données : `db_datareader` pour lire les données, `db_datawriter` pour enregistrer les objets à la base de données, ou `db_ddladmin` pour créer des objets tels que des procédures stockées ou des tables contenant formé et des données sérialisées.

Par exemple, ce qui suit [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction donne la connexion SQL *MySQLLogin* les droits pour exécuter des requêtes T-SQL le *ML_Samples* base de données. Pour exécuter cette instruction, la connexion SQL doit déjà exister dans le contexte de sécurité du serveur.

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autorisations incluses dans chaque rôle, consultez [rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md).