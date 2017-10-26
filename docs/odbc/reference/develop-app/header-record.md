---
title: "Enregistrement d’en-tête | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- header records [ODBC]
- diagnostic records [ODBC]
ms.assetid: d0fff1ed-5616-422a-a394-7ea1d2486f89
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0e4b73bf94c2d90f34c1d06240cbcceb07702c7a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="header-record"></a>Enregistrement d’en-tête
Les champs de l’enregistrement d’en-tête contiennent des informations générales sur l’exécution d’une fonction, y compris le code de retour, le nombre de lignes, le nombre d’enregistrements d’état et le type d’instruction exécutée. L’enregistrement d’en-tête est toujours créé, sauf si la fonction retourne SQL_INVALID_HANDLE. Pour obtenir une liste complète des champs de l’enregistrement d’en-tête, consultez le [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) description de fonction.

