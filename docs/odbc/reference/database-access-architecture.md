---
title: Architecture d’accès de base de données | Documents Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- standardizing database access [ODBC], about standardizing
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC]
ms.assetid: 3811599f-48cb-4205-9fe5-5ab4b240047d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 147841249b79ec1aab24941be533702443c72d6a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="database-access-architecture"></a>Architecture d’accès de base de données
L’une des questions dans le développement d’ODBC a été quelle partie de l’architecture d’accès de base de données afin de normaliser. Le SQL programming interfaces décrites dans la section précédente : embedded SQL, SQL modules et CLI, sont uniquement une partie de cette architecture. En fait, étant donné que ODBC a été principalement utilisée pour se connecter les applications basées sur les ordinateur personnel et ses macroordinateur SGBD, il ont également un nombre de composants réseau, certains d'entre eux peuvent être normalisé.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Accès aux bases de données de réseau](../../odbc/reference/network-database-access.md)  
  
-   [Architectures de l’accès aux bases de données standard](../../odbc/reference/standard-database-access-architectures.md)  
  
-   [La solution ODBC](../../odbc/reference/the-odbc-solution.md)
