---
title: sp_revokedbaccess (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revokedbaccess_TSQL
- sp_revokedbaccess
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokedbaccess
ms.assetid: c997cfa1-539d-485c-a664-9c6f76bfe0c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 5eea0129b76a7bb7825987da98be40ba4a66d6fb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67941716"
---
# <a name="sp_revokedbaccess-transact-sql"></a>sp_revokedbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un utilisateur de base de données de la base de données active.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez à la place [DROP USER](../../t-sql/statements/drop-user-transact-sql.md) .  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_revokedbaccess [ @name_in_db = ] 'name'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @name_in_db = ] 'name'`Nom de l’utilisateur de base de données à supprimer. *Name* est de **type sysname** et n’a pas de valeur par défaut. *nom* peut être le nom d’une connexion de serveur, d’une connexion Windows ou d’un groupe Windows, et doit exister dans la base de données actuelle. Lorsque vous spécifiez une connexion Windows ou un groupe Windows, spécifiez les noms sous lesquels ils sont connus dans la base de données.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Lorsque l'utilisateur de base de données est supprimé, les autorisations et les alias qui dépendent de cet utilisateur sont également supprimés.  
  
 **sp_revokedbaccess** pouvez supprimer uniquement les utilisateurs de base de données de la base de données active. Avant de supprimer un utilisateur de base de données qui possède des objets dans la base de données active, vous devez transférer la propriété des objets ou supprimer les objets de la base de données. Pour plus d’informations, consultez [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
 **sp_revokedbaccess** ne peut pas être exécutée dans une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation ALTER ANY USER sur la base de données.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant supprime l’utilisateur de base de données `Edmonds\LolanSo` mappé à à partir de la base de données active.  
  
```  
EXEC sp_revokedbaccess 'Edmonds\LolanSo';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Procédures stockées système &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [DROP USER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
