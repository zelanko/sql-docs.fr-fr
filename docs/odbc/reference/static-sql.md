---
title: SQL statique - France Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81279901"
---
# <a name="static-sql"></a>SQL statique
Le SQL intégré indiqué dans [Embedded SQL Exemple](../../odbc/reference/embedded-sql-example.md) est connu sous le nom de SQL statique. Il est appelé SQL statique parce que les déclarations SQL dans le programme sont statiques; c’est-à-dire qu’ils ne changent pas chaque fois que le programme est exécuté. Comme décrit dans la section précédente, ces énoncés sont compilés lorsque le reste du programme est compilé.  
  
 La SQL statique fonctionne bien dans de nombreuses situations et peut être utilisée dans n’importe quelle application pour laquelle l’accès aux données peut être déterminé au moment de la conception du programme. Par exemple, un programme d’entrée de commande utilise toujours la même instruction pour insérer une nouvelle commande, et un système de réservation de compagnie aérienne utilise toujours la même instruction pour changer l’état d’un siège d’disponible à réservé. Chacune de ces déclarations serait généralisée par l’utilisation de variables d’hôte; différentes valeurs peuvent être insérées dans un ordre de vente, et différents sièges peuvent être réservés. Étant donné que ces énoncés peuvent être codés en dur dans le programme, ces programmes ont l’avantage que les énoncés doivent être analysés, validés et optimisés une seule fois, au moment de la compilation. Il en résulte un code relativement rapide.
