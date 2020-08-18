---
description: DROP TABLE, instruction - limitations
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
ms.openlocfilehash: 9d56e53d8a17c15736e9423e5920c81f864e2973
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412555"
---
# <a name="drop-table-statement-limitations"></a>DROP TABLE, instruction - limitations
Lorsque le pilote Microsoft Excel 5,0, 7,0 ou 97 est utilisé, l’instruction DROP TABLE efface la feuille de calcul, mais ne supprime pas le nom de la feuille de calcul. Étant donné que le nom de la feuille de calcul existe toujours dans le classeur, une autre feuille de calcul ne peut pas être créée avec le même nom.
