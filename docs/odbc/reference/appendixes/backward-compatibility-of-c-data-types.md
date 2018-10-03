---
title: Compatibilité descendante des Types de données C | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: f1105f3adc3762e01c601d9c882bfbf0f05b9bad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47813631"
---
# <a name="backward-compatibility-of-c-data-types"></a>Compatibilité descendante des types de données C
SQL_C_SHORT, SQL_C_LONG et SQL_C_TINYINT ont été remplacés dans ODBC par types signés et non signés : SQL_C_SSHORT et SQL_C_USHORT, SQL_C_SLONG et SQL_C_ULONG et SQL_C_STINYINT et SQL_C_UTINYINT. Un ODBC 3 *.x* pilote doit fonctionner avec ODBC 2. *x* applications doivent prendre en charge SQL_C_SHORT, SQL_C_LONG et SQL_C_TINYINT, étant donné que lorsqu’elles sont appelées, le Gestionnaire de pilotes les passe par le biais du pilote.
