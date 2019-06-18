---
title: DROP TABLE, instruction-Limitations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, DROP TABLE statement limitations
- DROP TABLE statement limitations [ODBC]
ms.assetid: 0a1c80f5-c9f2-4655-9bfd-0131b2f015a9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a24a22a5e666421136780f3614db4df2233bc82
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63128016"
---
# <a name="drop-table-statement-limitations"></a>DROP TABLE, instruction - limitations
Lorsque le pilote Microsoft Excel 5.0, 7.0 ou 97 est utilisé, l’instruction DROP TABLE efface la feuille de calcul, mais ne supprime pas le nom de la feuille de calcul. Étant donné que le nom de la feuille de calcul existe toujours dans le classeur, une autre feuille de calcul ne peut pas être créé portant le même nom.
