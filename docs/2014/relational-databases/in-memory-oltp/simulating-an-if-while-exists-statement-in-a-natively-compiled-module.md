---
title: Simulation d’une Clause EXISTS dans une procédure stockée compilée en mode natif | Microsoft Docs
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
ms.openlocfilehash: 6827f14702063765ccf64c8b70ba5088a8509ff1
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52510079"
---
# <a name="simulating-an-exists-clause-in-a-natively-compiled-stored-procedure"></a>Simulation d'une clause EXISTS dans une procédure stockée compilée en mode natif
  Les procédures stockées compilées en mode natif ne prennent pas en charge la clause `EXISTS`, mais il existe une solution :  
  
```tsql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE ...  
IF @exists = 1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de migration pour les procédures stockées compilées en mode natif](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Les constructions Transact-SQL ne sont pas prises en charge par l’OLTP en mémoire](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
