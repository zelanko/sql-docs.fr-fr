---
title: sys.sp_cleanup_temporal_history | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: d74211c9c5052adc9fa49f47b55b9c379c33f01c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56026440"
---
# <a name="sysspcleanuptemporalhistory-transact-sql"></a>sys.sp_cleanup_temporal_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

Supprime toutes les lignes de la table d’historique temporelle qui correspondent à la période HISTORY_RETENTION configurée dans une transaction unique.
  
## <a name="syntax"></a>Syntaxe  
```  
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```  
  
## <a name="arguments"></a>Arguments  

*@table_name*

Le nom de la table temporelle pour la rétention nettoyage est appelé.

*schema_name*

Le nom du schéma de table temporelle actuelle appartient

*row_count_var* [OUTPUT]

Le paramètre de sortie qui retourne le nombre de lignes supprimées. Si la table d’historique a un index columnstore, ce paramètre retourne toujours 0.
  
## <a name="remarks"></a>Notes
Cette procédure stockée peut être utilisée uniquement avec les tables temporelles qu’ont une période de rétention spécifiée.
Utilisez cette procédure stockée uniquement si vous devez nettoyer immédiatement toutes les lignes anciennes de la table d’historique. Vous devez savoir qu’il peut avoir un impact significatif sur le journal de base de données et le sous-système d’e/s comme il supprime toutes les lignes éligibles dans la même transaction. 

Il est toujours recommandé de s’appuient sur une tâche en arrière-plan interne pour le nettoyage que supprime les anciennes lignes avec un impact minimal sur les charges de travail normales et la base de données en général.

## <a name="permissions"></a>Autorisations  
 Nécessite les autorisations db_owner.  

## <a name="example"></a>Exemple

```
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="see-also"></a>Voir aussi

[Stratégie de rétention de tables temporelles](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
