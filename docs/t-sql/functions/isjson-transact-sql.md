---
title: ISJSON (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISJSON
- ISJSON_TSQL
helpviewer_keywords:
- ISJSON function
- JSON, validating
ms.assetid: c836f3d3-3e17-44ae-92bf-f341918896c3
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b641847387801097bce59e78cf75255cc7217be
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="isjson-transact-sql"></a>ISJSON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Teste si une chaîne contient un JSON valide.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
ISJSON ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Chaîne à tester.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne 1 si la chaîne contient un JSON valide ; Sinon, retourne 0. Retourne null si *expression* est null.  
  
 Ne retourne pas d’erreurs.  
  
## <a name="remarks"></a>Notes  
 **ISJSON** ne vérifie pas l’unicité des clés au même niveau.  
  
## <a name="examples"></a>Exemples  
  
### <a name="example-1"></a>Exemple 1  
L’exemple suivant exécute un bloc d’instructions de manière conditionnelle Si la valeur du paramètre `@param` contient un JSON valide.  
  
```sql  
DECLARE @param <data type>
SET @param = <value>

IF (ISJSON(@param) > 0)  
BEGIN  
     -- Do something with the valid JSON value of @param.  
END
 
```  
  
### <a name="example-2"></a>Exemple 2  
L’exemple suivant retourne des lignes dans lesquelles la colonne `json_col` contient un JSON valide.  
  
```sql  
SELECT id, json_col
FROM tab1
WHERE ISJSON(json_col) > 0 
```  
  
## <a name="see-also"></a>Voir aussi  
 [Données JSON &#40; SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  

