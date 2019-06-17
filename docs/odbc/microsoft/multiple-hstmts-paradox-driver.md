---
title: Plusieurs hstmts (pilote Paradox) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- multiple hstmts [ODBC]
- Paradox driver [ODBC], multiple hstmts
ms.assetid: 66aecd94-092d-43d4-9583-74f5e2990eac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2dc086f25ca4da2a64a5edde2422f1fe33fcc444
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045464"
---
# <a name="multiple-hstmts-paradox-driver"></a>Plusieurs hstmts (pilote Paradox)
Lorsque le pilote ODBC Paradox est utilisé, si vous souhaitez utiliser plusieurs *hstmt* pour exécuter des requêtes sur une table, la table doit avoir un index unique (clé primaire).
