---
title: Niveaux de conformité SQL Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 3529df2c-a09b-4c16-9c60-eae7a06d903a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 875330ac78588566b4b1c212f7a65d2841127a61
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301380"
---
# <a name="sql-conformance-levels"></a>Niveaux de conformité SQL
Le niveau de grammaire SQL-92 supporté par un conducteur est indiqué par la valeur retournée par un appel à **SQLGetInfo** avec le type d’information SQL_SQL_CONFORMANCE. Cela indique si le conducteur est conforme aux niveaux d’entrée, de transition FIPS, intermédiaires ou complets définis dans SQL-92.  
  
 Tous les conducteurs de l’ODBC doivent supporter la grammaire minimale SQL décrite dans [SQL Minimum Grammar](../../../odbc/reference/appendixes/sql-minimum-grammar.md) à l’Annexe C : SQL Grammar. Cette grammaire est un sous-ensemble du niveau d’entrée de SQL-92. Les conducteurs peuvent prendre en charge sqL supplémentaire et être conformes à l’entrée SQL-92, niveau intermédiaire ou complet, ou au niveau de transition FIPS 127-2. Les conducteurs qui se conforment à un niveau donné de SQL-92 ou FIPS 127-2 peuvent prendre en charge des caractéristiques supplémentaires dans l’un des niveaux les plus élevés mais ne pas être entièrement conformes à ce niveau. Pour déterminer si une fonctionnalité est prise en charge, une application doit appeler **SQLGetInfo** avec le type d’information approprié. Le niveau de conformité d’une fonction SQL est décrit dans le type d’information correspondant. (Voir la description de la fonction [SQLGetInfo.)](../../../odbc/reference/syntax/sqlgetinfo-function.md)
