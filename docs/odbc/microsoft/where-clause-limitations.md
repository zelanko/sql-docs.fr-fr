---
title: "OÙ Clause Limitations | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, WHERE clause limitations
- WHERE clause limitations [ODBC]
ms.assetid: 46b54f74-e4a3-4318-87cf-8a97c38a2718
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c55864642bced9895f8a6f5a408b8fbc1a216335
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="where-clause-limitations"></a>OÙ Clause Limitations
Le nombre maximal de clauses dans une clause WHERE est 40.  
  
 Colonnes LONGVARBINARY et LONGVARCHAR peuvent être comparés aux littéraux jusqu'à 255 caractères, mais ne peut pas être comparés à l’aide de paramètres.
