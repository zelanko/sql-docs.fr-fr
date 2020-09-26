---
description: ROWCOUNT_BIG (Transact-SQL)
title: ROWCOUNT_BIG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 124ba59b2942fcfa7c4ac26be7b24df35c75806a
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "91379974"
---
# <a name="rowcount_big-transact-sql"></a>ROWCOUNT_BIG (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Renvoie le nombre de lignes affectées par la dernière instruction exécutée. Cette fonction s’apparente à [@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md), si ce n’est que le type de retour de ROWCOUNT_BIG est **bigint**.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
ROWCOUNT_BIG ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Types de retour
 **bigint**  
  
## <a name="remarks"></a>Notes  
 Placée après une instruction SELECT, cette fonction renvoie le nombre de lignes renvoyées par l'instruction SELECT.  
  
 Placée après une instruction INSERT, UPDATE ou DELETE, cette fonction renvoie le nombre de lignes affectées par l'instruction de modification de données.  
  
 Placée après une instruction qui ne renvoie pas de lignes, telle qu'une instruction IF, cette fonction renvoie la valeur 0.  
  
## <a name="see-also"></a>Voir aussi  
 [COUNT_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/count-big-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  
