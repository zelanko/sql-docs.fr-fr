---
title: ROWCOUNT_BIG (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROWCOUNT_BIG
- ROWCOUNT_BIG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ROWCOUNT_BIG function
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 6e18a0eb-bb36-4348-90d9-8b1ecf095064
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 38c430082532904b230e7a4a594e82e5c14e670e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="rowcountbig-transact-sql"></a>ROWCOUNT_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Renvoie le nombre de lignes affectées par la dernière instruction exécutée. Cette fonction s’apparente à [@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md), sauf le type de retour de ROWCOUNT_BIG est **bigint**.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ROWCOUNT_BIG ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 **bigint**  
  
## <a name="remarks"></a>Notes  
 Placée après une instruction SELECT, cette fonction renvoie le nombre de lignes renvoyées par l'instruction SELECT.  
  
 Placée après une instruction INSERT, UPDATE ou DELETE, cette fonction renvoie le nombre de lignes affectées par l'instruction de modification de données.  
  
 Placée après une instruction qui ne renvoie pas de lignes, telle qu'une instruction IF, cette fonction renvoie la valeur 0.  
  
## <a name="see-also"></a>Voir aussi  
 [COUNT_BIG &#40; Transact-SQL &#41;](../../t-sql/functions/count-big-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  

