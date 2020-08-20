---
description: Appel de SQLCloseCursor
title: Appel de SQLCloseCursor | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 925617d79266f0b50ef9b38586b31af91311b63e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494769"
---
# <a name="calling-sqlclosecursor"></a>Appel de SQLCloseCursor
Étant donné que **SQLCloseCursor** est quasiment identique à **SQLFreeStmt** avec SQL_CLOSE, le gestionnaire de pilotes ne mappe pas cette fonction. Les fonctions de remplacement sont mappées afin que les applications ODBC *2. x* existantes puissent facilement être déplacées vers ODBC *3. x* en utilisant les nouvelles fonctions. Un tel déplacement permet à de telles applications de commencer à utiliser de nouvelles fonctionnalités ODBC *3. x* à l’intérieur d’un code conditionnel de manière modulaire. **SQLCloseCursor** ne représente pas de nouvelles fonctionnalités. Une application ne tire aucun avantage en passant à **SQLCloseCursor** à partir de **SQLFreeStmt** avec SQL_CLOSE.
