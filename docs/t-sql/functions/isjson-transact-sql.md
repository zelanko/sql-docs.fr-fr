---
title: ISJSON (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: genemi
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
monikerRange: = azuresqldb-current||= azure-sqldw-latest||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: 0d3060af2114f62c1c21b25e79abf4714acfbe4b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68109443"
---
# <a name="isjson-transact-sql"></a>ISJSON (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Teste si une chaîne contient des données JSON valides.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
ISJSON ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Chaîne à tester.  
  
## <a name="return-value"></a>Valeur de retour  
 Renvoie 1 si la chaîne contient des données JSON valides ; sinon, renvoie 0. Renvoie Null si *expression* est Null.  
  
 Ne renvoie pas d’erreurs.  
  
## <a name="remarks"></a>Notes  
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
  
  
