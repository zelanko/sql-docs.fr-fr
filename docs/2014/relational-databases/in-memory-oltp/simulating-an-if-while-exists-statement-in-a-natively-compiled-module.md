---
title: Simulation d’une clause EXISTs dans une procédure stockée compilée en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac041e19aeb5948a644a9fcf82b3e687472b7259
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "62468292"
---
# <a name="simulating-an-exists-clause-in-a-natively-compiled-stored-procedure"></a>Simulation d'une clause EXISTS dans une procédure stockée compilée en mode natif
  Les procédures stockées compilées en mode natif ne prennent pas en charge la clause `EXISTS`, mais il existe une solution :  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de migration pour les procédures stockées compilées en mode natif](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Constructions Transact-SQL non prises en charge par l’OLTP en mémoire](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
