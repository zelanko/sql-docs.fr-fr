---
title: Appel de SQLSetPos pour insérer des données | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 86647601dfc0223dd6fa4f0ffcc0e5db695868b5
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793214"
---
# <a name="calling-sqlsetpos-to-insert-data"></a>Appel de SQLSetPos pour insérer des données
Lorsqu’une application ODBC *2.x* application fonctionne avec une application ODBC *3.x* pilote appelle **SQLSetPos** avec un *opération* argument de SQL_ADD, le Gestionnaire de pilotes ne mappe pas cet appel à **SQLBulkOperations**. Si une application ODBC *3.x* pilote doit fonctionner avec une application qui appelle **SQLSetPos** avec SQL_ADD, le pilote doit prendre en charge cette opération.  
  
 Une différence majeure dans le comportement lorsque **SQLSetPos** est appelée avec SQL_ADD se produit lorsqu’elle est appelée dans un état S6. Dans ODBC *2.x*, le pilote a retourné S1010 lorsque **SQLSetPos** a été appelé avec SQL_ADD dans un état S6 (une fois que le curseur a été positionné avec **SQLFetch**). Dans ODBC *3.x*, **SQLBulkOperations** avec un *opération* de SQL_ADD peut être appelée dans un état S6. Une deuxième différence de comportement est que **SQLBulkOperations** avec un *opération* de SQL_ADD peut être appelée dans un état S5, tandis que **SQLSetPos** avec un  **Opération** de SQL_ADD ne peut pas. Pour les transitions d’instruction qui peuvent se produire pour le même appel dans ODBC *3.x*, consultez [annexe b : Tableaux des transitions d’état ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
