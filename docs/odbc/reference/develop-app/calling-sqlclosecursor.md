---
title: Appel SQLCloseCursor (fr) Microsoft Docs
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
ms.openlocfilehash: 2feab58de28e39747a1d9c819f9f15426b156151
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306272"
---
# <a name="calling-sqlclosecursor"></a>Appel de SQLCloseCursor
Étant donné que **SQLCloseCursor** est presque le même que **SQLFreeStmt** avec SQL_CLOSE, le gestionnaire de conducteur ne cartographie pas cette fonction. Les fonctions de remplacement sont cartographiées de sorte que les applications existantes ODBC *2.x* peuvent facilement se déplacer vers ODBC *3.x* en utilisant les nouvelles fonctions. Un tel mouvement rend plus facile pour ces applications de commencer à utiliser la nouvelle fonctionnalité ODBC *3.x* à l’intérieur du code conditionnel d’une manière modulaire. **SQLCloseCursor** ne représente aucune nouvelle fonctionnalité. Une application ne bénéficie d’aucun avantage en passant à **SQLCloseCursor** de **SQLFreeStmt** avec SQL_CLOSE.
