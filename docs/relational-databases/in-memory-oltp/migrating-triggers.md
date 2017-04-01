---
title: "Migration de d&#233;clencheurs | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
caps.latest.revision: 13
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 13
---
# Migration de d&#233;clencheurs
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cette rubrique présente les déclencheurs DDL et les tables optimisées en mémoire.  
  
 Les déclencheurs DML sont pris en charge sur les tables optimisées en mémoire, mais uniquement avec l’événement déclencheur FOR | AFTER. Pour obtenir un exemple, consultez [Implémentation d’UPDATE avec FROM ou des sous-requêtes](../../relational-databases/in-memory-oltp/implementing-update-with-from-or-subqueries.md). 
  
 Les déclencheurs LOGON sont des déclencheurs définis pour se déclencher sur les événements LOGON. Ces déclencheurs n'affectent pas les tables mémoire optimisées.  
  
## Déclencheurs DDL  
 Les déclencheurs DDL sont des déclencheurs définis pour se déclencher lorsqu'une instruction CREATE, ALTER, DROP, GRANT, DENY, REVOKE ou UPDATE STATISTICS est exécutée sur la base de données ou sur le serveur sur lequel elle est définie.  
  
 Il est impossible de créer des tables mémoire optimisées si la base de données ou le serveur contient un ou plusieurs déclencheurs DDL définis sur l'événement CREATE_TABLE ou un groupe d'événements qui inclut cet événement. Il est impossible de supprimer une table mémoire optimisée si la base de données ou le serveur contient un ou plusieurs déclencheurs DDL définis sur l'événement DROP_TABLE ou un groupe d'événements qui inclut cet événement.  
  
 Il est impossible de créer des procédures stockées compilées en mode natif s'il existe un ou plusieurs déclencheurs DDL définis sur les événements CREATE_PROCEDURE, DROP_PROCEDURE ou un groupe d'événements qui inclut ces événements.  
  
## Voir aussi  
 [Migration vers OLTP en mémoire](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  