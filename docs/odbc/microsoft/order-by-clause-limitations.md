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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b58afff444c09622027f50a87bd77fcd6ed45640
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100779"
---
# <a name="order-by-clause-limitations"></a>ORDER BY, clause - limitations
Si une instruction SELECT contient une clause GROUP BY et une clause ORDER BY, la clause ORDER BY ne peut contenir qu’une colonne du jeu de résultats ou une expression dans la clause GROUP BY.
