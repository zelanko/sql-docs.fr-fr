---
title: Descripteurs alloués implicitement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0eb34866b75802a32c63e62b41d384e5a1dea73
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138946"
---
# <a name="implicitly-allocated-descriptors"></a>Descripteurs alloués implicitement
Lorsqu’un descripteur d’instruction est alloué, l’application alloue implicitement un ensemble de quatre descripteurs. L’application peut obtenir les handles de ces descripteurs alloués implicitement en tant qu’attributs du descripteur d’instruction. Lorsque l’application libère le descripteur d’instruction, le pilote libère tous les descripteurs alloués implicitement sur ce handle.
