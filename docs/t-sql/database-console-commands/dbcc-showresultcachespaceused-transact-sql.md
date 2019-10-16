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
ms.openlocfilehash: c2dd0389f4ec3287fbe23875458ab5d34ef269f7
ms.sourcegitcommit: 79e6d49ae4632f282483b0be935fdee038f69cc2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72174656"
---
# <a name="dbcc-showresultcachespaceused-transact-sql"></a>DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Affiche la mise en cache du jeu de résultats utilisée par l’espace de stockage pour une base de données [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Azure.
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DBCC SHOWRESULTCACHESPACEUSED  
[;]  
```  
## <a name="remarks"></a>Notes

La commande `DBCC SHOWRESULTCACHESPACEUSED` n’accepte aucun paramètre et retourne l’espace utilisé par la base de données à l’endroit où la commande est exécutée.

La taille maximale du cache de jeu de résultats est de 1 To par base de données.  Azure SQL Data Warehouse supprime automatiquement les entrées dans le cache du jeu de résultats :

- toutes les 48 heures si le jeu de résultats n’a pas été utilisé.
- lorsque le cache du jeu de résultats approche la taille maximale.

Pour vider manuellement le cache des résultats d’une base de données, les utilisateurs peuvent utiliser l’une des options suivantes :

- Désactiver la fonctionnalité de résultats pour la base de données
- Exécuter `DBCC DROPRESULTSETCACHE` pendant la connexion à la base de données 

La suspension d’une base de données ne permet pas de vider le cache du jeu de résultats.  

## <a name="permissions"></a>Autorisations

Requiert l'autorisation VIEW SERVER STATE.
  
## <a name="result-sets"></a>Jeux de résultats  
  
|colonne|Type de données|Description|  
|------------|---------------|-----------------|  
|reserved_space|BIGINT|Espace total utilisé pour la base de données, en Ko. Ce nombre est modifié à mesure que le jeu de résultats mis en cache augmente.|  
|data_space|BIGINT|Espace utilisé pour les données, en Ko.|  
|index_space|BIGINT|Espace utilisé pour les index, en Ko.|  
|unused_space|BIGINT|Espace qui fait partie de l’espace réservé et non utilisé, en Ko.|  


## <a name="see-also"></a>Voir aussi

[ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options?view=azure-sqldw-latest)</br>
[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)</br>
[SET RESULT SET CACHING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-result-set-caching-transact-sql)</br>
[DBCC DROPRESULTSETCACHE  &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dropresultsetcache-transact-sql)