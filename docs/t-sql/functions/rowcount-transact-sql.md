---
title: '@@ROWCOUNT (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@ROWCOUNT_TSQL'
- '@@ROWCOUNT'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@ROWCOUNT function'
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 97a47998-81d9-4331-a244-9eb8b6fe4a56
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 411dc7eb628ddff52eb2f9426488e05860c9d279
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="x40x40rowcount-transact-sql"></a>& #x 40 ; & #x 40 ; Nombre de lignes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne le nombre de lignes affectées par la dernière instruction. Si le nombre de lignes est supérieur à 2 milliards, utilisez [ROWCOUNT_BIG](../../t-sql/functions/rowcount-big-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@@ROWCOUNT  
```  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]les instructions peuvent définir la valeur de @@ROWCOUNT comme suit :  
  
-   Set @@ROWCOUNT au nombre de lignes affectées ou lues. Les lignes peuvent être, ou ne pas être, envoyées au client.  
  
-   Conserver@ROWCOUNT à partir de l’exécution d’instruction précédente.  
  
-   Réinitialiser@ROWCOUNT à 0 mais ne retournent pas la valeur au client.  
  
 Instructions qui réalisent une affectation simple de toujours définir le @@ROWCOUNT valeur sur 1. Aucune ligne n'est envoyée au client. Parmi ces instructions figurent : SET @*local_variable*, RETURN, READTEXT, ainsi que sélection sans requête des instructions telles que SELECT GETDATE() ou SELECT **'***texte générique***'**.  
  
 Instructions qui réalisent une affectation dans une requête ou utilisent RETURN dans un ensemble de requêtes le @@ROWCOUNT valeur au nombre de lignes affectées ou lues par la requête, par exemple : SELECT @*local_variable* = c1 FROM t1.  
  
 Jeu de données manipulation language (DML) instructions le @@ROWCOUNT valeur au nombre de lignes affectées par la requête et retourne cette valeur au client. Les instructions DML peuvent ne pas envoyer de lignes au client.  
  
 DECLARE CURSOR et FETCH définir le @@ROWCOUNT valeur sur 1.  
  
 Les instructions EXECUTE conservent le @ précédente@ROWCOUNT.  
  
 Les instructions telles que l’utilisation, définissez \<option >, DEALLOCATE CURSOR, CLOSE CURSOR, BEGIN TRANSACTION ou COMMIT TRANSACTION réinitialisent la valeur ROWCOUNT à 0.  
  
 Les procédures stockées compilées en mode natif conservent précédent @@ROWCOUNT. [!INCLUDE[tsql](../../includes/tsql-md.md)]les instructions à l’intérieur des procédures stockées compilées en mode natif ne définissez pas@ROWCOUNT. Pour plus d’informations, consultez [Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant exécute une instruction `UPDATE` et utilise `@@ROWCOUNT` pour déterminer si des lignes ont été modifiées.  
  
```  
USE AdventureWorks2012;  
GO  
UPDATE HumanResources.Employee   
SET JobTitle = N'Executive'  
WHERE NationalIDNumber = 123456789  
IF @@ROWCOUNT = 0  
PRINT 'Warning: No rows were updated';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [SET ROWCOUNT &#40; Transact-SQL &#41;](../../t-sql/statements/set-rowcount-transact-sql.md)  
  
  

