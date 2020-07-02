---
title: sp_dropmergefilter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergefilter_TSQL
- sp_dropmergefilter
helpviewer_keywords:
- sp_dropmergefilter
ms.assetid: 798586d7-05f3-4a5e-bea8-a34b7b52d0fd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8af47dea0174f094221ac3cdede781f3738b3fd7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783836"
---
# <a name="sp_dropmergefilter-transact-sql"></a>sp_dropmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Supprime un filtre de fusion. **sp_dropmergefilter** supprime toutes les colonnes de filtre de fusion définies dans le filtre de fusion à supprimer. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropmergefilter [ @publication= ] 'publication', [ @article= ] 'article'     , [ @filtername= ] 'filtername'  
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @article = ] 'article'`Nom de l’article. *article* est de **type sysname**et n’a pas de valeur par défaut.  
  
`[ @filtername = ] 'filtername'`Nom du filtre à supprimer. *FilterName* est de **type sysname**, sans valeur par défaut.  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`Active ou désactive la possibilité d’invalider un instantané. *force_invalidate_snapshot* est un **bit**, avec **0**comme valeur par défaut.  
  
 **0** indique que les modifications apportées à l’article de fusion n’entraînent pas la non-validité de l’instantané.  
  
 **1** signifie que les modifications apportées à l’article de fusion peuvent entraîner la non-validité de l’instantané. Si tel est le cas, la valeur **1** accorde l’autorisation pour que le nouvel instantané se produise.  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`Active ou désactive la possibilité de marquer un abonnement comme non valide. *force_reinit_subscription* est un **bit**, avec **0**comme valeur par défaut.  
  
 **0** indique que les modifications apportées au filtre d’article de fusion n’entraînent pas la non-validité des abonnements.  
  
 **1** signifie que les modifications apportées au filtre d’article de fusion entraînent la non-validité des abonnements.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Remarques  
 **sp_dropmergefilter** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_dropmergefilter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier les propriétés de publication et d’article](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
