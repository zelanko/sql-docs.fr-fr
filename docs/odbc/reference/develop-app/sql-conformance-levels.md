---
title: Niveaux de conformité SQL | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7862b2e3a86c6d98a51c73ecb470d59bcfe29dc9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107521"
---
# <a name="sql-conformance-levels"></a>Niveaux de conformité SQL
Le niveau de grammaire SQL-92 pris en charge par un pilote est indiqué par la valeur retournée par un appel à **SQLGetInfo** avec le type d’informations SQL_SQL_CONFORMANCE. Cela indique si le pilote est conforme aux niveaux d’entrée, de transition FIPS, intermédiaire ou complète définis dans SQL-92.  
  
 Tous les pilotes ODBC doivent prendre en charge la grammaire SQL minimale décrite dans [grammaire minimale SQL](../../../odbc/reference/appendixes/sql-minimum-grammar.md) dans annexe C : grammaire SQL. Cette grammaire est un sous-ensemble du niveau d’entrée de SQL-92. Les pilotes peuvent prendre en charge des SQL supplémentaires et être conformes à l’entrée SQL-92, au niveau intermédiaire ou complet, ou au niveau de transition FIPS 127-2. Les pilotes qui se conforment à un niveau donné de SQL-92 ou FIPS 127-2 peuvent prendre en charge des fonctionnalités supplémentaires dans n’importe quel niveau supérieur, mais ne sont pas entièrement conformes à ce niveau. Pour déterminer si une fonctionnalité est prise en charge, une application doit appeler **SQLGetInfo** avec le type d’informations approprié. Le niveau de conformité d’une fonctionnalité SQL est décrit dans le type d’informations correspondant. (Consultez la description de la fonction [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .)
