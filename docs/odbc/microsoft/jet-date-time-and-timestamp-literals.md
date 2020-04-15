---
title: 'Jet: Date, Heure, et Timestamp Literals (fr) Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 372b7c1dab1ad8ff000fb88729c3b02e05d4a21c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299932"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet : Littéraux de date, d’heure et d’horodatage
Pour une interopérabilité maximale, les demandes doivent passer des dates littérales dans le format canonique ODBC à l’aide de la syntaxe à clause d’évasion :  
  
-   Pour les littérals de date, la*valeur*d '', où la *valeur*e est sous la forme de "yyyy-mm-dd"  
  
-   Pour les littérals de temps, 't '*valeur*', où la *valeur*e est sous la forme "hh:mm:ss"  
  
 Pour les littérals de timestamp 'ts '*valeur*', où la *valeur*e est sous la forme "yyyy-mm-dd hh:mm:ss[.f...]".
