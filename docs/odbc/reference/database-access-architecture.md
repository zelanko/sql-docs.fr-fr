---
title: Architecture d’accès de base de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- standardizing database access [ODBC], about standardizing
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC]
ms.assetid: 3811599f-48cb-4205-9fe5-5ab4b240047d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 42fc1d3880e01c435e7991fb5781d0f815a83db5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47612288"
---
# <a name="database-access-architecture"></a>Architecture de l’accès aux bases de données
L’une des questions dans le développement d’ODBC a été quelle partie de l’architecture d’accès de base de données afin de normaliser. Le code SQL décrits dans la section précédente des interfaces de programmation — embedded SQL, SQL modules et CLI — sont uniquement une partie de cette architecture. En fait, étant donné que ODBC a été principalement destiné à se connecter les applications basées sur les ordinateur personnel et ses grands systèmes SGBD, comportait également un nombre de composants réseau, certains d'entre eux peuvent être normalisé.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Accès aux bases de données de réseau](../../odbc/reference/network-database-access.md)  
  
-   [Architectures de l’accès aux bases de données standard](../../odbc/reference/standard-database-access-architectures.md)  
  
-   [La solution ODBC](../../odbc/reference/the-odbc-solution.md)
