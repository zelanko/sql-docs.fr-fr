---
title: Les niveaux de conformité SQL | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: c2e8ce5aeeb94a4f7a33b22054adc8067e0654ac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47605947"
---
# <a name="sql-conformance-levels"></a>Niveaux de conformité SQL
Niveau de la grammaire SQL-92 pris en charge par un pilote est indiqué par la valeur retournée par un appel à **SQLGetInfo** avec le type d’information SQL_SQL_CONFORMANCE. Cela indique si le pilote est conforme aux niveaux d’entrée, FIPS transitoires, intermédiaire ou intégral définis dans SQL-92.  
  
 Tous les pilotes ODBC doivent prendre en charge la grammaire SQL minimale décrite dans [grammaire minimale SQL](../../../odbc/reference/appendixes/sql-minimum-grammar.md) dans l’annexe c : SQL grammaire. Cette syntaxe est un sous-ensemble du niveau d’entrée de SQL-92. Pilotes peuvent prendre en charge SQL supplémentaire et être conforme au niveau d’entrée SQL-92, intermédiaire ou intégral ou à la norme FIPS 127-2 de niveau transitoire. Les pilotes qui sont conformes à un niveau donné de SQL-92 ou de la norme FIPS 127-2 peuvent prendre en charge des fonctionnalités supplémentaires dans un des niveaux plus élevés mais non d’entièrement conforme à ce niveau. Pour déterminer si une fonctionnalité est prise en charge, une application doit appeler **SQLGetInfo** avec le type d’informations. Le niveau de conformité d’une fonctionnalité SQL est décrite dans le type d’information. (Consultez le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) description de fonction.)
