---
title: 'Jet : Littéraux de Date, heure et Timestamp | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2325cd7e4a10e91f351aa2107c64c0978b843fa6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825837"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet : littéraux de date, d’heure et d’horodatage
Pour une interopérabilité maximale, les applications doivent passer des littéraux de date au format canonique ODBC à l’aide de la syntaxe de la clause d’échappement :  
  
-   Pour les littéraux de date, {d '*valeur*»}, où *ur*e se présente sous la forme « aaaa-mm-jj »  
  
-   Pour les littéraux d’heure, {t '*valeur*»}, où *ur*e est sous la forme « hh : mm : »  
  
 Pour les littéraux d’horodatage {ts'*valeur*»}, où *ur*e se présente sous la forme « aaaa-mm-jj hh : mm : [. f...] ».
