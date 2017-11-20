---
title: "SQLSetPos (pilotes d’ordinateur de bureau) | Documents Microsoft"
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
- SQLSetPos function [ODBC], Desktop Database Drivers
ms.assetid: 8ef027ec-8512-48fe-8fe2-2ff7cd81e331
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2b630be96f099e1f2553c8d03b9896f32ea3e670
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetpos-desktop-database-drivers"></a>SQLSetPos (pilotes bureau de base de données)
La sémantique du modèle en bloc pour **SQLSetPos** appelle avec la *irow* argument égal à 0 sont pris en charge.  
  
 SQL_LOCK_NO_CHANGE est pris en charge pour *généalogique*. SQL_LOCK_EXCLUSIVE et SQL_LOCK_UNLOCK ne sont pas pris en charge.  
  
 **SQLSetPos** prend en charge les jointures d’être mise à jour. (Pour plus d’informations, consultez la *Guide du programmeur moteur Microsoft Jet de base de données*.)

