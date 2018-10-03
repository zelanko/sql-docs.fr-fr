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
manager: craigg
ms.openlocfilehash: c1423d7bcc0f0b943b490fdcf8f931efb6b533c6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47775885"
---
# <a name="escape-sequences"></a>Séquences d’échappement
ODBC définit des séquences d’échappement contenant une syntaxe standard pour les appels de fonction scalaire date, time, timestamp et des littéraux d’intervalle de date/heure, **comme** prédicat caractères d’échappement, les jointures externes et les appels de procédure. Applications interopérables doivent utiliser ces séquences autant que possible.  
  
 Pour déterminer si un pilote prend en charge les séquences d’échappement pour la date, heure, timestamp ou littéraux d’intervalle de date/heure, une application appelle **SQLGetTypeInfo**. Si la source de données prend en charge une date, heure, timestamp ou le type de données d’intervalle datetime, il doit également prendre en charge la séquence d’échappement correspondante. Pour déterminer si les autres séquences d’échappement sont pris en charge, une application appelle **SQLGetInfo**.  
  
 Pour plus d’informations, consultez [les séquences d’échappement dans ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md), plus loin dans cette section.
