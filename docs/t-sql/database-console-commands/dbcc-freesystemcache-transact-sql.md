---
description: DBCC FREESYSTEMCACHE (Transact-SQL)
title: DBCC FREESYSTEMCACHE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/25/2020
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FREESYSTEMCACHE_TSQL
- DBCC_FREESYSTEMCACHE_TSQL
- DBCC FREESYSTEMCACHE
- FREESYSTEMCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- clearing unused cache entries
- DBCC FREESYSTEMCACHE statement
- unused cache entries
- releasing unused cache entries
- freeing unused cache entries
- cleaning unused cache entries
ms.assetid: 4b5c460b-e4ad-404a-b4ca-d65aba38ebbb
author: pmasl
ms.author: umajay
ms.openlocfilehash: f99d6e50aed43273dbcaa659f95a8bb8a1fe73d3
ms.sourcegitcommit: 544706f6725ec6cdca59da3a0ead12b99accb2cc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638982"
---
# <a name="dbcc-freesystemcache-transact-sql"></a>DBCC FREESYSTEMCACHE (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Libère les entrées non utilisées de tous les caches. Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nettoie, en arrière-plan et de manière proactive, les entrées de cache non utilisées afin de libérer de la mémoire pour les entrées actives. Vous pouvez toutefois utiliser cette commande pour supprimer manuellement les entrées non utilisées de tous les caches ou du cache de pool Resource Governor spécifié.
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
```syntaxsql
DBCC FREESYSTEMCACHE   
    ( 'ALL' [, pool_name ] )   
    [WITH   
    { [ MARK_IN_USE_FOR_REMOVAL ] , [ NO_INFOMSGS ]  }  
    ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
( 'ALL' [, _nom\_pool_ ] )  
ALL spécifie tous les caches pris en charge.  
_nom\_pool_ spécifie un cache de pool Resource Governor. Seules les entrées associées à ce pool sont libérées.  
  
MARK_IN_USE_FOR_REMOVAL  
Libère de manière asynchrone les entrées en cours d'utilisation de leurs caches respectifs une fois qu'elles ne sont plus utilisées. Après l’exécution DBCC FREESYSTEMCACHE WITH MARK_IN_USE_FOR_REMOVAL, les nouvelles entrées créées dans le cache ne sont pas affectées.  
  
NO_INFOMSGS  
Supprime tous les messages d'information.  
  
## <a name="remarks"></a>Notes  
L'exécution de DBCC FREESYSTEMCACHE efface le cache du plan pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette opération entraîne la recompilation de tous les plans d’exécution ultérieurs et peut entraîner une diminution temporaire et brutale des performances des requêtes. Pour chaque mémoire cache effacée du cache du plan, le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient le message d’information suivant : 

>`SQL Server has encountered %d occurrence(s) of cachestore flush for the '%s' cachestore (part of plan cache) due to 'DBCC FREEPROCCACHE' or 'DBCC FREESYSTEMCACHE' operations.`

 Ce message est enregistré toutes les cinq minutes si le cache est vidé au cours de cet intervalle de temps.

## <a name="result-sets"></a>Jeux de résultats  
DBCC FREESYSTEMCACHE retourne : « Exécution de DBCC terminée. Si DBCC vous a adressé des messages d'erreur, contactez l'administrateur système. »
  
## <a name="permissions"></a>Autorisations  
Nécessite l'autorisation ALTER SERVER STATE sur le serveur.
  
## <a name="examples"></a>Exemples  
  
### <a name="a-releasing-unused-cache-entries-from-a-resource-governor-pool-cache"></a>R. Libération des entrées de cache non utilisées d'un cache de pool du gouverneur de ressources  
L'exemple suivant illustre comment nettoyer des caches qui sont dédiés à un pool de ressources du gouverneur de ressources spécifié.
  
```sql
-- Clean all the caches with entries specific to the resource pool named "default".  
DBCC FREESYSTEMCACHE ('ALL', default);  
```  
  
### <a name="b-releasing-entries-from-their-respective-caches-after-they-become-unused"></a>B. Libération des entrées de leurs caches respectifs une fois qu'elles ne sont plus utilisées  
L'exemple suivant utilise la clause MARK_IN_USE_FOR_REMOVAL pour libérer les entrées de tous les caches actuels une fois qu'elles ne sont plus utilisées.
  
```sql
DBCC FREESYSTEMCACHE ('ALL') WITH MARK_IN_USE_FOR_REMOVAL;  
```  
  
## <a name="see-also"></a>Voir aussi  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC FREEPROCCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md)  
[DBCC FREESESSIONCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-freesessioncache-transact-sql.md)  
[gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md)
  
  
