---
title: sp_add_targetsvrgrp_member (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_add_targetsvrgrp_member
- sp_add_targetsvrgrp_member_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_add_targetsvrgrp_member
ms.assetid: 5021ed5b-acca-4f8b-b9db-18733059c359
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 04d278e67070b10c72fb0820d17f6d19b37d323b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="spaddtargetsvrgrpmember-transact-sql"></a>sp_add_targetsvrgrp_member (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute le serveur cible spécifié au groupe de serveurs cibles spécifié.  
   
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_add_targetsvrgrp_member [ @group_name = ] 'group_name' , [ @server_name = ] 'server_name'   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@group_name=** ] **'***nom_groupe***'**  
 Le nom du groupe. *nom_groupe* est **sysname**, sans valeur par défaut.  
  
 [  **@server_name=** ] **'***nom_serveur***'**  
 Nom du serveur à ajouter au groupe spécifié. *nom_serveur* est **nvarchar (30)**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="remarks"></a>Notes  
 Un serveur cible peut être membre de plusieurs groupes de serveurs cibles.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter cette procédure.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant ajoute le groupe `Servers Maintaining Customer Information`, ainsi que le serveur `LONDON1` à ce groupe.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_targetsvrgrp_member  
   @group_name = N'Servers Maintaining Customer Information',  
   @server_name = N'LONDON1' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_delete_targetsvrgrp_member &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-targetsvrgrp-member-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
