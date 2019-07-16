---
title: 'Jet : Date, Time et Timestamp littéraux | Microsoft Docs'
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
ms.openlocfilehash: 1bb7f0fb02049b6d2f1897c4f495035aee2858f6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085495"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet : Littéraux de date, d’heure et d’horodatage
Pour une interopérabilité maximale, les applications doivent passer des littéraux de date au format canonique ODBC à l’aide de la syntaxe de la clause d’échappement :  
  
-   Pour les littéraux de date, {d '*valeur*»}, où *ur*e se présente sous la forme « aaaa-mm-jj »  
  
-   Pour les littéraux d’heure, {t '*valeur*»}, où *ur*e est sous la forme « hh : mm : »  
  
 Pour les littéraux d’horodatage {ts'*valeur*»}, où *ur*e se présente sous la forme « aaaa-mm-jj hh : mm : [. f...] ».
