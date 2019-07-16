---
title: sp_validatelogins (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_validatelogins
- sp_validatelogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_validatelogins
ms.assetid: 6ac52e21-e20d-469b-ad40-5aa091e06b61
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: bd29100f8f7c54906b8aeafa98a7cf67f526db8b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68021050"
---
# <a name="spvalidatelogins-transact-sql"></a>sp_validatelogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet de signaler des informations sur les utilisateurs et les groupes Windows qui sont mappés sur des principaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais qui n'existent plus dans l'environnement Windows.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_validatelogins  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**SID**|**varbinary(85)**|Identificateur de sécurité de l'utilisateur ou groupe Windows.|  
|**Connexion NT**|**sysname**|Nom de l’utilisateur de Windows ou d’un groupe.|  
  
## <a name="remarks"></a>Notes  
 Si le principal orphelin au niveau serveur possède un utilisateur de base de données, celui-ci doit être supprimé pour que le principal de serveur orphelin puisse être supprimé. Pour supprimer un utilisateur de base de données, utilisez [DROP USER](../../t-sql/statements/drop-user-transact-sql.md). Si le principal au niveau serveur possède des éléments sécurisables dans la base de données, la propriété des éléments sécurisables doit être transférée ou ils doivent être supprimés. Pour transférer la propriété des éléments sécurisables de base de données, utilisez [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
 Pour supprimer des mappages aux utilisateurs de Windows et les groupes qui n’existent plus, utilisez [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance dans le **sysadmin** ou **securityadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple ci-dessous, les utilisateurs et les groupes Windows qui n'existent plus mais qui bénéficient toujours d'un accès à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont affichés.  
  
```  
EXEC sp_validatelogins;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP USER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [DROP LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
