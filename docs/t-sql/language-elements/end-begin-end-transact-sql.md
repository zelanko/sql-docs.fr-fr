---
description: END (BEGIN...END) (Transact-SQL)
title: END (BEGIN...END) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- END
- END_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- enclosing statements [SQL Server]
- END keyword
- BEGIN...END keyword
- END (BEGIN...END) keyword
ms.assetid: 354c4935-1375-4141-8195-61326662f4d2
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eca6f1267084293f00e5e2b22eabf3a4a15d3c43
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97484041"
---
# <a name="end-beginend-transact-sql"></a>END (BEGIN...END) (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Renferme une série d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui seront exécutées comme un groupe. Les blocs BEGIN...END peuvent être imbriqués.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
BEGIN   
     { sql_statement | statement_block }   
END   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 { *sql_statement*| *statement_block*}  
 Toute instruction ou tout groupe d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] valide tel que défini dans un bloc d'instructions. Pour définir un bloc (traitement) d'instructions, utilisez les mots clé BEGIN et END du langage de contrôle de flux. Bien que toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] soient valides à l’intérieur d’un bloc BEGIN…END, certaines instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ne doivent pas être regroupées dans un même lot (bloc d’instructions).  
  
## <a name="result-types"></a>Types des résultats  
 **Booléen**  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Dans l’exemple suivant, `BEGIN` et `END` définissent une série d’instructions [!INCLUDE[DWsql](../../includes/dwsql-md.md)] qui s’exécutent ensemble. Si le bloc `BEGIN...END` n’est pas inclus, l’exemple suivant est dans une boucle continue.  
  
```sql  
-- Uses AdventureWorks  
  
DECLARE @Iteration INTEGER = 0  
WHILE @Iteration <10  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM dbo.DimCustomer WHERE LastName = 'Adams';  
SET @Iteration += 1  
END;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [BEGIN...END &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [Langage de contrôle de flux &#40;Transact-SQL&#41;](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [ELSE &#40;IF...ELSE&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/else-if-else-transact-sql.md)   
 [IF...ELSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/if-else-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  


