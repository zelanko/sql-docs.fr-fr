---
title: Descripteurs implicitement alloués (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 271d479a9d2faa8cd7ab01e02e830b194c4138b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300129"
---
# <a name="implicitly-allocated-descriptors"></a>Descripteurs alloués implicitement
Lorsqu’une poignée de relevé est attribuée, l’application alloue implicitement un ensemble de quatre descripteurs. La demande peut obtenir les poignées de ces descripteurs implicitement attribués comme attributs de la poignée de déclaration. Lorsque l’application libère la poignée de relevé, le conducteur libère tous les descripteurs implicitement attribués sur cette poignée.
