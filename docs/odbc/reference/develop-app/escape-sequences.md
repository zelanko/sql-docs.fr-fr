---
title: Séquences d’échappement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5d9589230183b198cb7d59cf9739dab75625441e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298709"
---
# <a name="escape-sequences"></a>Séquences d’échappement
ODBC définit les séquences d’évasion contenant la grammaire standard pour la date, l’heure, l’heure et les litres d’intervalle de date, les appels de fonction scalaire, les caractères d’échappement **de LIKE,** les jointures extérieures, et les appels de procédure. Les applications interopérables doivent utiliser ces séquences dans la mesure du possible.  
  
 Pour déterminer si un conducteur prend en charge les séquences d’évacuation pour la date, l’heure, l’heure ou les litres d’intervalle de date, une application appelle **SQLGetTypeInfo**. Si la source de données prend en charge un type de données de date, d’heure, d’heure ou d’intervalle de date, elle doit également prendre en charge la séquence d’évacuation correspondante. Pour déterminer si les autres séquences d’évacuation sont prises en charge, une application appelle **SQLGetInfo**.  
  
 Pour plus d’informations, voir [Escape Sequences in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md), plus tard dans cette section.
