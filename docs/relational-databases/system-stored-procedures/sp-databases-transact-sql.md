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
ms.openlocfilehash: c338fb8057c2d58727f18e0bb69e2fa825e71559
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108335"
---
# <a name="sp_databases-transact-sql"></a>sp_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie les bases de données présentes dans une instance du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou accessibles via une passerelle de base de données.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_databases  
```  
  
## <a name="return-code-values"></a>Codet de retour  
 None  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**DATABASE_NAME**|**sysname**|Nom de la base de données. Dans [!INCLUDE[ssDE](../../includes/ssde-md.md)], cette colonne représente le nom de la base de données tel qu’il est stocké dans l’affichage catalogue **sys. databases** .|  
|**DATABASE_SIZE**|**int**|Taille de la base de données, exprimée en kilo-octets.|  
|**CONCERNANT**|**varchar (254)**|Pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)], ce champ retourne toujours la valeur null.|  
  
## <a name="remarks"></a>Notes  
 Les noms de bases de données qui sont renvoyés peuvent être utilisés comme paramètres dans l'instruction USE pour changer de contexte de base de données active.  
  
 **sp_databases** n’a pas d’équivalent dans Open Database Connectivity (ODBC).  
  
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
 [sys. databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [HAS_DBACCESS &#40;Transact-SQL&#41;](../../t-sql/functions/has-dbaccess-transact-sql.md)  
  
  
