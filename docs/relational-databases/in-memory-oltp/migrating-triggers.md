---
title: Migration de déclencheurs | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4629b9f18cdf0b97b5a79cff0696973cb60f7c36
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68050146"
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
  
## <a name="see-also"></a>Voir aussi  
 [Migration vers OLTP en mémoire](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
