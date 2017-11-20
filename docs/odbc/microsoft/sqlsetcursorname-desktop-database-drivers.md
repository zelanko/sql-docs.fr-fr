---
title: "SQLSetCursorName (pilotes d’ordinateur de bureau) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetCursorName function [ODBC], Desktop Database Drivers
ms.assetid: 9bd7c87b-d99d-4e23-b2db-868d3b461c94
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ee0a3a3d5aa5404a062a11410f0ae2adf072e240
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (pilotes bureau de base de données)
Étant donné que le pilote ne pas prendre en charge une mise à jour positionnée ou supprimer par la WHERE CURRENT OF *cursorname* syntaxe, **SQLSetCursorName** est pris en charge, mais ne peut pas être utilisé pour les mises à jour positionnées. Il peut être utilisé uniquement lorsque la bibliothèque de curseurs est activée et à l’aide de l’application **SQLExtendedFetch**.

