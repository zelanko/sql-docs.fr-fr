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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d19cde2d531819a60229dd7a780181571e169503
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307780"
---
# <a name="supported-data-types"></a>Types de données pris en charge
Les types de données pris en charge par les SGBD varient considérablement. Une application peut déterminer les noms et les caractéristiques des types de données pris en charge en appelant **SQLGetTypeInfo**. En raison d’une grande variation dans les noms de types de données, l’application doit utiliser les noms de types de données retournés par **SQLGetTypeInfo** dans les instructions **Create table** . Pour plus d’informations, consultez [types de données dans ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
