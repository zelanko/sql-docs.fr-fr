---
description: 'Jet : Littéraux de date, d’heure et d’horodatage'
title: 'Jet : littéraux de date, d’heure et d’horodatage | Microsoft Docs'
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
ms.openlocfilehash: 02b2a7c5c633ee891dbcd962786cb1904bfd5df8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449441"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet : Littéraux de date, d’heure et d’horodatage
Pour une interopérabilité maximale, les applications doivent transmettre des littéraux de date au format canonique ODBC à l’aide de la syntaxe de clause Escape :  
  
-   Pour les littéraux de date, {d'*value*'}, où *ur*e se présente sous la forme « yyyy-mm-dd »  
  
-   Pour les littéraux d’heure, {t'*value*'}, où *ur*e est au format "HH : mm : SS"  
  
 Pour les littéraux timestamp {ts'*value*'}, où *ur*e se présente sous la forme « yyyy-mm-jj hh : mm : SS [. f...] ».
