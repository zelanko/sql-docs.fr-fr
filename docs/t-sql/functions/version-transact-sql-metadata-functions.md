---
title: VERSION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aa9dec84a07189eb3b2c6c9c3d9342db4eac1df6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="version---transact-sql-metadata-functions"></a>Version - Transact des fonctions de métadonnées SQL
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

 Retourne la version de [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] en cours d’exécution sur l’appareil.  
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
VERSION ( )  
```  
  
## <a name="arguments"></a>Arguments  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
Un nom de table doit être spécifié dans un [FROM](../../t-sql/queries/from-transact-sql.md) clause pour cette fonction retourner les résultats. Une ligne de résultats est retournée pour chaque ligne dans le jeu de résultats de la requête. Utilisez [haut (Transact-SQL)](../../t-sql/queries/top-transact-sql.md) pour limiter le nombre de lignes retournées.  
  
## <a name="examples"></a>Exemples  
L’exemple suivant retourne le numéro de version.  
  
```  
SELECT VERSION();  
```  
  
## <a name="see-also"></a>Voir aussi 
[SESSION_ID (Transact-SQL)](../../t-sql/functions/session-id-transact-sql.md)  
[Db_name &#40; Transact-SQL &#41;](../../t-sql/functions/db-name-transact-sql.md)  
  
  
