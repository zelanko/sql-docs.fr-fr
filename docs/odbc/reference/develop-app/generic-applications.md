---
title: "Applications génériques | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 471cceb31dfec36cde45185d3d472aba3100b4da
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="generic-applications"></a>Applications génériques
Applications génériques exécutent parfois une tâche codé en dur, par exemple un tableur la récupération des données à partir d’une base de données. Ils peuvent également effectuer diverses tâches définies par l’utilisateur, telle qu’une application de requêtes générique pour autoriser l’utilisateur à entrer et à exécuter une instruction SQL. Les applications génériques ont en commun est qu’ils doivent travailler avec un large éventail de SGBD différents et que le développeur ne sait pas au préalable ces SGBD sera.  
  
 Par conséquent, les applications génériques doivent être hautement interopérable. Le développeur doit rendre propose un vaste choix, en ajustant l’interopérabilité des fonctionnalités et doit écrire du code qui attend les pilotes pour prendre en charge un large éventail de fonctionnalités. Alors que les applications génériques peuvent être analysées pour fonctionner avec SGBD courants, qu’ils contiennent rarement code spécifique au pilote ou propres au SGBD.
