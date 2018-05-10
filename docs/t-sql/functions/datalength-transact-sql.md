---
title: DATALENGTH (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATALENGTH_TSQL
- DATALENGTH
dev_langs:
- TSQL
helpviewer_keywords:
- number of bytes representing expression
- data types [SQL Server], length
- DATALENGTH function
- expressions [SQL Server], length
- lengths [SQL Server], data
ms.assetid: 00f377f1-cc3e-4eac-be47-b3e3f80267c9
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 346b5aada1a16e84aa3e74019e83dd7a74d9914a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="datalength-transact-sql"></a>DATALENGTH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne le nombre d'octets utilisés pour représenter une expression.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATALENGTH ( expression )   
```  
  
## <a name="arguments"></a>Arguments  
*expression*  
[Expression](../../t-sql/language-elements/expressions-transact-sql.md) de n’importe quel type de données.
  
## <a name="return-types"></a>Types de retour
**bigint** si *expression* est du type **varchar(max)**, **nvarchar(max)** ou **varbinary(max)**  ; sinon, **int**.
  
## <a name="remarks"></a>Notes   
DATALENGTH est particulièrement utile pour les types de données **varchar**, **varbinary**, **text**, **image**, **nvarchar** et **ntext**, car ces types de données permettent le stockage de données de longueur variable.
  
La fonction DATALENGTH exécutée sur la valeur NULL donne NULL comme résultat.
  
> [!NOTE]  
>  Les niveaux de compatibilité peuvent affecter les valeurs de retour. Pour plus d’informations sur les niveaux de compatibilité, consultez [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="examples"></a>Exemples  
L'exemple suivant recherche la longueur de la colonne `Name` dans la table `Product`.
  
```sql
-- Uses AdventureWorks  
  
SELECT length = DATALENGTH(EnglishProductName), EnglishProductName  
FROM dbo.DimProduct  
ORDER BY EnglishProductName;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[LEN &#40;Transact-SQL&#41;](../../t-sql/functions/len-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  

