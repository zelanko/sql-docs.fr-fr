---
title: Niveaux de conformité de l’interface | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 2c470e54-0600-4b2b-b1f3-9885cb28a01a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df78a4890658ec83a62eeccbce23d891d5afc56d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812101"
---
# <a name="interface-conformance-levels"></a>Niveaux de conformité de l’interface
L’objectif de l’audit consiste à informer l’application quelles fonctionnalités sont disponibles à ce dernier à partir du pilote. Un schéma audit basé sur les fonctions ne pas suffisamment à atteindre cet objectif. Dans ODBC 3. *x*, pilotes sont classées selon les fonctionnalités qu’ils possèdent. Prise en charge la fonctionnalité peut inclure la prise en charge de la fonction ; Il peut également inclure la prise en charge d’un champ de descripteur, un attribut d’instruction, une valeur « Y » pour un type d’informations retourné par **SQLGetInfo**, et ainsi de suite.  
  
 Pour simplifier la spécification de la conformité de l’interface, ODBC définit trois niveaux de conformité. Pour répondre à un niveau de conformité spécifique, un pilote doit satisfaire toutes les exigences de ce niveau de conformité. La mise en conformité avec un niveau donné implique la mise en conformité complète avec tous les niveaux inférieurs.  
  
 Niveaux de conformité ne pas toujours diviser clairement la prise en charge pour une liste spécifique de fonctions ODBC, mais spécifient les fonctionnalités prises en charge comme indiqué dans les sections suivantes. Pour prendre en charge une fonctionnalité, un pilote doit prendre en charge certains ou tous les formulaires d’appels à certaines fonctions ODBC (pour plus d’informations, consultez [fonction conformité](../../../odbc/reference/develop-app/function-conformance.md)), définissant certains attributs (voir [conformité des attributs ](../../../odbc/reference/develop-app/attribute-conformance.md)) et certains champs de descripteur (consultez [conformité des champs de descripteur](../../../odbc/reference/develop-app/descriptor-field-conformance.md)).  
  
 L’application détecte un niveau de conformité d’interface d’un pilote en se connectant à une source de données et en appelant **SQLGetInfo** avec l’option SQL_ODBC_INTERFACE_CONFORMANCE.  
  
 Pilotes sont libres d’implémenter des fonctionnalités au-delà du niveau auquel ils prétendent la mise en conformité complète. Applications découvrir toutes ces fonctionnalités supplémentaires en appelant **SQLGetFunctions** (pour déterminer quelles fonctions ODBC sont présentes) et **SQLGetInfo** (pour différentes autres fonctionnalités ODBC de la requête).  
  
 Il existe trois niveaux de conformité d’interface ODBC : Core, niveau 1 et niveau 2.  
  
> [!NOTE]  
>  Ces niveaux de conformité des exigences différentes que les niveaux de conformité ODBC API du même nom dans ODBC 2 *.x*. En particulier, toutes les fonctionnalités implicitement par ODBC 2 *.x* conformité API niveau 1 font désormais partie du niveau de la conformité de l’interface Core. Par conséquent, de nombreux pilotes ODBC peuvent signaler de conformité de l’interface au niveau du noyau.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Conformité de l’interface principale](../../../odbc/reference/develop-app/core-interface-conformance.md)  
  
-   [Conformité de l’interface - niveau 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md)  
  
-   [Conformité de l’interface - niveau 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md)  
  
-   [Conformité des fonctions](../../../odbc/reference/develop-app/function-conformance.md)  
  
-   [Conformité des attributs](../../../odbc/reference/develop-app/attribute-conformance.md)  
  
-   [Conformité des champs de descripteur](../../../odbc/reference/develop-app/descriptor-field-conformance.md)
