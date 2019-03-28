---
title: sp_droprole (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droprole
- sp_droprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprole
ms.assetid: 889ee074-00f8-40a9-bddb-d7d3ef0cbc19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f07ccd19a419f3b6d332213e9846aec740b0c152
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538400"
---
# <a name="spdroprole-transact-sql"></a>sp_droprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un rôle de base de données de la base de données actuelle.  
  
> [!IMPORTANT]  
>  Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **sp_droprole** a été remplacé par l’instruction DROP ROLE. **sp_droprole** est inclus uniquement pour la compatibilité avec les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et ne peut pas être pris en charge dans une version ultérieure.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_droprole [ @rolename= ] 'role'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @rolename = ] 'role'` Est le nom du rôle de base de données à supprimer de la base de données actuelle. *rôle* est un **sysname**, sans valeur par défaut. *rôle* doit déjà exister dans la base de données actuelle.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Seuls les rôles de base de données peuvent être supprimées à l’aide de **sp_droprole**.  
  
 Il est impossible de supprimer un rôle de base de données s'il possède des membres. Il faut supprimer tous les membres d'un rôle de base de données avant de supprimer ce rôle. Pour supprimer des utilisateurs à partir d’un rôle, utilisez **sp_droprolemember**. Si tous les utilisateurs sont toujours membres du rôle, **sp_droprole** affiche ces membres.  
  
 Rôles fixes et le **public** rôle ne peut pas être supprimé.  
  
 Il n'est pas possible de supprimer un rôle s'il est propriétaire d'éléments sécurisables. Avant de supprimer un rôle d'application propriétaire d'éléments sécurisables, vous devez transférer la propriété de ces éléments sécurisables ou les supprimer. Utilisez ALTER AUTHORIZATION pour changer le propriétaire des objets qui ne doivent pas être supprimés.  
  
 **sp_droprole** ne peut pas être exécutée dans une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Autorisations  
 Il faut avoir l'autorisation CONTROL sur le rôle.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le rôle d'application `Sales`.  
  
```  
EXEC sp_droprole 'Sales';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [DROP ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_dropapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropapprole-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
