---
title: VERSION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1905ef3b0f31e91d6cec00c0314770b7686e8c51
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="version---transact-sql-metadata-functions"></a>Version - Transact des fonctions de métadonnées SQL
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

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
  
  

