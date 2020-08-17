---
description: ORDER BY, clause - limitations
title: Limitations des clauses ORDER BY | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, ORDER BY clause limitations
- ORDER BY clause limitations [ODBC]
ms.assetid: fd4ddc7c-9c7e-4a0c-a781-e5427dfb2e18
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c116c40bdb16f3417b2b92295b0d13056dfcc18a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340625"
---
# <a name="order-by-clause-limitations"></a>ORDER BY, clause - limitations
Si une instruction SELECT contient une clause GROUP BY et une clause ORDER BY, la clause ORDER BY ne peut contenir qu’une colonne du jeu de résultats ou une expression dans la clause GROUP BY.
