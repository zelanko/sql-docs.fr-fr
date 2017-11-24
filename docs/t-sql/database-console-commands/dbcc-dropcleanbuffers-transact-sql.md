---
title: DBCC DROPCLEANBUFFERS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROPCLEANBUFFERS
- DBCC_DROPCLEANBUFFERS_TSQL
- DROPCLEANBUFFERS_TSQL
- DBCC DROPCLEANBUFFERS
dev_langs: TSQL
helpviewer_keywords:
- clean buffers
- cold buffer cache
- buffer pools [SQL Server]
- dropping buffers
- removing buffers
- DBCC DROPCLEANBUFFERS statement
ms.assetid: a4121927-f2ce-4926-aa2c-9b1519dac048
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b10e1d76e20fdb8859cb83cbb65d984b49b21c52
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dbcc-dropcleanbuffers-transact-sql"></a>DBCC DROPCLEANBUFFERS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

Supprime tous les tampons nettoyés du pool de mémoires tampons et les objets de columnstore à partir du pool d’objet columnstore.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe
Syntaxe pour SQL Server : 

```sql
DBCC DROPCLEANBUFFERS [ WITH NO_INFOMSGS ]  
```  
Syntaxe de l’entrepôt SQL Azure et Parallel Data Warehouse :

```sql  
DBCC DROPCLEANBUFFERS ( COMPUTE | ALL ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Arguments  
 WITH NO_INFOMSGS  
 Supprime tous les messages d'information. Messages d’information sont toujours supprimés sur [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 COMPUTE  
 Vider le cache du plan de requête à partir de chaque nœud de calcul.  
  
 ALL  
 Vider le cache du plan de requête à partir de chaque nœud de calcul et de nœud de contrôle. Il s’agit de la valeur par défaut si vous ne spécifiez pas de valeur.  
  
## <a name="remarks"></a>Notes  
Utilisez l'instruction DBCC DROPCLEANBUFFERS pour vérifier les requêtes avec un cache de tampons à froid sans arrêter et redémarrer le serveur.
Pour supprimer les tampons nettoyés à partir des objets de columnstore et de pool de mémoire tampon à partir du pool d’objet columnstore, utilisez d’abord CHECKPOINT pour générer un cache de tampons à froid. Cette opération permet d'écrire sur disque toutes les pages incorrectes de la base de données active et de nettoyer les mémoires tampons. Ensuite, vous pouvez émettre la commande DBCC DROPCLEANBUFFERS pour supprimer toutes les mémoires tampons du pool de mémoires tampons.
  
## <a name="result-sets"></a>Jeux de résultats  
DBCC DROPCLEANBUFFERS sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne :
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  

S’applique à : SQL Server, de l’entrepôt de données en parallèle 

- Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  

S’applique à : Azure SQL Data Warehouse

- L’appartenance au rôle de serveur fixe DB_OWNER.  
  
## <a name="see-also"></a>Voir aussi  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)  
  
  
