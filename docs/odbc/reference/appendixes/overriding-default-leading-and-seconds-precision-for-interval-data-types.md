---
title: Remplacement de la précision de tête et de seconde pour les types de données d’intervalle (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1e60d5d8fc696ad8e2bd4cfb0c082ff214e066d0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303600"
---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Remplacement de la précision du début et de la fin par défaut pour les types de données d’intervalle
Lorsque le champ SQL_DESC_TYPE d’un ARD est réglé à un type date ou d’intervalle C, en appelant **SQLBindCol** ou **SQLSetDescField**, le champ SQL_DESC_PRECISION (qui contient la précision des secondes d’intervalle) est réglé sur les défauts suivants :  
  
-   6 pour l’en-cas et tous les types de données d’intervalle avec un deuxième composant.  
  
-   0 pour tous les autres types de données.  
  
 Pour tous les types de données d’intervalle, le champ descripteur SQL_DESC_DATETIME_INTERVAL_PRECISION, qui contient la précision de champ de tête d’intervalle, est réglé à une valeur par défaut de 2.  
  
 Lorsque le champ SQL_DESC_TYPE dans un APD est réglé à une date ou un type d’intervalle C, en appelant **SQLBindParameter** ou **SQLSetDescField**, les champs de SQL_DESC_PRECISION et de SQL_DESC_DATETIME_INTERVAL_PRECISION dans la DPA sont réglés à la valeur par défaut donnée précédemment. Cela est vrai pour les paramètres d’entrée, mais pas pour les paramètres d’entrée/sortie ou de sortie.  
  
 Un appel à **SQLSetDescRec** définit l’intervalle menant à la valeur par défaut, mais définit la précision des secondes d’intervalle (dans le champ SQL_DESC_PRECISION) à la valeur de son argument de *précision.*  
  
 Si l’un ou l’autre des défauts donnés précédemment n’est pas acceptable pour une application, l’application doit définir le champ SQL_DESC_PRECISION ou SQL_DESC_DATETIME_INTERVAL_PRECISION en appelant **SQLSetDescField**.  
  
 Si l’application appelle **SQLGetData** pour retourner les données dans un type datetime ou intervalle C, l’intervalle par défaut menant la précision et la précision des secondes d’intervalle sont utilisés. Si l’un ou l’autre défaut n’est pas acceptable, l’application doit appeler **SQLSetDescField** pour définir soit le champ descripteur, ou **SQLSetDescRec** pour définir SQL_DESC_PRECISION. L’appel à **SQLGetData** devrait avoir un *TargetType* de SQL_ARD_TYPE d’utiliser les valeurs dans les champs descripteur.  
  
 Lorsque **SQLPutData** est appelé, l’intervalle de précision et de précision des secondes d’intervalle sont lus à partir des champs de l’enregistrement descripteur qui correspondent au paramètre ou colonne de données à l’exécution, qui sont des champs APD pour les appels à **SQLExecute** ou **SQLExecDirect**, ou champs ARD pour les appels à **SQLBulkOperations** ou **SQLSetPos**.
