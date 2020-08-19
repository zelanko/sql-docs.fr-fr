---
description: Plusieurs hstmts (pilote Paradox)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 687b87f07142ad23f6faf7155ae974a6d93deab4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449401"
---
# <a name="multiple-hstmts-paradox-driver"></a>Plusieurs hstmts (pilote Paradox)
Lorsque le pilote ODBC Paradox est utilisé, si vous souhaitez utiliser plusieurs *HSTMT* pour exécuter des requêtes sur une table, la table doit avoir un index unique (clé primaire Paradox).
