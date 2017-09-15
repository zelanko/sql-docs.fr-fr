---
title: "Séquences d’échappement | Documents Microsoft"
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
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1c648549b41ff607ad34175475c6a2b75603625f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="escape-sequences"></a>Séquences d’échappement
ODBC définit des séquences d’échappement contenant une grammaire standard pour date, time, timestamp et littéraux de l’intervalle datetime, les appels de fonction scalaire, **comme** prédicat caractères d’échappement, des jointures externes et des appels de procédure. Applications interopérables doivent utiliser ces séquences de chaque fois que possible.  
  
 Pour déterminer si un pilote prend en charge les séquences d’échappement pour la date, heure, timestamp ou littéraux d’intervalle datetime, une application appelle **SQLGetTypeInfo**. Si la source de données prend en charge une date, heure, timestamp ou le type de données d’intervalle datetime, il doit également prendre en charge la séquence d’échappement correspondante. Pour déterminer si les autres séquences d’échappement sont pris en charge, une application appelle **SQLGetInfo**.  
  
 Pour plus d’informations, consultez [les séquences d’échappement dans ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md), plus loin dans cette section.
