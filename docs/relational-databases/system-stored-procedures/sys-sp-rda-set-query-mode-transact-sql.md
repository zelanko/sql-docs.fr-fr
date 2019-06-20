---
title: sys.sp_rda_set_query_mode (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_query_mode
- sys.sp_rda_set_query_mode_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_query_mode stored procedure
ms.assetid: 65a0b390-cf87-4db7-972a-1fdf13456c88
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: aa168f3bbac37e34730d5ee0ab348f5fd7d1743d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65982884"
---
# <a name="syssprdasetquerymode-transact-sql"></a>sys.sp_rda_set_query_mode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Spécifie si des requêtes sur la base de données compatibles avec Stretch actuel et ses tables de retournent des données locales et distantes (par défaut), ou uniquement les données locales.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_rda_set_query_mode [ @mode = ] @mode   
    [ , [ @force = ]  @force ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @mode = ] *@mode*  
 Est une des valeurs suivantes.  
  
-   **DÉSACTIVÉ** toutes les requêtes sur les tables compatibles Stretch échouent.  
  
-   **LOCAL_ONLY** requêtes sur les tables compatibles Stretch retournent uniquement les données locales.  
  
-   **LOCAL_AND_REMOTE** requêtes sur les tables compatibles Stretch retournent des données locales et distantes. Il s'agit du comportement par défaut.  
  
 [ @force = ]  *@force*  
 Est une valeur de bit facultatif que vous pouvez définir sur 1 si vous souhaitez modifier le mode de requête sans validation.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès) ou > 0 (échec)  
  
## <a name="permissions"></a>Autorisations  
 Nécessite les autorisations db_owner.  
  
## <a name="remarks"></a>Notes  
 Les procédures stockées étendues suivantes également définissent le mode de requête pour une base de données compatibles avec Stretch.  
  
-   **sp_rda_deauthorize_db**  
  
     Après avoir exécuté **sp_rda_deauthorize_db** , toutes les requêtes sur les tables et les bases de données Stretch échouent. Autrement dit, le mode de requête est défini sur désactivé. Pour quitter ce mode, effectuez l’une des opérations suivantes.  
  
    -   Exécutez [sys.sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) se reconnecter à la base de données Azure distante. Cette opération réinitialise automatiquement le mode de requête LOCAL_AND_REMOTE, qui est le comportement par défaut pour Stretch Database. Autrement dit, les requêtes retournent des résultats à partir de données locales et distantes.  
  
    -   Exécutez [sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) avec l’argument LOCAL_ONLY pour permettre les requêtes continuent de s’exécuter avec les données locales uniquement.  
  
-   **sp_rda_reauthorize_db**  
  
     Lorsque vous exécutez [sys.sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) pour vous reconnecter à la base de données Azure distante, cette opération rétablit automatiquement le mode de requête LOCAL_AND_REMOTE, qui est le comportement par défaut pour Stretch Database. Autrement dit, les requêtes retournent des résultats à partir de données locales et distantes.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.sp_rda_deauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
