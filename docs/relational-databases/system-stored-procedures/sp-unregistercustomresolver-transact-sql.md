---
title: sp_unregistercustomresolver (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_unregistercustomresolver_TSQL
- sp_unregistercustomresolver
helpviewer_keywords:
- sp_unregistercustomresolver
ms.assetid: 08bd20c8-c6be-4be2-be9f-2b5e1d7bee43
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 831b1004df2d4c62f81e051fb4cdb95e48a97d35
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spunregistercustomresolver-transact-sql"></a>sp_unregistercustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Annule l'inscription d'un module de logique métier précédemment inscrit. La logique métier peut prendre la forme d'un composant COM ou d'un assemby [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework. Cette procédure stockée est exécutée sur le serveur de distribution dans lequel la logique métier personnalisée a été inscrite.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_unregistercustomresolver [ @article_resolver = ] 'article_resolver'   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@article_resolver =** ] **'***article_resolver***'**  
 Spécifie le nom de la logique métier personnalisée en cours de désinscription. *article_resolver* est **nvarchar (255)**, sans valeur par défaut. Si la logique métier en cours de suppression est un composant COM, ce paramètre est le nom convivial du composant. Si la logique métier est un assembly .NET Framework, ce paramètre correspond au nom de l'assembly.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_unregistercustomresolver** est utilisé dans la réplication de fusion.  
  
 Utilisez [sp_enumcustomresolvers](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) n’importe quel serveur dans la topologie de réplication pour retourner la liste des modules de logique métier personnalisée inscrits ou des programmes de résolution COM disponibles à la topologie.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** du rôle de base de données fixe peut exécuter **sp_unregistercustomresolver**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_lookupcustomresolver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_registercustomresolver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
