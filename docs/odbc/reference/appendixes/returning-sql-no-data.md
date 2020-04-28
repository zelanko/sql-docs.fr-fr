---
title: Retour de SQL_NO_DATA | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e2c806edd5d5647e09c00975ad7207ee5c2c876
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305110"
---
# <a name="returning-sql_no_data"></a>Retour de SQL_NO_DATA
Quand une application *ODBC 2. x* avec un pilote *ODBC 3. x* appelle **SQLExecDirect**, **SQLExecute**ou **SQLParamData**et qu’une instruction UPDATE ou DELETE recherchée a été exécutée mais n’a affecté aucune ligne au niveau de la source de données, le pilote ODBC *3. x* doit retourner SQL_SUCCESS. Quand une application *ODBC 3. x* qui utilise un pilote *ODBC 3. x* appelle **SQLExecDirect**, **SQLExecute**ou **SQLParamData** avec le même résultat, le pilote ODBC *3. x* doit retourner SQL_NO_DATA.  
  
 Si une instruction UPDATE ou DELETE recherchée dans un lot d’instructions n’affecte aucune ligne de la source de données, **SQLMoreResults** retourne SQL_SUCCESS. Elle ne peut pas retourner SQL_NO_DATA, car cela signifie qu’il n’y a plus de résultats, et non qu’il y a un résultat d’une mise à jour/suppression recherchée qui n’a affecté aucune ligne.
