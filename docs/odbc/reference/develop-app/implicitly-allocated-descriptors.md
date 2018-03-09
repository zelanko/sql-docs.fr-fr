---
title: "Implicitement alloué descripteurs | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b06fd5efeaad6f1346feecda9ac74476353aac87
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="implicitly-allocated-descriptors"></a>Descripteurs implicitement alloués
Quand un descripteur d’instruction est alloué, l’application alloue implicitement un ensemble de descripteurs. L’application peut obtenir les descripteurs de ces implicitement alloué descripteurs en tant qu’attributs du handle d’instruction. Lorsque l’application libère le handle d’instruction, il libère tous les descripteurs implicitement alloués sur ce handle.
