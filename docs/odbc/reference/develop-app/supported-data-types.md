---
title: Types de données pris en charge | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f5ec0f3943fd52540f094a23e9b3f9f3886e1371
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114077"
---
# <a name="supported-data-types"></a>Types de données pris en charge
Les types de données pris en charge par les SGBD varient considérablement. Une application peut déterminer les noms et les caractéristiques des types de données pris en charge en appelant **SQLGetTypeInfo**. En raison d’une grande variation dans les noms de types de données, l’application doit utiliser les noms de types de données retournés par **SQLGetTypeInfo** dans les instructions **Create table** . Pour plus d’informations, consultez [types de données dans ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
