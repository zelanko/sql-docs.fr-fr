---
title: Enregistrement d’en-tête | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- header records [ODBC]
- diagnostic records [ODBC]
ms.assetid: d0fff1ed-5616-422a-a394-7ea1d2486f89
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7b6ffacb618dd2b7714be59814f3f1a88a52228
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208481"
---
# <a name="header-record"></a>Enregistrement d’en-tête
Les champs dans l’enregistrement d’en-tête contiennent des informations générales sur l’exécution d’une fonction, y compris le code de retour, le nombre de lignes, le nombre d’enregistrements d’état et le type d’instruction exécutée. L’enregistrement d’en-tête est toujours créé, sauf si la fonction retourne SQL_INVALID_HANDLE. Pour obtenir une liste complète des champs dans l’enregistrement d’en-tête, consultez le [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) description de fonction.
