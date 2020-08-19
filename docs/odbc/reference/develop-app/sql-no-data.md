---
description: SQL_NO_DATA
title: SQL_NO_DATA | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb81d6f1fce50a27aba203eec4b78648754010e5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424571"
---
# <a name="sql_no_data"></a>SQL_NO_DATA
Quand ODBC 3. l’application *x* appelle **SQLExecDirect**, **SQLExecute**ou **SQLParamData** dans ODBC 2. *x* pour exécuter une instruction UPDATE ou DELETE recherchée qui n’affecte aucune ligne de la source de données, le pilote doit retourner SQL_SUCCESS, et non SQL_NO_DATA. Quand ODBC 2. *x* ou ODBC 3. *x* qui fonctionne avec une application ODBC 3. le pilote *x* appelle **SQLExecDirect**, **SQLExecute**ou **SQLParamData** avec le même résultat, ODBC 3. le pilote *x* doit retourner SQL_NO_DATA.
