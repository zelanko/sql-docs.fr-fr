---
title: Implémentation de la fonctionnalité de fusion | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e762c1999a4206d5277050934e82b5d5d5c59371
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82715126"
---
# <a name="implementing-merge-functionality"></a>Implémentation de la fonctionnalité MERGE
  Une base de données devra peut-être effectuer l'insertion d'une mise à jour, selon qu'une ligne particulière existe déjà ou non dans la base de données.  
  
 Sans utiliser l'instruction `MERGE`, voici une approche que vous pouvez utiliser dans [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
```sql  
UPDATE mytable SET col=@somevalue WHERE myPK = @parm  
IF @@ROWCOUNT = 0  
    INSERT mytable (columns) VALUES (@parm, @other values)  
```  
  
 Autre méthode [!INCLUDE[tsql](../../includes/tsql-md.md)] pour implémenter une fusion :  
  
```sql  
IF EXISTS (SELECT 1 FROM mytable WHERE myPK = @parm)  
    UPDATE....  
ELSE  
    INSERT  
```  
  
 Pour une procédure stockée compilée en mode natif  
  
```sql  
DECLARE @i  int  = 0  -- or whatever your PK data type is  
UPDATE mytable SET @i=myPK, othercolums = other values WHERE myPK = @parm  
IF @i = 0  
   INSERT....  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de migration pour les procédures stockées compilées en mode natif](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Constructions Transact-SQL non prises en charge par In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
