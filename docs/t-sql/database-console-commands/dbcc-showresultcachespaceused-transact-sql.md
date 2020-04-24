---
title: DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: f6821ae2ee11a6cd8e5713996cc04b3330a63300
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632329"
---
# <a name="dbcc-showresultcachespaceused-transact-sql"></a>DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Affiche la mise en cache du jeu de résultats utilisée par l’espace de stockage pour une base de données [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Azure.
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
DBCC SHOWRESULTCACHESPACEUSED  
[;]  
```  
## <a name="remarks"></a>Notes

La commande `DBCC SHOWRESULTCACHESPACEUSED` n’accepte aucun paramètre et retourne l’espace utilisé par la base de données à l’endroit où la commande est exécutée.

## <a name="permissions"></a>Autorisations

Requiert l'autorisation VIEW SERVER STATE.
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Colonne|Type de données|Description|  
|------------|---------------|-----------------|  
|reserved_space|bigint|Espace total utilisé pour la base de données, en Ko. Ce nombre est modifié à mesure que le jeu de résultats mis en cache augmente.|  
|data_space|bigint|Espace utilisé pour les données, en Ko.|  
|index_space|bigint|Espace utilisé pour les index, en Ko.|  
|unused_space|bigint|Espace qui fait partie de l’espace réservé et non utilisé, en Ko.|  


## <a name="see-also"></a>Voir aussi

[Optimisation des performances avec la mise en cache des jeux de résultats](/azure/sql-data-warehouse/performance-tuning-result-set-caching)</br>
[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options?view=azure-sqldw-latest)</br>
[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)</br>
[SET RESULT SET CACHING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-result-set-caching-transact-sql)</br>
[DBCC DROPRESULTSETCACHE  &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dropresultsetcache-transact-sql)
