---
title: Sys.sp_rda_deauthorize_db (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_deauthorize_db
- sys.sp_rda_deauthorize_db_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.sp_rda_deauthorize_db stored procedure
ms.assetid: 2e362e15-2cd5-4856-9f0b-54df56b0866b
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6524ced433a0b4b58de1fd857ce32f02cfb64923
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syssprdadeauthorizedb-transact-sql"></a>Sys.sp_rda_deauthorize_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Supprime la connexion authentifiée entre une base de données prenant en charge Stretch locale et la base de données Azure distante. Exécutez **sp_rda_deauthorize_db** lorsque la base de données distant est inaccessible ou dans un état incohérent et que vous souhaitez modifier le comportement de la requête pour toutes les tables compatibles Stretch dans la base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_rda_deauthorize_db   
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou >0 (échec)  
  
## <a name="permissions"></a>Permissions  
 Nécessite les autorisations db_owner.  
  
## <a name="remarks"></a>Notes  
 Après avoir exécuté **sp_rda_deauthorize_db** , toutes les requêtes sur les tables et les bases de données Stretch échouent. Autrement dit, le mode de requête est défini sur désactivé. Pour quitter ce mode, effectuez l’une des opérations suivantes.  
  
-   Exécutez [sys.sp_rda_reauthorize_db &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) se reconnecter à la base de données Azure distante. Cette opération réinitialise automatiquement le mode de requête LOCAL_AND_REMOTE, qui est le comportement par défaut pour la base de données Stretch. Autrement dit, les requêtes retournent des résultats à partir des données locales et distantes.  
  
-   Exécutez [sys.sp_rda_set_query_mode &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) avec l’argument LOCAL_ONLY pour vous permettre de requêtes continuent de s’exécuter avec les données locales uniquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.sp_rda_set_query_mode &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md)   
 [Sys.sp_rda_reauthorize_db &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
