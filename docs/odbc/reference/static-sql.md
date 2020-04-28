---
title: SQL statique | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55710d8ea734cba86ae5e4daa725f75e94e65a64
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81279901"
---
# <a name="static-sql"></a>SQL statique
L’exemple de SQL incorporé dans [Embedded](../../odbc/reference/embedded-sql-example.md) SQL est connu sous le nom de SQL statique. Elle est appelée SQL statique, car les instructions SQL du programme sont statiques ; autrement dit, ils ne changent pas chaque fois que le programme est exécuté. Comme décrit dans la section précédente, ces instructions sont compilées lors de la compilation du reste du programme.  
  
 Le SQL statique fonctionne correctement dans de nombreuses situations et peut être utilisé dans n’importe quelle application pour laquelle l’accès aux données peut être déterminé au moment de la conception du programme. Par exemple, un programme de saisie de commande utilise toujours la même instruction pour insérer une nouvelle commande, et un système de réservation d’une compagnie aérienne utilise toujours la même instruction pour modifier l’état d’un siège de disponible à réservé. Chacune de ces instructions est généralisée par le biais de l’utilisation de variables hôtes. différentes valeurs peuvent être insérées dans une commande client et des sièges différents peuvent être réservés. Comme ces instructions peuvent être codées en dur dans le programme, ces programmes ont l’avantage que les instructions doivent être analysées, validées et optimisées une seule fois, au moment de la compilation. Cela entraîne un code relativement rapide.
