---
title: "Migration de déclencheurs | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a2f151fa00c2e92ef1509ea2c6d7d93e8c8d2c69
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2018
---
# <a name="migrating-triggers"></a>Migration de déclencheurs
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Cette rubrique présente les déclencheurs DDL et les tables optimisées en mémoire.  
  
 Les déclencheurs DML sont pris en charge sur les tables optimisées en mémoire, mais uniquement avec l’événement déclencheur FOR | AFTER. Pour obtenir un exemple, consultez [Implémentation d’UPDATE avec FROM ou des sous-requêtes](../../relational-databases/in-memory-oltp/implementing-update-with-from-or-subqueries.md). 
  
 Les déclencheurs LOGON sont des déclencheurs définis pour se déclencher sur les événements LOGON. Ces déclencheurs n'affectent pas les tables mémoire optimisées.  
  
## <a name="ddl-triggers"></a>Déclencheurs DDL  
 Les déclencheurs DDL sont des déclencheurs définis pour se déclencher lorsqu'une instruction CREATE, ALTER, DROP, GRANT, DENY, REVOKE ou UPDATE STATISTICS est exécutée sur la base de données ou sur le serveur sur lequel elle est définie.  
  
 Il est impossible de créer des tables mémoire optimisées si la base de données ou le serveur contient un ou plusieurs déclencheurs DDL définis sur l'événement CREATE_TABLE ou un groupe d'événements qui inclut cet événement. Il est impossible de supprimer une table mémoire optimisée si la base de données ou le serveur contient un ou plusieurs déclencheurs DDL définis sur l'événement DROP_TABLE ou un groupe d'événements qui inclut cet événement.  
  
 Il est impossible de créer des procédures stockées compilées en mode natif s'il existe un ou plusieurs déclencheurs DDL définis sur les événements CREATE_PROCEDURE, DROP_PROCEDURE ou un groupe d'événements qui inclut ces événements.  
  
## <a name="see-also"></a> Voir aussi  
 [Migration vers OLTP en mémoire](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
