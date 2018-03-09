---
title: sp_droptype (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_droptype_TSQL
- sp_droptype
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droptype
ms.assetid: e78464ac-2370-4c4e-9cc0-06aebc07cec5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95c6a5166d3e1dec0bef153c3c545bdc36d879aa
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="spdroptype-transact-sql"></a>sp_droptype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Supprime un type de données d’alias de **systypes**.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_droptype [ @typename = ] 'type'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@typename=**] **'***type***'**  
 Nom d'un type de données alias dont vous êtes propriétaire. *type* est **sysname**, sans valeur par défaut.  
  
## <a name="return-code-type"></a>Type des codes renvoyés  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="remarks"></a>Notes  
 Le **type** alias type de données ne peut pas être supprimé si des tables ou autres objets de base de données font référence.  
  
> [!NOTE]  
>  Vous ne pouvez pas supprimer un type de données alias si celui-ci est utilisé dans une définition de table ou si une règle ou une valeur par défaut lui est associée.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance dans le **db_owner** rôle de base de données fixe ou la **db_ddladmin** rôle de base de données fixe.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le type de données alias `birthday`.  
  
> [!NOTE]  
>  Ce type de données alias doit déjà exister, faute de quoi cet exemple renvoie un message d'erreur.  
  
```  
USE master;  
GO  
EXEC sp_droptype 'birthday';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de base de données stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addtype &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addtype-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
