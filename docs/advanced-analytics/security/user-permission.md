---
title: Autoriser les utilisateurs à SQL Server Machine Learning Services | Microsoft Docs
description: Comment autoriser les utilisateurs à SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 07268386ad66350eed7f1382348fa4d698863600
ms.sourcegitcommit: 13d98701ecd681f0bce9ca5c6456e593dfd1c471
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49419064"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>Autoriser les utilisateurs à SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment vous pouvez autoriser les utilisateurs à exécuter des scripts externes dans SQL Server Machine Learning Services et donner des autorisations language (DDL) aux bases de données en lecture, écriture ou définition de données.

Pour plus d’informations, consultez la section autorisations dans [vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité](../../advanced-analytics/concepts/security.md#permissions).

<a name="permissions-external-script"></a>

## <a name="permission-to-run-scripts"></a>Autorisation d’exécuter des scripts

Si vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous-même et que vous exécutez des scripts R ou Python dans votre propre instance, en général, vous exécutez les scripts en tant qu’administrateur. Par conséquent, vous avez une autorisation implicite sur différentes opérations et toutes les données dans la base de données.

La plupart des utilisateurs, toutefois, n’ont pas de ces autorisations élevées. Par exemple, les utilisateurs d’une organisation qui utilisent des connexions SQL pour accéder à la base de données généralement n’ont pas des autorisations élevées. Par conséquent, pour chaque utilisateur qui est à l’aide de R ou Python, vous devez accorder aux utilisateurs des Services Machine Learning l’autorisation d’exécuter des scripts externes dans chaque base de données où la langue est utilisée. Voici comment :

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT TO [UserName]
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