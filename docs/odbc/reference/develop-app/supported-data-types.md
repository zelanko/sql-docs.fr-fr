---
title: Types de données pris en charge | Documents Microsoft
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
ms.topic: article
helpviewer_keywords:
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bcac33a3e45509591f46d8e340712ae2f30b2f55
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="supported-data-types"></a>Types de données pris en charge
Les types de données pris en charge par le SGBD varient considérablement. Une application peut déterminer les noms et les caractéristiques des types de données pris en charge en appelant **SQLGetTypeInfo**. En raison des variations importantes dans les noms de types de données, l’application doit utiliser les noms de type de données retournés par **SQLGetTypeInfo** dans **CREATE TABLE** instructions. Pour plus d’informations, consultez [des Types de données dans ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
