---
title: "Implicitement alloué descripteurs | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
ms.openlocfilehash: a0018755a9a03cb84385f2a187fdb1d62f0f6244
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="implicitly-allocated-descriptors"></a>Descripteurs implicitement alloués
Quand un descripteur d’instruction est alloué, l’application alloue implicitement un ensemble de descripteurs. L’application peut obtenir les descripteurs de ces implicitement alloué descripteurs en tant qu’attributs du handle d’instruction. Lorsque l’application libère le handle d’instruction, il libère tous les descripteurs implicitement alloués sur ce handle.
