---
title: Comportement d’engagement et de recul (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c67c29b295160a2908152b22c7a349ce4c0f9f50
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299129"
---
# <a name="commit-and-rollback-behavior"></a>Comportement de validation et d’annulation
Un comportement courant parmi les DBMS serveur est de fermer les curseurs et de jeter les instructions préparées lorsqu’une déclaration est commise ou annulée. Les bases de données de bureau sont plus susceptibles de garder les curseurs ouverts et de conserver les instructions préparées. Pour de plus amples renseignements, consultez les options de SQL_CURSOR_COMMIT_BEHAVIOR et de SQL_CURSOR_ROLLBACK_BEHAVIOR dans la description de la fonction [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) et [l’effet des transactions sur les curseurs et les déclarations préparées.](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)
