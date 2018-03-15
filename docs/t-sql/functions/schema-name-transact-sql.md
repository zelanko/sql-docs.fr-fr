---
title: SCHEMA_NAME (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SCHEMA_NAME
- SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SCHEMA_NAME function
- schemas [SQL Server], names
ms.assetid: 20071b77-2b6e-4ce7-a8e3-fa71480baf73
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 41dd04ebbbc5b07512d243e5d4ac77761ba9ca1e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="schemaname-transact-sql"></a>SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne le nom de schéma associé à un ID de schéma.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SCHEMA_NAME ( [ schema_id ] )  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|----------|----------------|  
|*schema_id*|Identificateur du schéma. *schema_id* est de type **int**. Si *schema_id* n’est pas défini, SCHEMA_NAME renvoie le nom du schéma par défaut de l’appelant.|  
  
## <a name="return-types"></a>Types de retour  
 **sysname**  
  
 Renvoie la valeur NULL lorsque *schema_id* n’est pas un ID valide.  
  
## <a name="remarks"></a>Notes   
 SCHEMA_NAME retourne des noms de schémas système et de schémas définis par l'utilisateur. Vous pouvez l'appeler dans une liste SELECT, dans une clause WHERE et partout où une expression est autorisée.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-the-name-of-the-default-schema-of-the-caller"></a>A. Obtention du nom du schéma par défaut de l'appelant  
  
```  
SELECT SCHEMA_NAME();  
```  
  
### <a name="b-returning-the-name-of-a-schema-by-using-an-id"></a>B. Obtention du nom d'un schéma d'après son ID  
  
```  
SELECT SCHEMA_NAME(1);  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SCHEMA_ID &#40;Transact-SQL&#41;](../../t-sql/functions/schema-id-transact-sql.md)   
 [sys.schemas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  

