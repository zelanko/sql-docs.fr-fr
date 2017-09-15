---
title: "Substitution de précision par défaut et l’échelle pour les Types de données numériques | Documents Microsoft"
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
- numeric data type [ODBC], precision and scale
- precision [ODBC], numeric data types
- data types [ODBC], numeric data types
- numeric data type [ODBC]
- numeric literals [ODBC]
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 613ec65d838a525251b6682cca477c5c8d24a162
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Substitution de précision par défaut et l’échelle pour les Types de données numériques
Lorsque le champ SQL_DESC_TYPE dans un ARD a la valeur SQL_C_NUMERIC, en appelant **SQLBindCol** ou **SQLSetDescField**, le champ SQL_DESC_SCALE dans le ARD est défini sur 0 et le champ SQL_DESC_PRECISION est défini avec une précision par défaut définie par le pilote. Cela est également vrai lorsque le champ SQL_DESC_TYPE dans un APD a la valeur SQL_C_NUMERIC, en appelant **SQLBindParameter** ou **SQLSetDescField**. Cela est vrai pour les paramètres de sortie, d’entrée/sortie ou d’entrée.  
  
 Si une des valeurs par défaut décrites précédemment ne sont pas acceptable pour une application, l’application doit définir le champ SQL_DESC_SCALE ou SQL_DESC_PRECISION en appelant **SQLSetDescField** ou **SQLSetDescRec**.  
  
 Si l’application appelle **SQLGetData** pour renvoyer des données en une structure SQL_C_NUMERIC, les champs SQL_DESC_SCALE et SQL_DESC_PRECISION par défaut sont utilisés. Si les valeurs par défaut ne sont pas acceptables, l’application doit appeler **SQLSetDescRec** ou **SQLSetDescField** pour définir les champs, puis appelez **SQLGetData** avec un *TargetType* de SQL_ARD_TYPE pour utiliser les valeurs dans les champs de descripteur.  
  
 Lorsque **SQLPutData** est appelée, l’appel utilise les champs SQL_DESC_SCALE et SQL_DESC_PRECISION de l’enregistrement de descripteur qui correspond au paramètre de data-at-execution ou colonne, qui sont des champs APD pour les appels à **SQLExecute** ou **SQLExecDirect**, ou les champs ARD pour les appels à **SQLBulkOperations** ou **SQLSetPos**.
