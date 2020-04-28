---
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
ms.openlocfilehash: e80fcf8b1f2e3e83182e3278b63bdb856c7189fe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292929"
---
# <a name="order-by-clause-limitations"></a>ORDER BY, clause - limitations
Si une instruction SELECT contient une clause GROUP BY et une clause ORDER BY, la clause ORDER BY ne peut contenir qu’une colonne du jeu de résultats ou une expression dans la clause GROUP BY.
