---
title: Fonctions de curseur (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], cursors
- cursor functions
ms.assetid: 7d9daa10-4c50-4212-9400-42120222b2b8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4f7e49dc39d95e4d5bcce285040f8a598e6935ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026287"
---
# <a name="cursor-functions-transact-sql"></a>Fonctions de curseur (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Ces fonctions scalaires retournent des informations sur les curseurs :
  
|||  
|-|-|  
|[@@CURSOR_ROWS](../../t-sql/functions/cursor-rows-transact-sql.md)|[CURSOR_STATUS](../../t-sql/functions/cursor-status-transact-sql.md)|  
|[@@FETCH_STATUS](../../t-sql/functions/fetch-status-transact-sql.md)||  
  
Toutes les fonctions de curseur sont non déterministes. Cela signifie qu’elles ne retournent pas toujours les mêmes résultats chaque fois qu’elles s’exécutent, même avec un ensemble identique de valeurs d’entrée. Pour plus d’informations sur le déterminisme des fonctions, consultez [Fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="see-also"></a>Voir aussi
[Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)
  
  
