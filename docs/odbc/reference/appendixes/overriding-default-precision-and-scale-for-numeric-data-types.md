---
title: Précision et échelle par défaut pour les types de données numériques (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], precision and scale
- precision [ODBC], numeric data types
- data types [ODBC], numeric data types
- numeric data type [ODBC]
- numeric literals [ODBC]
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 365c5f69d21dd3a4ad8e89805d81f1b3b0c9dcba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303590"
---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Remplacement de la précision et de l’échelle par défaut pour les types de données numériques
Lorsque le champ SQL_DESC_TYPE dans un ARD est mis à SQL_C_NUMERIC, en appelant **sqLBindCol** ou **SQLSetDescField**, le champ SQL_DESC_SCALE dans l’ARD est réglé à 0 et le champ SQL_DESC_PRECISION est réglé à une précision par défaut définie par le conducteur. Cela est également vrai lorsque le champ SQL_DESC_TYPE dans un APD est mis à SQL_C_NUMERIC, en appelant soit **SQLBindParameter** ou **SQLSetDescField**. Cela est vrai pour les paramètres d’entrée, d’entrée/sortie ou de sortie.  
  
 Si l’un ou l’autre des défauts décrits précédemment ne sont pas acceptables pour une application, l’application doit définir le champ SQL_DESC_SCALE ou SQL_DESC_PRECISION en appelant **SQLSetDescField** ou **SQLSetDescRec**.  
  
 Si l’application appelle **SQLGetData** pour retourner les données dans une structure SQL_C_NUMERIC, les champs par défaut SQL_DESC_SCALE et SQL_DESC_PRECISION sont utilisés. Si les défauts de paiement ne sont pas acceptables, l’application doit appeler **SQLSetDescRec** ou **SQLSetDescField** pour définir les champs, puis appeler **SQLGetData** avec un *TargetType* de SQL_ARD_TYPE pour utiliser les valeurs dans les champs descripteur.  
  
 Lorsque **SQLPutData** est appelé, l’appel utilise les champs SQL_DESC_SCALE et SQL_DESC_PRECISION de l’enregistrement descripteur qui correspond au paramètre ou colonne de données à l’exécution, qui sont des champs APD pour les appels à **SQLExecute** ou **SQLExecDirect**, ou champs ARD pour les appels à **SQLBulkOperations** ou **SQLSetPos**.
