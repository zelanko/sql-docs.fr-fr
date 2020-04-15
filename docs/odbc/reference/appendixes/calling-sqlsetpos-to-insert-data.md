---
title: Appel à SQLSetPos pour insérer des données ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb374b2506d55b400207c8f60bdf42bb6bb4065e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306600"
---
# <a name="calling-sqlsetpos-to-insert-data"></a>Appel de SQLSetPos pour insérer des données
Lorsqu’une application ODBC *2.x* travaillant avec un conducteur ODBC *3.x* appelle **SQLSetPos** avec un argument *d’opération* de SQL_ADD, le gestionnaire de conducteur ne cartographie pas cet appel à **SQLBulkOperations**. Si un conducteur ODBC *3.x* doit travailler avec une application qui appelle **SQLSetPos** avec SQL_ADD, le conducteur doit soutenir cette opération.  
  
 Une différence majeure de comportement lorsque **SQLSetPos** est appelé avec SQL_ADD se produit quand il est appelé dans l’état S6. Dans ODBC *2.x*, le conducteur est retourné S1010 lorsque **SQLSetPos** a été appelé avec SQL_ADD dans l’état S6 (après que le curseur a été positionné avec **SQLFetch**). Dans ODBC *3.x*, **SQLBulkOperations** avec une *opération* de SQL_ADD peut être appelé dans l’état S6. Une deuxième différence majeure de comportement est que **SQLBulkOperations** avec une *opération* de SQL_ADD peut être appelé dans l’état S5, tandis que **SQLSetPos** avec une **opération** de SQL_ADD ne peut pas. Pour les transitions de déclaration qui peuvent se produire pour le même appel dans ODBC *3.x*, voir [Annexe B: ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
