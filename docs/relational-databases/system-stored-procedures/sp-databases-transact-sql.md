---
title: sp_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_databases_TSQL
- sp_databases
dev_langs:
- TSQL
helpviewer_keywords:
- sp_databases
ms.assetid: 2a83b92a-9ecc-43c4-8ff4-e91e3a940b5a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1be4fbfb6ce30443a979fb500954e7aa8fa9779a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62507411"
---
# <a name="spdatabases-transact-sql"></a>sp_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie les bases de données présentes dans une instance du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou accessibles via une passerelle de base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_databases  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 None  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**DATABASE_NAME**|**sysname**|Nom de la base de données. Dans le [!INCLUDE[ssDE](../../includes/ssde-md.md)], cette colonne représente le nom de la base de données stockées dans le **sys.databases** vue de catalogue.|  
|**DATABASE_SIZE**|**Int**|Taille de la base de données, exprimée en kilo-octets.|  
|**REMARQUES**|**varchar(254)**|Pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)], ce champ retourne toujours NULL.|  
  
## <a name="remarks"></a>Notes  
 Les noms de bases de données qui sont renvoyés peuvent être utilisés comme paramètres dans l'instruction USE pour changer de contexte de base de données active.  
  
 **sp_databases** n’a aucun équivalent dans ODBC Open Database Connectivity ().  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation CREATE DATABASE, ALTER ANY DATABASE ou VIEW ANY DEFINITION et doit être autorisée à accéder à la base de données. L'autorisation VIEW ANY DEFINITION ne peut pas lui être refusée.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre l'exécution de `sp_databases`.  
  
```sql  
USE master;  
GO  
EXEC sp_databases;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [HAS_DBACCESS &#40;Transact-SQL&#41;](../../t-sql/functions/has-dbaccess-transact-sql.md)  
  
  
