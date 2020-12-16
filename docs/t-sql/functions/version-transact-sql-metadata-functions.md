---
description: Version - Fonctions de métadonnées Transact SQL
title: VERSION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
author: julieMSFT
ms.author: jrasnick
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: 164c05d3a8d78ad296af31bcbcbf797c0c77e56b
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97421374"
---
# <a name="version---transact-sql-metadata-functions"></a>Version - Fonctions de métadonnées Transact SQL
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

 Retourne la version de [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou de [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] actuellement exécutée sur l’appliance.  
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
-- Azure Synapse Analytics and Parallel Data Warehouse  
VERSION ( )  
```  
  
## <a name="arguments"></a>Arguments  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
Vous devez spécifier un nom de table dans une clause [FROM](../../t-sql/queries/from-transact-sql.md) pour que cette fonction retourne des résultats. Une ligne de résultats est retournée pour chaque ligne du jeu de résultats de la requête. Utilisez [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md) pour limiter le nombre de lignes retournées.  
  
## <a name="examples"></a>Exemples  
L’exemple suivant retourne le numéro de version.  
  
```sql
SELECT VERSION();  
```  
  
## <a name="see-also"></a>Voir aussi 
[SESSION_ID (Transact-SQL)](../../t-sql/functions/session-id-transact-sql.md)  
[DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)  
  
  
