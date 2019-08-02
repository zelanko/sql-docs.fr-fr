---
title: Accorder des autorisations de base de données pour l’exécution de scripts R et Python
description: Octroi d’autorisations d’utilisateur de base de données pour l’exécution de scripts R et Python sur SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 97e1fb6e2415e30f595d61dffa8a4952cfdc42d0
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715562"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>Accorder aux utilisateurs l’autorisation d’SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment permettre aux utilisateurs d’exécuter des scripts externes dans SQL Server Machine Learning Services et fournir des autorisations de lecture, d’écriture ou de langage de définition de données (DDL) aux bases de données.

Pour plus d’informations, consultez la section autorisations dans [vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité](../../advanced-analytics/concepts/security.md#permissions).

<a name="permissions-external-script"></a>

## <a name="permission-to-run-scripts"></a>Autorisation d’exécuter des scripts

Si vous vous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] êtes installé et que vous exécutez des scripts R ou python dans votre propre instance, vous exécutez généralement des scripts en tant qu’administrateur. Ainsi, vous disposez d’une autorisation implicite sur diverses opérations et sur toutes les données de la base de données.

Toutefois, la plupart des utilisateurs ne disposent pas de ces autorisations élevées. Par exemple, les utilisateurs d’une organisation qui utilisent des connexions SQL pour accéder à la base de données ne disposent généralement pas d’autorisations élevées. Par conséquent, pour chaque utilisateur qui utilise R ou python, vous devez accorder aux utilisateurs de Machine Learning Services l’autorisation d’exécuter des scripts externes dans chaque base de données où la langue est utilisée. Voici comment :

```sql
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT TO [UserName]
```

> [!NOTE]
> Les autorisations ne sont pas spécifiques au langage de script pris en charge. En d’autres termes, il n’existe pas de niveaux d’autorisation distincts pour les scripts R et Python. Si vous avez besoin de conserver des autorisations distinctes pour ces langues, installez R et Python sur des instances distinctes.

<a name="permissions-db"></a> 

## <a name="grant-databases-permissions"></a>Autorisations de base de données Grant

Lorsqu’un utilisateur exécute des scripts, il peut avoir besoin de lire des données d’autres bases de données. L’utilisateur peut également être amené à créer des tables pour stocker les résultats et à écrire des données dans des tables.

Pour chaque compte d’utilisateur Windows ou connexion SQL qui exécute des scripts R ou python, assurez-vous qu’il dispose des autorisations appropriées sur `db_datareader` la base de données `db_datawriter` spécifique: pour lire des données, pour `db_ddladmin` enregistrer des objets dans la base de données ou pour créer des objets tels que les procédures stockées ou les tables contenant des données formées et sérialisées.

Par exemple, l’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante donne à la connexion SQL *MySQLLogin* les droits d’exécuter des requêtes T-SQL dans la base de données *ML_Samples* . Pour exécuter cette instruction, la connexion SQL doit déjà exister dans le contexte de sécurité du serveur.

```sql
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autorisations incluses dans chaque rôle, consultez [rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md).