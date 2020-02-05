---
title: DATABASE_PRINCIPAL_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATABASE_PRINCIPAL_ID_TSQL
- DATABASE_PRINCIPAL_ID
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], principals
- principal ID numbers [SQL Server]
- DATABASE_PRINCIPAL_ID function
- IDs [SQL Server], principals
ms.assetid: 908c7dd8-c10b-4658-92f6-0224f9835dd9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0fa5615d70542373030e0344d6988d9d2d0a028c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68026259"
---
# <a name="database_principal_id-transact-sql"></a>DATABASE_PRINCIPAL_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

Cette fonction retourne le numéro d’ID d’un principal de la base de données active. Pour plus d’informations sur les principaux, consultez [Principaux &#40;Moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md).
  
![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATABASE_PRINCIPAL_ID ( 'principal_name' )  
```  
  
## <a name="arguments"></a>Arguments  
*principal_name*  
Expression de type **sysname** qui représente le principal. Quand *principal_name* est omis, `DATABASE_PRINCIPAL_ID` retourne l’ID de l’utilisateur actif. `DATABASE_PRINCIPAL_ID` nécessite les parenthèses.
  
## <a name="return-types"></a>Types de retour
**int**  
NULL si le principal de la base de données n’existe pas.
  
## <a name="remarks"></a>Notes  
Utilisez `DATABASE_PRINCIPAL_ID` dans une liste de sélection, une clause WHERE ou n’importe quel emplacement qui autorise une expression. Pour plus d’informations, consultez [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="examples"></a>Exemples  
  
### <a name="a-retrieving-the-id-of-the-current-user"></a>R. Extraction de l'ID de l'utilisateur actuel  
Cet exemple retourne l’ID de principal de base de données de l’utilisateur actif.
  
```sql
SELECT DATABASE_PRINCIPAL_ID();  
GO  
```  
  
### <a name="b-retrieving-the-id-of-a-specified-database-principal"></a>B. Extraction de l'ID d'un principal de base de données spécifique  
Cet exemple retourne l’ID de principal de base de données du rôle de base de données `db_owner`.
  
```sql
SELECT DATABASE_PRINCIPAL_ID('db_owner');  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
[Hiérarchie des autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
[sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)
  
  
