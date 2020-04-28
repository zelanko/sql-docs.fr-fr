---
title: Limitations de l’instruction DROP TABLE | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c296108b9ab26a6361d12ad71a1f21b21d5bea1e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303400"
---
# <a name="drop-table-statement-limitations"></a>DROP TABLE, instruction - limitations
Lorsque le pilote Microsoft Excel 5,0, 7,0 ou 97 est utilisé, l’instruction DROP TABLE efface la feuille de calcul, mais ne supprime pas le nom de la feuille de calcul. Étant donné que le nom de la feuille de calcul existe toujours dans le classeur, une autre feuille de calcul ne peut pas être créée avec le même nom.
