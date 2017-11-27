---
title: curseur (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: cursor data type
ms.assetid: fbea16ef-f2cc-4734-9149-ec2598fd3cca
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b9fa1c8e8fea6aabf8fe8a0e6e84f82f7220facf
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cursor-transact-sql"></a>cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Type de données pour les variables ou les paramètres OUTPUT des procédures stockées contenant une référence à un curseur.
  
## <a name="remarks"></a>Notes  
Les opérations qui peuvent référencer des variables et des paramètres ayant un **curseur** sont de type de données :
-   DECLARE  *@local_variable*  et  *@local_variable*  instructions.  
-   les instructions de curseur OPEN, FETCH, CLOSE et DEALLOCATE ;  
-   les paramètres de sortie des procédures stockées ;  
-   la fonction CURSOR_STATUS ;  
-   Le **sp_cursor_list**, **sp_describe_cursor**, **sp_describe_cursor_tables**, et **sp_describe_cursor_columns** procédures stockées système.  
  
Le **cursor_name** colonne de sortie de **sp_cursor_list** et **sp_describe_cursor** retourne le nom de la variable de curseur.
  
Toutes les variables créées avec la **curseur** type de données sont nullables.
  
Le **curseur** type de données ne peut pas être utilisé pour une colonne dans une instruction CREATE TABLE.
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CURSOR_STATUS &#40; Transact-SQL &#41;](../../t-sql/functions/cursor-status-transact-sql.md)  
[Conversion de Type de données &#40; moteur de base de données &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Déclarez le curseur &#40; Transact-SQL &#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
