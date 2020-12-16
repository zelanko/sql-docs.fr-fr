---
description: ISJSON (Transact-SQL)
title: ISJSON (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/03/2020
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ISJSON
- ISJSON_TSQL
helpviewer_keywords:
- ISJSON function
- JSON, validating
ms.assetid: c836f3d3-3e17-44ae-92bf-f341918896c3
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
monikerRange: = azuresqldb-current||= azure-sqldw-latest||>= sql-server-2016||>= sql-server-linux-2017
ms.openlocfilehash: 49d1bcd94ed12e0b9bb22e63018b0867f680dd41
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97464300"
---
# <a name="isjson-transact-sql"></a>ISJSON (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Teste si une chaîne contient des données JSON valides.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql  
ISJSON ( expression )  
```  
  
## <a name="arguments"></a>Arguments
 *expression*  
 Chaîne à tester.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Renvoie 1 si la chaîne contient des données JSON valides ; sinon, renvoie 0. Renvoie Null si *expression* est Null.  
  
 Ne renvoie pas d’erreurs.  
  
## <a name="remarks"></a>Remarques  
 **ISJSON** ne vérifie pas l’unicité des clés au même niveau.  
  
## <a name="examples"></a>Exemples  
  
### <a name="example-1"></a>Exemple 1  
L’exemple suivant exécute un bloc d’instructions de manière conditionnelle si la valeur de paramètre `@param` contient des données JSON valides.  
  
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
 [Données JSON &#40;SQL Server&#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  
