---
title: SET RESULT_SET_CACHING (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/16/2020
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords: ''
dev_langs:
- TSQL
helpviewer_keywords: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: c975242a65da5ef29374267262deb6d8bf370f25
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87397018"
---
# <a name="set-result-set-caching-transact-sql"></a>DÉFINIR LA MISE EN CACHE DU JEU DE RÉSULTATS (Transact-SQL) 

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Contrôle le comportement de mise en cache du jeu de résultats pour la session client actuelle.  

S’applique à Azure SQL Data Warehouse  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe

```syntaxsql
SET RESULT_SET_CACHING { ON | OFF };
```  
  
## <a name="remarks"></a>Notes  

Exécutez cette commande quand vous êtes connecté à la base de données utilisateur pour laquelle vous souhaitez configurer le paramètre result_set_caching.

**ON**   
Active la mise en cache du jeu de résultats pour la session client actuelle.  La mise en cache du jeu de résultats ne peut pas être activée pour une session si elle est désactivée au niveau de la base de données.

**OFF**   
Désactive la mise en cache du jeu de résultats pour la session client actuelle.

## <a name="examples"></a>Exemples

Interrogez la colonne result_cache_hit de [sys.dm_pdw_exec_requests](/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql) avec request_id d’une requête pour voir si cette requête a été exécutée avec une correspondance dans le cache de résultat ou un échec.

```sql
SELECT result_cache_hit
FROM sys.dm_pdw_exec_requests
WHERE request_id = 'QID58286'
```

## <a name="permissions"></a>Autorisations

Nécessite l’appartenance au rôle public.

## <a name="see-also"></a>Voir aussi

- [Optimisation des performances avec la mise en cache des jeux de résultats](/azure/sql-data-warehouse/performance-tuning-result-set-caching)
- [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options?view=azure-sqldw-latest)
- [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)
- [DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-showresultcachespaceused-transact-sql)
- [DBCC DROPRESULTSETCACHE (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-dropresultsetcache-transact-sql)
