---
title: DATABASE_PRINCIPAL_ID (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_PRINCIPAL_ID_TSQL
- DATABASE_PRINCIPAL_ID
dev_langs: TSQL
helpviewer_keywords:
- identification numbers [SQL Server], principals
- principal ID numbers [SQL Server]
- DATABASE_PRINCIPAL_ID function
- IDs [SQL Server], principals
ms.assetid: 908c7dd8-c10b-4658-92f6-0224f9835dd9
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 44f4bd65c93fc0c6ed0fd069946fabaedd1e0943
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="databaseprincipalid-transact-sql"></a>DATABASE_PRINCIPAL_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne le numéro d'ID d'un principal dans la base de données active. Pour plus d’informations sur les principaux, consultez [principaux &#40; moteur de base de données &#41;](../../relational-databases/security/authentication-access/principals-database-engine.md).
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATABASE_PRINCIPAL_ID ( 'principal_name' )  
```  
  
## <a name="arguments"></a>Arguments  
*principal_name*  
Est une expression de type **sysname** qui représente le principal.  
Lorsque *principal_name* est omis, l’ID de l’utilisateur actuel est retourné. Les parenthèses sont obligatoires.
  
## <a name="return-types"></a>Types de retour
**int**  
NULL lorsque le principal de la base de données n'existe pas
  
## <a name="remarks"></a>Notes  
DATABASE_PRINCIPAL_ID peut être utilisé dans une liste de sélection, une clause WHERE ou partout où une expression est autorisée. Pour plus d’informations, consultez [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="examples"></a>Exemples  
  
### <a name="a-retrieving-the-id-of-the-current-user"></a>A. Extraction de l'ID de l'utilisateur actuel  
L'exemple suivant retourne l'ID de principal de base de données de l'utilisateur actuel.
  
```sql
SELECT DATABASE_PRINCIPAL_ID();  
GO  
```  
  
### <a name="b-retrieving-the-id-of-a-specified-database-principal"></a>B. Extraction de l'ID d'un principal de base de données spécifique  
L'exemple suivant retourne l'ID de principal de base de données du rôle de base de données `db_owner`.
  
```sql
SELECT DATABASE_PRINCIPAL_ID('db_owner');  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
[Hiérarchie des autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
[sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)
  
  
