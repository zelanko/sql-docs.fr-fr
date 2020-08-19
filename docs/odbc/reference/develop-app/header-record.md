---
description: Enregistrement d’en-tête
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4de764381e54a0b3485130c1a3bdf25b2a9bf9fa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476641"
---
# <a name="header-record"></a>Enregistrement d’en-tête
Les champs de l’enregistrement d’en-tête contiennent des informations générales sur l’exécution d’une fonction, y compris le code de retour, le nombre de lignes, le nombre d’enregistrements d’État et le type d’instruction exécuté. L’enregistrement d’en-tête est toujours créé, sauf si la fonction retourne SQL_INVALID_HANDLE. Pour obtenir la liste complète des champs de l’enregistrement d’en-tête, consultez la description de la fonction [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) .
