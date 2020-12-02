---
description: COL_LENGTH (Transact-SQL)
title: COL_LENGTH (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COL_LENGTH
- COL_LENGTH_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- lengths [SQL Server], columns
- COL_LENGTH function
- column properties [SQL Server]
- column length [SQL Server]
ms.assetid: cf891206-c49f-40eb-858e-eefd2b638a33
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 862e7aa70a3d26f5555c5f809d5fb24137de1a40
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96128542"
---
# <a name="col_length-transact-sql"></a>COL_LENGTH (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Cette fonction retourne la longueur définie d’une colonne en octets.
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
COL_LENGTH ( 'table' , 'column' )   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
**'** *table* **'**  
Nom de la table dont les informations de longueur de colonne doivent être déterminées. *table* est une expression de type **nvarchar**.
  
**'** *column* **'**  
Nom de la colonne dont nous voulons déterminer la longueur. *column* est une expression de type **nvarchar**.
  
## <a name="return-type"></a>Type de retour
**smallint**
  
## <a name="exceptions"></a>Exceptions  
Retourne NULL en cas d’erreur ou si un appelant ne dispose pas de l’autorisation appropriée pour voir l’objet.
  
Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un utilisateur peut seulement voir les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d’un droit d’accès. Cela signifie que les fonctions intégrées générant des métadonnées, comme COL_LENGTH, peuvent retourner NULL si l’utilisateur ne dispose pas de l’autorisation appropriée sur l’objet. Pour plus d’informations, consultez [Configuration de la visibilité des métadonnées](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Notes  
Pour les colonnes **varchar** déclarées avec le spécificateur **max** (**varchar(max)**), COL_LENGTH retourne la valeur -1.
  
## <a name="examples"></a>Exemples  
L’exemple suivant montre les valeurs retournées pour une colonne de type `varchar(40)` et pour une colonne de type `nvarchar(40)` :
  
```sql
USE AdventureWorks2012;  
GO  
CREATE TABLE t1(c1 VARCHAR(40), c2 NVARCHAR(40) );  
GO  
SELECT COL_LENGTH('t1','c1')AS 'VarChar',  
      COL_LENGTH('t1','c2')AS 'NVarChar';  
GO  
DROP TABLE t1;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
VarChar     NVarChar  
40          80  
```  
  
## <a name="see-also"></a>Voir aussi
[Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[COL_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/col-name-transact-sql.md)  
[COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)
  
  
