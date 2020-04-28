---
title: Substitution de la précision et de l’échelle par défaut pour les types de données numériques | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303590"
---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Remplacement de la précision et de l’échelle par défaut pour les types de données numériques
Lorsque le champ SQL_DESC_TYPE d’un ARD est défini sur SQL_C_NUMERIC, en appelant **SQLBindCol** ou **SQLSetDescField**, le champ SQL_DESC_SCALE dans ARD est défini sur 0 et le champ SQL_DESC_PRECISION est défini sur une précision par défaut définie par le pilote. Cela est également vrai lorsque le champ SQL_DESC_TYPE dans un APD est défini sur SQL_C_NUMERIC, en appelant **SQLBindParameter** ou **SQLSetDescField**. Cela est vrai pour les paramètres d’entrée, d’entrée/sortie ou de sortie.  
  
 Si l’une des valeurs par défaut décrites précédemment n’est pas acceptable pour une application, l’application doit définir le champ SQL_DESC_SCALE ou SQL_DESC_PRECISION en appelant **SQLSetDescField** ou **SQLSetDescRec**.  
  
 Si l’application appelle **SQLGetData** pour retourner des données dans une structure SQL_C_NUMERIC, les champs SQL_DESC_SCALE et SQL_DESC_PRECISION par défaut sont utilisés. Si les valeurs par défaut ne sont pas acceptables, l’application doit appeler **SQLSetDescRec** ou **SQLSetDescField** pour définir les champs, puis appeler **SQLGetData** avec un *TargetType* de SQL_ARD_TYPE pour utiliser les valeurs des champs de descripteur.  
  
 Lorsque **SQLPutData** est appelé, l’appel utilise les champs SQL_DESC_SCALE et SQL_DESC_PRECISION de l’enregistrement de descripteur qui correspond au paramètre ou à la colonne de données en cours d’exécution, qui sont des champs APD pour les appels à **SQLExecute** ou **SQLEXECDIRECT**, ou les champs ARD pour les appels à **SQLBulkOperations** ou **SQLSetPos**.
