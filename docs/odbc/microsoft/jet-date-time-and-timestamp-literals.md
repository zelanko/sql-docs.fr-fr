---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1bb7f0fb02049b6d2f1897c4f495035aee2858f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68085495"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet : littéraux de date, d’heure et d’horodatage
Pour une interopérabilité maximale, les applications doivent transmettre des littéraux de date au format canonique ODBC à l’aide de la syntaxe de clause Escape :  
  
-   Pour les littéraux de date, {d'*value*'}, où *ur*e se présente sous la forme « yyyy-mm-dd »  
  
-   Pour les littéraux d’heure, {t'*value*'}, où *ur*e est au format "HH : mm : SS"  
  
 Pour les littéraux timestamp {ts'*value*'}, où *ur*e se présente sous la forme « yyyy-mm-jj hh : mm : SS [. f...] ».
