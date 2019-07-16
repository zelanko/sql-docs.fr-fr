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
ms.openlocfilehash: 49ee96941c69da962e7c000c33d6eb14f66d4dab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031149"
---
# <a name="drop-table-statement-limitations"></a>DROP TABLE, instruction - limitations
Lorsque le pilote Microsoft Excel 5.0, 7.0 ou 97 est utilisé, l’instruction DROP TABLE efface la feuille de calcul, mais ne supprime pas le nom de la feuille de calcul. Étant donné que le nom de la feuille de calcul existe toujours dans le classeur, une autre feuille de calcul ne peut pas être créé portant le même nom.
