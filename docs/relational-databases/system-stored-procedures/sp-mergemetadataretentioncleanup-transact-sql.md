---
title: sp_mergemetadataretentioncleanup (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergemetadataretentioncleanup
- sp_mergemetadataretentioncleanup_TSQL
helpviewer_keywords:
- sp_mergemetadataretentioncleanup
ms.assetid: 4e8d6343-2a38-421d-a3f3-c37d437a0f88
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 78ef8690e4f8dd374125d4c8e6e77a4a1964d329
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828302"
---
# <a name="sp_mergemetadataretentioncleanup-transact-sql"></a>sp_mergemetadataretentioncleanup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Effectue un nettoyage manuel des métadonnées dans les tables système [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_mappings](../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md)et [MSmerge_current_partition_mappings](../../relational-databases/system-tables/msmerge-current-partition-mappings.md) . Cette procédure stockée est exécutée sur chaque serveur de publication et abonné dans la topologie.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_mergemetadataretentioncleanup [ [ @num_genhistory_rows = ] num_genhistory_rows OUTPUT ]  
    [ , [ @num_contents_rows = ] num_contents_rows OUTPUT ]   
    [ , [ @num_tombstone_rows = ] num_tombstone_rows OUTPUT ]   
    [ , [ @aggressive_cleanup_only = ] aggressive_cleanup_only ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @num_genhistory_rows = ] num_genhistory_rows OUTPUT`Retourne le nombre de lignes nettoyées à partir de la table [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md) . *num_genhistory_rows* est de **type int**, avec **0**comme valeur par défaut.  
  
`[ @num_contents_rows = ] num_contents_rows OUTPUT`Retourne le nombre de lignes nettoyées à partir de la table [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) . *num_contents_rows* est de **type int**, avec **0**comme valeur par défaut.  
  
`[ @num_tombstone_rows = ] num_tombstone_rows OUTPUT`Retourne le nombre de lignes nettoyées à partir de la table [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) . *num_tombstone_rows* est de **type int**, avec **0**comme valeur par défaut.  
  
`[ @aggressive_cleanup_only = ] aggressive_cleanup_only`À usage interne uniquement.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Remarques  
  
> [!IMPORTANT]  
>  S’il existe plusieurs publications dans une base de données et que l’une de ces publications utilise une période de rétention de publication infinie, l’exécution de **sp_mergemetadataretentioncleanup** ne nettoie pas les métadonnées de suivi des modifications de réplication de fusion pour la base de données. C'est pour cette raison qu'il faut utiliser la période de rétention infinie avec prudence. Pour déterminer si une publication a une période de rétention infinie, exécutez [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md) sur le serveur de publication et Notez toutes les publications dans le jeu de résultats avec la valeur **0** pour la **rétention**.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du **db_owner** rôle de base de données fixe ou les utilisateurs de la liste d’accès à la publication d’une base de données publiée peuvent exécuter **sp_mergemetadataretentioncleanup**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
