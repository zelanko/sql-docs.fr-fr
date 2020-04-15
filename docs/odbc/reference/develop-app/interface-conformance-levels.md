---
title: Niveaux de conformité à l’interface (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fff555324746fcb92641126ddf11ea91ce5e3f89
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304599"
---
# <a name="interface-conformance-levels"></a>Niveaux de conformité de l’interface
Le but du nivellement est d’informer l’application des caractéristiques qui lui sont disponibles auprès du conducteur. Un système de nivellement basé sur les fonctions n’atteint pas suffisamment cet objectif. À ODBC 3. *x*, les pilotes sont classés en fonction des caractéristiques qu’ils possèdent. Soutenir la fonctionnalité peut inclure le soutien de la fonction; il peut également inclure le soutien d’un champ descripteur, un attribut de déclaration, une valeur « Y » pour un type d’information retourné par **SQLGetInfo**, et ainsi de suite.  
  
 Pour simplifier la spécification de la conformité à l’interface, ODBC définit trois niveaux de conformité. Pour répondre à un niveau de conformité particulier, un conducteur doit satisfaire à toutes les exigences de ce niveau de conformité. La conformité avec un niveau donné implique une conformité complète avec tous les niveaux inférieurs.  
  
 Les niveaux de conformité ne se divisent pas toujours parfaitement en support pour une liste spécifique des fonctions ODBC, mais spécifient les fonctionnalités prises en charge telles que énumérées dans les sections suivantes. Pour fournir un soutien à une fonctionnalité, un conducteur doit prendre en charge une partie ou toutes les formes d’appels à certaines fonctions ODBC (pour plus d’informations, voir [Conformité de fonction](../../../odbc/reference/develop-app/function-conformance.md)), définir certains attributs (voir Conformité [d’attribut](../../../odbc/reference/develop-app/attribute-conformance.md)), et certains champs descripteur (voir [Descriptor Field Conformance](../../../odbc/reference/develop-app/descriptor-field-conformance.md)).  
  
 L’application découvre le niveau de conformité à l’interface d’un conducteur en se connectant à une source de données et en appelant **SQLGetInfo** avec l’option SQL_ODBC_INTERFACE_CONFORMANCE.  
  
 Les conducteurs sont libres de mettre en œuvre des fonctionnalités au-delà du niveau auquel ils prétendent être conformes complets. Les applications découvrent de telles capacités supplémentaires en appelant **SQLGetFunctions** (pour déterminer quelles fonctions ODBC sont présentes) et **SQLGetInfo** (pour interroger diverses autres capacités ODBC).  
  
 Il existe trois niveaux de conformation d’interface ODBC : Core, Level 1 et Level 2.  
  
> [!NOTE]
>  Ces niveaux de conformité ont des exigences différentes de celles des niveaux de conformation de l’ODBC API du même nom dans ODBC 2 *.x*. En particulier, toutes les fonctionnalités sous-entendues par ODBC 2 *.x* API conformance Niveau 1 font maintenant partie du niveau de conformité de l’interface De base. Par conséquent, de nombreux pilotes ODBC peuvent signaler la conformité à l’interface au niveau central.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Conformité de l’interface principale](../../../odbc/reference/develop-app/core-interface-conformance.md)  
  
-   [Conformité de l’interface - niveau 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md)  
  
-   [Conformité de l’interface - niveau 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md)  
  
-   [Conformité des fonctions](../../../odbc/reference/develop-app/function-conformance.md)  
  
-   [Conformité des attributs](../../../odbc/reference/develop-app/attribute-conformance.md)  
  
-   [Conformité des champs de descripteur](../../../odbc/reference/develop-app/descriptor-field-conformance.md)
