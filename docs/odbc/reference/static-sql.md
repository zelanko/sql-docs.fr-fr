---
title: SQL statique | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 392cf843734bcc668c88f6408227b20df97d43ae
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="static-sql"></a>SQL statique
Embedded SQL illustré [Embedded SQL exemple](../../odbc/reference/embedded-sql-example.md) SQL statique est appelée. Il est appelé SQL statique, car les instructions SQL dans le programme sont statiques ; Autrement dit, ils changent chaque fois que le programme est exécuté. Comme décrit dans la section précédente, ces instructions sont compilées lors de la compilation du reste du programme.  
  
 SQL statique fonctionne dans de nombreuses situations et peut être utilisé dans n’importe quelle application pour laquelle l’accès aux données peut être déterminée au moment du design programme. Par exemple, un programme de saisie de commandes utilise toujours la même instruction pour insérer une nouvelle commande et un système de réservation des compagnies aériennes utilise toujours la même instruction pour modifier l’état d’un siège disponibles pour réservé. Chacune de ces instructions est généralisé via l’utilisation de variables d’hôte ; des valeurs différentes peuvent être insérés dans une commande client, et sièges différents peuvent être réservées. Étant donné que ces instructions peuvent être codées en dur dans le programme, ces programmes présentent l’avantage que les instructions doivent être analysée, validé et optimisé qu’une seule fois, au moment de la compilation. Cela entraîne un code relativement rapide.
