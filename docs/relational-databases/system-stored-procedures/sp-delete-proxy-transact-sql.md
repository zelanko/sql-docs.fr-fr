---
title: sp_delete_proxy (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_proxy
- sp_delete_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_proxy
- DROP PROXY statement
ms.assetid: 44a1db13-b7f2-4dab-a1b5-b8dafb41737c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1db08d96a36112d686ab34db0b7989e910a01960
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47844057"
---
# <a name="spdeleteproxy-transact-sql"></a>sp_delete_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime le proxy spécifié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_proxy [ @proxy_id = ] id , [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@proxy_id**=] *id*  
 Numéro d'identification du proxy à supprimer. Le *proxy_id* est **int**, avec NULL comme valeur par défaut.  
  
 [ **@proxy_name**=] **'***proxy_name***'**  
 Nom du proxy à supprimer. Le *proxy_name* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 Soit **@proxy_name** ou **@proxy_id** doit être spécifié. Si ces deux arguments sont spécifiés, ils doivent tous les deux référencer le même proxy, sinon la procédure stockée échoue.  
  
 Si une étape d'un travail fait référence au proxy spécifié, ce dernier ne peut pas être supprimé et la procédure stockée échoue.  
  
## <a name="permissions"></a>Permissions  
 Par défaut, seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_delete_proxy**.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le proxy `Catalog application proxy`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_proxy  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)  
  
  
