---
title: sys. sp_cleanup_temporal_history | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a9cd5efaf70a915b6a31dced0f79498a01dd7ef5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783596"
---
# <a name="syssp_cleanup_temporal_history-transact-sql"></a>sys. sp_cleanup_temporal_history (Transact-SQL)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

Supprime toutes les lignes de la table d’historique temporelle correspondant à la configuration HISTORY_RETENTION période au sein d’une même transaction.

## <a name="syntax"></a>Syntaxe

```
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```

## <a name="arguments"></a>Arguments

*\@table_name*

Nom de la table temporelle pour laquelle le nettoyage de rétention est appelé.

*schema_name*

Nom du schéma auquel appartient la table temporelle actuelle

*row_count_var* [sortie]

Paramètre de sortie qui retourne le nombre de lignes supprimées. Si la table d’historique contient un index cluster ColumnStore, ce paramètre retourne toujours la valeur 0.

## <a name="remarks"></a>Remarques

Cette procédure stockée ne peut être utilisée qu’avec des tables temporelles dont la période de rétention est définie.
Utilisez cette procédure stockée uniquement si vous devez nettoyer immédiatement toutes les lignes anciennes de la table d’historique. Vous devez savoir qu’il peut avoir un impact significatif sur le journal de base de données et sur le sous-système d’e/s, car il supprime toutes les lignes éligibles au sein de la même transaction.

Il est toujours recommandé de s’appuyer sur une tâche en arrière-plan interne pour le nettoyage qui supprime les lignes anciennes avec un impact minimal sur les charges de travail et la base de données normales en général.

## <a name="permissions"></a>Autorisations

Requiert db_owner autorisations.

## <a name="example"></a>Exemple

```sql
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="next-steps"></a>Étapes suivantes

[Stratégie de rétention des tables temporelles](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
