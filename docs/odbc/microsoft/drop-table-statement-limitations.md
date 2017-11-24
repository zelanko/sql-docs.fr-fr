---
title: "Limitations d’instruction DROP TABLE | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, DROP TABLE statement limitations
- DROP TABLE statement limitations [ODBC]
ms.assetid: 0a1c80f5-c9f2-4655-9bfd-0131b2f015a9
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 171439174f79ff6c7688834e0a487d9acf93bc6b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="drop-table-statement-limitations"></a>Limitations d’instruction DROP TABLE
Lorsque le pilote Microsoft Excel 5.0, 7.0 ou 97 est utilisé, l’instruction DROP TABLE supprime la feuille de calcul, mais ne supprime pas le nom de la feuille de calcul. Étant donné que le nom de la feuille de calcul existe toujours dans le classeur, Impossible de créer une autre feuille de calcul portant le même nom.
