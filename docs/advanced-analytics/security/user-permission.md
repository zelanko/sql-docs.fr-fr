---
title: Accorder des autorisations pour des scripts
description: Décrit comment accorder des autorisations d’utilisateur de base de données pour l’exécution de scripts R et Python sur SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9b8d3ea5c52c5c18f09097322fdc1e1b2321494e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "73727308"
---
# <a name="give-users-permission-to-sql-server-machine-learning-services"></a>Accorder des autorisations utilisateur sur SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment autoriser les utilisateurs à exécuter des scripts externes dans SQL Server Machine Learning Services et comment accorder des autorisations de lecture, d’écriture ou de langage de définition de données (DDL) sur les bases de données.

Pour plus d’informations, consultez la section Autorisations dans la [vue d’ensemble de la sécurité du framework d’extensibilité](../../advanced-analytics/concepts/security.md#permissions).

<a name="permissions-external-script"></a>

## <a name="permission-to-run-scripts"></a>Autorisation d’exécuter des scripts

Si vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous-même et que vous exécutez des scripts R ou Python dans votre propre instance, vous exécutez généralement des scripts en tant qu’administrateur. Vous disposez ainsi d’autorisations implicites sur diverses opérations et sur toutes les données de la base de données.

Toutefois, la plupart des utilisateurs ne bénéficient pas de ces autorisations élevées. Par exemple, les utilisateurs d’une organisation qui utilisent des connexions SQL pour accéder à la base de données n’ont généralement pas d’autorisations élevées. Par conséquent, pour chaque utilisateur utilisant R ou Python, vous devez autoriser les utilisateurs de Machine Learning Services à exécuter des scripts externes dans chaque base de données où le langage est utilisé. Voici comment faire :

```sql
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT TO [UserName]
```

> [!NOTE]
> Les autorisations ne sont pas spécifiques au langage de script pris en charge. En d’autres termes, il n’existe pas de niveaux d’autorisation distincts pour les scripts R et Python. Si vous souhaitez maintenir des autorisations distinctes pour ces langages, installez R et Python sur des instances distinctes.

<a name="permissions-db"></a> 

## <a name="grant-databases-permissions"></a>Accorder des autorisations sur les bases de données

Quand un utilisateur exécute des scripts, il peut avoir besoin de lire les données d’autres bases de données. Il peut également être amené à créer des tables pour stocker les résultats et à écrire des données dans des tables.

Vérifiez que chaque compte d’utilisateur Windows ou connexion SQL exécutant des scripts R ou Python dispose des autorisations appropriées sur la base de données spécifique : `db_datareader` pour lire des données, `db_datawriter` pour enregistrer des objets dans la base de données ou `db_ddladmin` pour créer des objets tels que des procédures stockées ou des tables contenant des données entraînées et sérialisées.

Par exemple, l’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante donne à la connexion SQL *MySQLLogin* les droits nécessaires pour exécuter des requêtes T-SQL dans la base de données *ML_Samples*. Pour exécuter cette instruction, la connexion SQL doit déjà exister dans le contexte de sécurité du serveur.

```sql
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autorisations incluses dans chaque rôle, consultez [Rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md).