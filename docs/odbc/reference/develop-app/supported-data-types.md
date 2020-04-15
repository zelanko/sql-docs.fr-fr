---
title: Types de données pris en charge (en anglais seulement) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307780"
---
# <a name="supported-data-types"></a>Types de données pris en charge
Les types de données pris en charge par les DBMS varient considérablement. Une application peut déterminer les noms et les caractéristiques des types de données pris en charge en appelant **SQLGetTypeInfo**. En raison d’une grande variation des noms de type de données, l’application doit utiliser les noms de type de données retournés par **SQLGetTypeInfo** dans les relevés **CREATE TABLE.** Pour plus d’informations, voir [Data Types in ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
