---
title: DBCC DROPCLEANBUFFERS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROPCLEANBUFFERS
- DBCC_DROPCLEANBUFFERS_TSQL
- DROPCLEANBUFFERS_TSQL
- DBCC DROPCLEANBUFFERS
dev_langs:
- TSQL
helpviewer_keywords:
- clean buffers
- cold buffer cache
- buffer pools [SQL Server]
- dropping buffers
- removing buffers
- DBCC DROPCLEANBUFFERS statement
ms.assetid: a4121927-f2ce-4926-aa2c-9b1519dac048
author: pmasl
ms.author: umajay
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a3b2d2ff81fddaae0b0ae68da9d4477819a61073
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68101935"
---
# <a name="dbcc-dropcleanbuffers-transact-sql"></a>DBCC DROPCLEANBUFFERS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

Supprime toutes les mémoires tampons propres du pool de mémoires tampons et les objets columnstore du pool d’objets columnstore.
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe
Syntaxe de SQL Server : 

```sql
DBCC DROPCLEANBUFFERS [ WITH NO_INFOMSGS ]  
```  
Syntaxe d’Azure SQL Warehouse et Parallel Data Warehouse :

```sql  
DBCC DROPCLEANBUFFERS ( COMPUTE | ALL ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Arguments  
 WITH NO_INFOMSGS  
 Supprime tous les messages d'information. Les messages d’informations sont toujours supprimés sur [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 COMPUTE  
 Videz le cache de données en mémoire sur chaque nœud de calcul.  
  
 ALL  
 Videz le cache de données en mémoire sur chaque nœud de calcul et sur le nœud de contrôle. Il s’agit de la valeur par défaut si vous ne spécifiez aucune valeur.  
  
## <a name="remarks"></a>Notes  
Utilisez l'instruction DBCC DROPCLEANBUFFERS pour vérifier les requêtes avec un cache de tampons à froid sans arrêter et redémarrer le serveur.
Pour supprimer les mémoires tampons propres du pool de mémoires tampons et les objets columnstore du pool d’objets columnstore, utilisez d'abord CHECKPOINT pour générer un cache de tampons à froid. Cette opération permet d'écrire sur disque toutes les pages incorrectes de la base de données active et de nettoyer les mémoires tampons. Ensuite, vous pouvez émettre la commande DBCC DROPCLEANBUFFERS pour supprimer toutes les mémoires tampons du pool de mémoires tampons.
  
## <a name="result-sets"></a>Jeux de résultats  
DBCC DROPCLEANBUFFERS sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne :
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Autorisations  

S’applique à : SQL Server, Parallel Data Warehouse 

- Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  

S’applique à : Azure SQL Data Warehouse

- Nécessite l'appartenance au rôle serveur fixe DB_OWNER.  
  
## <a name="see-also"></a>Voir aussi  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)  
  
  
