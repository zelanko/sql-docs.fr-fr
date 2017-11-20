---
title: "Prise en charge de Type de données | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 147e940dcd37b452e1fe05b3a39f6b184c810397
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="data-type-support"></a>Prise en charge du type de données
ODBC (pilotes) doivent prendre en charge au moins un des SQL_CHAR et SQL_VARCHAR. Prise en charge d’autres types de données est déterminée par le niveau de conformité de la source données ou du pilote SQL-92. Une application doit appeler **SQLGetTypeInfo** pour déterminer les types de données pris en charge par le pilote.  
  
 Pour plus d’informations sur les types de données, consultez [annexe d : les Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md).

