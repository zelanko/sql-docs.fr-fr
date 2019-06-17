---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ee139dd652204c750c99d8bad8ab2b17c7c1ba1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63007805"
---
# <a name="calling-sqlclosecursor"></a>Appel de SQLCloseCursor
Étant donné que **SQLCloseCursor** est presque identique **SQLFreeStmt** avec SQL_CLOSE, le Gestionnaire de pilotes ne mappe pas cette fonction. Fonctions de remplacement sont mappées afin qu’existant ODBC 2 *.x* applications peuvent facilement transférer dans ODBC 3. *x* à l’aide des nouvelles fonctions. Ce déplacement rend plus facile pour de telles applications commencer à l’aide de la nouvelle ODBC 3. *x* fonctionnalités à l’intérieur du code conditionnel de façon modulaire. **SQLCloseCursor** ne représente pas de nouvelles fonctionnalités. Une application ne peut pas accéder tout l’avantage en déplaçant vers **SQLCloseCursor** de **SQLFreeStmt** avec SQL_CLOSE.
