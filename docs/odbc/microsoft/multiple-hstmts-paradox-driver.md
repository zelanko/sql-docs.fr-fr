---
title: Plusieurs hstmts (pilote Paradox) | Documents Microsoft
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
- multiple hstmts [ODBC]
- Paradox driver [ODBC], multiple hstmts
ms.assetid: 66aecd94-092d-43d4-9583-74f5e2990eac
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 64c4a04b3896425e0d7e677c7e04077fd759ffd6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="multiple-hstmts-paradox-driver"></a>Plusieurs hstmts (pilote Paradox)
Lorsque le pilote ODBC Paradox est utilisé, si vous souhaitez utiliser plusieurs *hstmt* pour exécuter des requêtes sur une table, la table doit avoir un index unique (clé primaire).
