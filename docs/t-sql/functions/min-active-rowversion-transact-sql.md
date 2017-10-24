---
title: MIN_ACTIVE_ROWVERSION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MIN_ACTIVE_ROWVERSION
- MIN_ACTIVE_ROWVERSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MIN_ACTIVE_ROWVERSION function [Transact-SQL]
ms.assetid: 87c89547-8ea1-4820-b75e-36be683e4e10
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ed1254e0e35aa108d9866f30da49962b886a39ae
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="minactiverowversion-transact-sql"></a>MIN_ACTIVE_ROWVERSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la valeur **rowversion** active la plus basse dans la base de données active. Une valeur **rowversion** est active si elle est utilisée dans une transaction qui n'a pas encore été validée. Pour plus d’informations, consultez [rowversion &#40; Transact-SQL &#41; ](../../t-sql/data-types/rowversion-transact-sql.md).  
  
> [!NOTE]  
>  Le **rowversion** type de données est également appelé **timestamp**.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MIN_ACTIVE_ROWVERSION  
```  
  
## <a name="return-types"></a>Types de retour  
 Retourne un **Binary (8)** valeur.  
  
## <a name="remarks"></a>Notes  
 MIN_ACTIVE_ROWVERSION est une fonction non déterministe qui retourne l’active la plus basse **rowversion** valeur dans la base de données actuelle. Une nouvelle valeur **rowversion** est générée en règle générale lorsqu'une insertion ou une mise à jour est effectuée sur une table qui contient une colonne de type **rowversion**. S’il n’y a pas de valeurs actives dans la base de données, MIN_ACTIVE_ROWVERSION retourne la même valeur que @@DBTS + 1.  
  
 MIN_ACTIVE_ROWVERSION est utile pour les scénarios tels que la synchronisation des données qui utilisent **rowversion** valeurs à des ensembles de modifications. Si une application utilise@DBTS au lieu de MIN_ACTIVE_ROWVERSION, il est possible d’absence dans les modifications qui sont actives lors de la synchronisation se produit.  
  
 La fonction MIN_ACTIVE_ROWVERSION n'est pas affectée par les modifications apportées aux niveaux d'isolation des transactions.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant renvoie **rowversion** valeurs à l’aide de `MIN_ACTIVE_ROWVERSION` et `@@DBTS`. Notez que les valeurs diffèrent lorsqu'il n'y a pas de transactions actives dans la base de données.  
  
```  
-- Create a table that has a ROWVERSION column in it.  
CREATE TABLE RowVersionTestTable (rv ROWVERSION)  
GO  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()   
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E2  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E3  
  
-- Insert a row.  
INSERT INTO RowVersionTestTable VALUES (DEFAULT)  
SELECT * FROM RowVersionTestTable  
GO  
---------------- Results ----------------  
--rv  
--0x00000000000007E3  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()  
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E3  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E4  
  
-- Insert a new row inside a transaction but do not commit.  
BEGIN TRAN  
INSERT INTO RowVersionTestTable VALUES (DEFAULT)  
SELECT * FROM RowVersionTestTable  
GO  
---------------- Results ----------------  
--rv  
--0x00000000000007E3  
--0x00000000000007E4  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()   
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E4  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E4  
  
-- Commit the transaction.  
COMMIT  
GO  
  
-- Print the current values for the database.  
PRINT ''  
PRINT 'DBTS'  
PRINT @@DBTS  
PRINT 'MIN_ACTIVE_ROWVERSION'  
PRINT MIN_ACTIVE_ROWVERSION()  
GO  
---------------- Results ----------------  
--DBTS  
--0x00000000000007E4  
--MIN_ACTIVE_ROWVERSION  
--0x00000000000007E5  
```  
  
## <a name="see-also"></a>Voir aussi  
 [@@DBTS &#40;Transact-SQL&#41;](../../t-sql/functions/dbts-transact-sql.md)   
 [rowversion &#40;Transact-SQL&#41;](../../t-sql/data-types/rowversion-transact-sql.md)  
  
  

