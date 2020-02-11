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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d73282cde4d0598d7e6a35ac6273935626b96969
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001371"
---
# <a name="escape-sequences"></a>Séquences d’échappement
ODBC définit des séquences d’échappement contenant la grammaire standard pour les littéraux date, Time, timestamp et DateTime Interval, les appels de fonction scalaires, **comme** les caractères d’échappement de prédicat, les jointures externes et les appels de procédure. Les applications interopérables doivent utiliser ces séquences dans la mesure du possible.  
  
 Pour déterminer si un pilote prend en charge les séquences d’échappement pour les littéraux de date, d’heure, d’horodatage ou d’intervalle DateTime, une application appelle **SQLGetTypeInfo**. Si la source de données prend en charge un type de données date, Time, timestamp ou DateTime Interval, elle doit également prendre en charge la séquence d’échappement correspondante. Pour déterminer si les autres séquences d’échappement sont prises en charge, une application appelle **SQLGetInfo**.  
  
 Pour plus d’informations, consultez [séquences d’échappement dans ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md), plus loin dans cette section.
