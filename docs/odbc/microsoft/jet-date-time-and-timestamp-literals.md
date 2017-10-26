---
title: "Jet : Date, heure et horodatage littéraux | Documents Microsoft"
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
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c1a98ca0b68198dada19e4ac81f8637798a99b95
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet : Date, heure et horodatage littéraux
Pour une interopérabilité maximale, les applications doivent passer des littéraux de date au format canonique ODBC à l’aide de la syntaxe de la clause d’échappement :  
  
-   Pour les littéraux de date, {d '*valeur*'}, où *eurs*e est sous la forme « aaaa-mm-jj »  
  
-   Pour les littéraux d’heure, {t '*valeur*'}, où *eurs*e est sous la forme « hh : mm : »  
  
 Pour les littéraux d’horodatage {ts'*valeur*'}, où *eurs*e est sous la forme « aaaa-mm-jj hh : mm : [. f...] ».

