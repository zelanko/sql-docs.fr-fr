---
title: Compatibilité rétrograde des types de données C (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a89b282a2229b6f34833b4371081661ea51b231
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304584"
---
# <a name="backward-compatibility-of-c-data-types"></a>Compatibilité descendante des types de données C
SQL_C_SHORT, SQL_C_LONG et SQL_C_TINYINT ont été remplacés en ODBC par des types signés et non signés : SQL_C_SSHORT et SQL_C_USHORT, SQL_C_SLONG et SQL_C_ULONG, et SQL_C_STINYINT et SQL_C_UTINYINT. Un conducteur ODBC *3.x* qui devrait travailler avec les applications ODBC *2.x* devrait prendre en charge SQL_C_SHORT, SQL_C_LONG et SQL_C_TINYINT, parce que quand ils sont appelés, le gestionnaire de conducteur les transmet au conducteur.
