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
ms.openlocfilehash: 98796b89486ce59b289c83a74e5c466a6522b557
ms.sourcegitcommit: 710d60e7974e2c4c52aebe36fceb6e2bbd52727c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72278323"
---
# <a name="syssp_rda_set_query_mode-transact-sql"></a>sys.sp_rda_set_query_mode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Spécifie si les requêtes sur la base de données Stretch active et ses tables retournent à la fois les données locales et distantes (par défaut), ou les données locales uniquement.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_rda_set_query_mode [ @mode = ] @mode   
    [ , [ @force = ]  @force ]  
```  
  
## <a name="arguments"></a>Arguments  
 [@mode =] *mode de\@*  
 Est l’une des valeurs suivantes.  
  
-   **Désactivé** Toutes les requêtes sur les tables compatibles Stretch échouent.  
  
-   **LOCAL_ONLY** Les requêtes sur les tables compatibles Stretch ne retournent que des données locales.  
  
-   **LOCAL_AND_REMOTE** Les requêtes sur les tables compatibles avec Stretch retournent les données locales et distantes. Il s'agit du comportement par défaut.  
  
 [@force =]  *\@force*  
 Est une valeur de bit facultative que vous pouvez définir sur 1 si vous souhaitez modifier le mode de requête sans validation.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès) ou > 0 (échec)  
  
## <a name="permissions"></a>Autorisations  
 Requiert db_owner autorisations.  
  
## <a name="remarks"></a>Notes  
 Les procédures stockées étendues suivantes définissent également le mode de requête pour une base de données Stretch.  
  
-   **sp_rda_deauthorize_db**  
  
     Après l’exécution de **sp_rda_deauthorize_db** , toutes les requêtes sur les tables et les bases de données Stretch échouent. Autrement dit, le mode de requête est défini sur désactivé. Pour quitter ce mode, effectuez l’une des opérations suivantes.  
  
    -   Exécutez la commande [sys &#40;. sp_rda_reauthorize_db Transact&#41; -SQL](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) pour vous reconnecter à la base de données Azure distante. Cette opération rétablit automatiquement le mode de requête LOCAL_AND_REMOTE, qui est le comportement par défaut pour Stretch Database. Autrement dit, les requêtes retournent des résultats à partir de données locales et distantes.  
  
    -   Exécutez [sys. sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) avec l’argument LOCAL_ONLY pour permettre aux requêtes de continuer à s’exécuter sur des données locales uniquement.  
  
-   **sp_rda_reauthorize_db**  
  
     Lorsque vous exécutez [sys. sp_rda_reauthorize_db &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) pour vous reconnecter à la base de données Azure distante, cette opération réinitialise automatiquement le mode de requête sur LOCAL_AND_REMOTE, qui est le comportement par défaut pour Stretch Database. Autrement dit, les requêtes retournent des résultats à partir de données locales et distantes.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.sp_rda_deauthorize_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
