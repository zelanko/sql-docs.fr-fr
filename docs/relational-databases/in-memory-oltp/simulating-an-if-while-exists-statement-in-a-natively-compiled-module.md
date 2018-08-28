---
title: Simulation d’une instruction IF-WHILE EXISTS dans un module compilé en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3faef8fa02957cc2e05d336918f5f1b5651ac3bd
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43110890"
---
# <a name="simulating-an-if-while-exists-statement-in-a-natively-compiled-module"></a>Simulation d’une instruction IF-WHILE EXISTS dans un module compilé en mode natif
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Les procédures stockées compilées en mode natif ne gèrent pas la clause **EXISTS** dans les instructions conditionnelles du type IF ou WHILE.  
  
 L’exemple suivant illustre une solution de contournement qui utilise une variable BIT avec une instruction SELECT pour simuler une clause EXISTS :  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE …  
IF @exists = 1  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Problèmes de migration pour les procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Les constructions Transact-SQL ne sont pas prises en charge par l’OLTP en mémoire](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
