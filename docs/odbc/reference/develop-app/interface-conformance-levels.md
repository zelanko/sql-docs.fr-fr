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
ms.openlocfilehash: 185e68ed8d083e3ccfbab99369f6a778766a4c09
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138911"
---
# <a name="interface-conformance-levels"></a>Niveaux de conformité de l’interface
L’objectif de l’audit est d’informer l’application des fonctionnalités qui lui sont disponibles à partir du pilote. Un schéma de nivellement basé sur des fonctions n’atteint pas suffisamment cet objectif. Dans ODBC 3. *x*, les pilotes sont classés en fonction des fonctionnalités qu’ils possèdent. La prise en charge de la fonctionnalité peut inclure la prise en charge de la fonction. Il peut également inclure la prise en charge d’un champ de descripteur, d’un attribut d’instruction, d’une valeur « Y » pour un type d’informations retourné par **SQLGetInfo**, et ainsi de suite.  
  
 Pour simplifier la spécification de la conformité de l’interface, ODBC définit trois niveaux de conformité. Pour atteindre un niveau de conformité particulier, un pilote doit satisfaire à toutes les exigences de ce niveau de conformité. La conformité avec un niveau donné implique une conformité complète avec tous les niveaux inférieurs.  
  
 Les niveaux de conformité ne se divisent pas toujours clairement en prise en charge d’une liste spécifique de fonctions ODBC, mais spécifient les fonctionnalités prises en charge, comme indiqué dans les sections suivantes. Pour assurer la prise en charge d’une fonctionnalité, un pilote doit prendre en charge une partie ou l’ensemble des types d’appels à certaines fonctions ODBC (pour plus d’informations, consultez [conformité](../../../odbc/reference/develop-app/function-conformance.md)aux fonctions), définir certains attributs (voir [conformité aux attributs](../../../odbc/reference/develop-app/attribute-conformance.md)) et certains champs de descripteur (voir conformité au [champ du descripteur](../../../odbc/reference/develop-app/descriptor-field-conformance.md)).  
  
 L’application Découvre le niveau de conformité de l’interface d’un pilote en se connectant à une source de données et en appelant **SQLGetInfo** avec l’option SQL_ODBC_INTERFACE_CONFORMANCE.  
  
 Les pilotes sont libres d’implémenter des fonctionnalités au-delà du niveau auquel ils revendiquent une conformité complète. Les applications découvrent ces fonctionnalités supplémentaires en appelant **SQLGetFunctions** (pour déterminer quelles fonctions ODBC sont présentes) et **SQLGetInfo** (pour interroger diverses autres fonctionnalités ODBC).  
  
 Il existe trois niveaux de conformité de l’interface ODBC : Core, Level 1 et Level 2.  
  
> [!NOTE]
>  Ces niveaux de conformité ont des exigences différentes de celles des niveaux de conformité de l’API ODBC du même nom dans ODBC 2 *. x*. En particulier, toutes les fonctionnalités impliquées par le niveau 1 de conformité de l’API ODBC 2 *. x* font désormais partie du niveau de conformité de l’interface de base. Par conséquent, de nombreux pilotes ODBC peuvent signaler la conformité de l’interface au niveau du noyau.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Conformité de l’interface principale](../../../odbc/reference/develop-app/core-interface-conformance.md)  
  
-   [Conformité de l’interface - niveau 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md)  
  
-   [Conformité de l’interface - niveau 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md)  
  
-   [Conformité des fonctions](../../../odbc/reference/develop-app/function-conformance.md)  
  
-   [Conformité des attributs](../../../odbc/reference/develop-app/attribute-conformance.md)  
  
-   [Conformité des champs de descripteur](../../../odbc/reference/develop-app/descriptor-field-conformance.md)
