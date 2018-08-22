---
title: Prise en charge des constructions sur les procédures stockées compilées en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6a118b8d9dfe69f5890c9c66e71c2319a6a27a1
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396318"
---
# <a name="supported-constructs-on-natively-compiled-stored-procedures"></a>Constructions prises en charge dans les procédures stockées compilées en mode natif
  Cette rubrique répertorie les constructions prises en charge dans les procédures stockées compilées en mode natif.  
  
 Pour plus d’informations sur les constructions non prises en charge, consultez [Constructions Transact-SQL non prises en charge par l’OLTP en mémoire](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
## <a name="procedure-ddl"></a>Procédure DDL  
 Les constructions suivantes sont admises :  
  
-   CREATE PROCEDURE  
  
-   DROP PROCEDURE  
  
-   SCHEMABINDING (requis pour les procédures stockées compilées en mode natif)  
  
-   NATIVE_COMPILATION  
  
-   Les paramètres peuvent être déclarés NOT NULL.  
  
-   Paramètres table.  
  
## <a name="security"></a>Sécurité  
 Les constructions suivantes sont admises :  
  
-   Pour les procédures : EXECUTE AS OWNER, SELF, et utilisateur.  
  
-   GRANT (accorder) et DENY (refuser) des autorisations sur les tables et les procédures.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md)  
  
  
