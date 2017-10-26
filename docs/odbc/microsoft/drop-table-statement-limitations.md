---
title: "Limitations d’instruction DROP TABLE | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, DROP TABLE statement limitations
- DROP TABLE statement limitations [ODBC]
ms.assetid: 0a1c80f5-c9f2-4655-9bfd-0131b2f015a9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 65c47ece213312b749dee0e83b76e8de89cf3dc9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="drop-table-statement-limitations"></a>Limitations d’instruction DROP TABLE
Lorsque le pilote Microsoft Excel 5.0, 7.0 ou 97 est utilisé, l’instruction DROP TABLE supprime la feuille de calcul, mais ne supprime pas le nom de la feuille de calcul. Étant donné que le nom de la feuille de calcul existe toujours dans le classeur, Impossible de créer une autre feuille de calcul portant le même nom.

