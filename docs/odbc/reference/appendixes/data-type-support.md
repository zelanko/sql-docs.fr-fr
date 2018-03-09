---
title: "Prise en charge de Type de données | Documents Microsoft"
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
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4885db2868e5baf301264d2b29a18831d02dcf26
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="data-type-support"></a>Prise en charge du type de données
ODBC (pilotes) doivent prendre en charge au moins un des SQL_CHAR et SQL_VARCHAR. Prise en charge d’autres types de données est déterminée par le niveau de conformité de la source données ou du pilote SQL-92. Une application doit appeler **SQLGetTypeInfo** pour déterminer les types de données pris en charge par le pilote.  
  
 Pour plus d’informations sur les types de données, consultez [annexe d : les Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).
