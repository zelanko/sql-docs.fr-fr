---
title: Remplacer la précision du début et Types de données Interval | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- precision [ODBC], interval data types
- seconds precision [ODBC]
- interval data type [ODBC], precision
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: 3d65493f-dce7-4d29-9f59-c63a4e47918c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fdab9e6e60311aca4ce0ae35f92e38c45fdf3702
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687945"
---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Remplacement de la précision du début et de la fin par défaut pour les types de données d’intervalle
Lorsque le champ SQL_DESC_TYPE d’un ARD est défini à un type de C datetime ou interval, en appelant **SQLBindCol** ou **SQLSetDescField**, le champ SQL_DESC_PRECISION (qui contient l’intervalle en secondes précision) est définie sur les valeurs par défaut suivantes :  
  
-   6 pour timestamp et tous les types de données d’intervalle avec un second composant.  
  
-   0 pour tous les autres types de données.  
  
 Pour tous les types de données d’intervalle, le champ de descripteur SQL_DESC_DATETIME_INTERVAL_PRECISION, qui contient la précision de champ Début intervalle, a la valeur 2 comme valeur par défaut.  
  
 Quand le champ SQL_DESC_TYPE dans un APD a un type de C datetime ou interval, en appelant **SQLBindParameter** ou **SQLSetDescField**, le SQL_DESC_PRECISION et SQL_DESC_DATETIME_INTERVAL_ Champs de précision dans le descripteur APD sont définies sur la valeur par défaut indiquée précédemment. Cela est vrai pour les paramètres d’entrée mais pas pour les paramètres d’entrée/sortie ou de sortie.  
  
 Un appel à **SQLSetDescRec** définit l’intervalle de la précision de début à la valeur par défaut, mais définit la précision de secondes d’intervalle (dans le champ SQL_DESC_PRECISION) à la valeur de son *précision* argument.  
  
 Si une des valeurs par défaut étant donnés précédemment n’est pas acceptable pour une application, l’application doit définir le champ SQL_DESC_PRECISION or SQL_DESC_DATETIME_INTERVAL_PRECISION en appelant **SQLSetDescField**.  
  
 Si l’application appelle **SQLGetData** pour retourner des données dans un intervalle de type C ou datetime, la précision par défaut du début de l’intervalle et la précision de secondes d’intervalle sont utilisés. Si la valeur par défaut n’est pas acceptable, l’application doit appeler **SQLSetDescField** à définir n’importe quel champ de descripteur, ou **SQLSetDescRec** pour définir SQL_DESC_PRECISION. L’appel à **SQLGetData** doit avoir un *TargetType* de SQL_ARD_TYPE d’utiliser les valeurs dans les champs de descripteur.  
  
 Lorsque **SQLPutData** est appelée, l’intervalle de précision et l’intervalle de secondes précision sont lues à partir des champs de l’enregistrement de descripteur qui correspondent à la data-at-execution paramètre ou la colonne, qui sont des champs APD pour les appels de début pour **SQLExecute** ou **SQLExecDirect**, ou les champs ARD pour les appels à **SQLBulkOperations** ou **SQLSetPos**.
