---
title: Compatibilité descendante des types de données C | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], C data types
- compatibility [ODBC], C data types
- data types [ODBC], backward compatibility
- C data types [ODBC], backward compatibility
ms.assetid: b1453a65-ae03-4061-b0cf-a8434d8bc40b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dcfc4dd2ef1bee2783f073fbb85c0d911f84305a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037801"
---
# <a name="backward-compatibility-of-c-data-types"></a>Compatibilité descendante des types de données C
SQL_C_SHORT, SQL_C_LONG et SQL_C_TINYINT ont été remplacés dans ODBC par des types signés et non signés : SQL_C_SSHORT et SQL_C_USHORT, SQL_C_SLONG et SQL_C_ULONG, et SQL_C_STINYINT et SQL_C_UTINYINT. Un pilote ODBC *3. x* qui doit fonctionner avec les applications ODBC *2. x* doit prendre en charge SQL_C_SHORT, SQL_C_LONG et SQL_C_TINYINT, car lorsqu’ils sont appelés, le gestionnaire de pilotes les transmet au pilote.
