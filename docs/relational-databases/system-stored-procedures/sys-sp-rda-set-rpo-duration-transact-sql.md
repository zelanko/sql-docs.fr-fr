---
title: sys. sp_rda_set_rpo_duration (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_rpo_duration
- sys.sp_rda_set_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_rpo_duration stored procedure
ms.assetid: 95c80c5b-9252-4612-9ea7-544c48834fd2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8e00939df070233efd2087a8534aaa711be01b3d
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053475"
---
# <a name="syssp_rda_set_rpo_duration-transact-sql"></a>sys. sp_rda_set_rpo_duration (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Définit le nombre d’heures de données migrées que SQL Server conserve dans une table de mise en lots pour garantir une restauration complète de la base de données Azure distante, si une limite de restauration dans le temps est nécessaire.    
    
 Pour plus d’informations, consultez [Stretch Database réduit le risque de perte de données pour vos données Azure en conservant temporairement les lignes migrées](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO).  
   
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
     
## <a name="syntax"></a>Syntaxe    
    
```    
    
sp_rda_set_rpo_duration [ @duration_hrs = ] duration_hrs    
    
```    
    
## <a name="arguments"></a>Arguments    
 [ @duration_hrs =] *duration_hrs*    
 Nombre d’heures (valeur entière non null) des données migrées que vous souhaitez SQL Server conserver pour la base de données Stretch actuelle. La valeur par défaut et la valeur minimale est de 8 heures.    
 
 > [!NOTE]
 > Des valeurs plus élevées requièrent plus d’espace de stockage sur SQL Server.
    
## <a name="permissions"></a>Autorisations    
 Requiert db_owner autorisations.    
    
## <a name="remarks"></a>Remarques    
 Récupérez la valeur actuelle en exécutant [sys. sp_rda_get_rpo_duration &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md).    
    
## <a name="see-also"></a>Voir aussi    
 [sys. sp_rda_get_rpo_duration &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)     
 [Restaurer des bases de données Stretch (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)     
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
