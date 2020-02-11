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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e6d053e4d2a5520432c4c1debbafb35fdb17bc4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68016739"
---
# <a name="static-sql"></a>SQL statique
L’exemple de SQL incorporé dans [Embedded](../../odbc/reference/embedded-sql-example.md) SQL est connu sous le nom de SQL statique. Elle est appelée SQL statique, car les instructions SQL du programme sont statiques ; autrement dit, ils ne changent pas chaque fois que le programme est exécuté. Comme décrit dans la section précédente, ces instructions sont compilées lors de la compilation du reste du programme.  
  
 Le SQL statique fonctionne correctement dans de nombreuses situations et peut être utilisé dans n’importe quelle application pour laquelle l’accès aux données peut être déterminé au moment de la conception du programme. Par exemple, un programme de saisie de commande utilise toujours la même instruction pour insérer une nouvelle commande, et un système de réservation d’une compagnie aérienne utilise toujours la même instruction pour modifier l’état d’un siège de disponible à réservé. Chacune de ces instructions est généralisée par le biais de l’utilisation de variables hôtes. différentes valeurs peuvent être insérées dans une commande client et des sièges différents peuvent être réservés. Comme ces instructions peuvent être codées en dur dans le programme, ces programmes ont l’avantage que les instructions doivent être analysées, validées et optimisées une seule fois, au moment de la compilation. Cela entraîne un code relativement rapide.
