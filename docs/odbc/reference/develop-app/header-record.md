---
title: "Enregistrement d’en-tête | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- header records [ODBC]
- diagnostic records [ODBC]
ms.assetid: d0fff1ed-5616-422a-a394-7ea1d2486f89
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 13bab46b1340d152a6b91919bdadc59e987edde3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="header-record"></a>Enregistrement d’en-tête
Les champs de l’enregistrement d’en-tête contiennent des informations générales sur l’exécution d’une fonction, y compris le code de retour, le nombre de lignes, le nombre d’enregistrements d’état et le type d’instruction exécutée. L’enregistrement d’en-tête est toujours créé, sauf si la fonction retourne SQL_INVALID_HANDLE. Pour obtenir une liste complète des champs de l’enregistrement d’en-tête, consultez le [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) description de fonction.
