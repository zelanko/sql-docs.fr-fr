---
title: sys.sp_rda_reconcile_batch (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_batch
- sys.sp_rda_reconcile_batch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_batch stored procedure
ms.assetid: 6d21eac3-7b6c-4fe0-8bc4-bf503f3948a6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 54bdac5237ff190f3620bb29dabbf684868c0b75
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65982929"
---
# <a name="syssprdareconcilebatch-transact-sql"></a>sys.sp_rda_reconcile_batch (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Rapproche l’ID de lot stocké dans la table compatible Stretch SQL Server avec l’ID de lot stocké dans la table Azure distante.  
  
 En général, vous devez uniquement exécuter **sp_rda_reconcile_batch** si vous avez supprimé manuellement les données plus récemment migrées à partir de la table distante. Lorsque vous supprimez manuellement les données distantes qui inclut le lot la plus récente, les ID de lot ne sont pas synchronisés et la migration s’arrête.  
 
 Pour supprimer les données qui a déjà été migrées vers Azure, consultez la section Notes sur cette page.
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Arguments  
 \@objname = '*\@objname*'  
 Le nom de la table SQL Server compatible Stretch.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite les autorisations db_owner.  
  
## <a name="remarks"></a>Notes  
 Si vous souhaitez supprimer des données qui a déjà été migrées vers Azure, procédez comme suit.  
  
1.  Suspendre la migration des données. Pour plus d’informations, consultez [Suspension et reprise de la migration de données &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
2.  Supprimer les données de la table intermédiaire de SQL Server en exécutant une commande de suppression avec l’indicateur STAGE_ONLY. Pour plus d’informations, consultez [apporter des mises à jour administratives et les suppressions](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md#adminHints).
  
3.  Supprimer les mêmes données à partir de la table Azure à distance en exécutant une commande de suppression avec l’indicateur REMOTE_ONLY.  
  
4.  Exécutez **sp_rda_reconcile_batch**.  
  
5.  Reprendre la migration des données. Pour plus d’informations, consultez [Suspension et reprise de la migration de données &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
## <a name="example"></a>Exemple  
 Pour rapprocher l’ID de lot, exécutez l’instruction suivante.  
  
```sql  
EXEC sp_rda_reconcile_batch @objname = N'StretchEnabledTableName';  
```  
  
  
