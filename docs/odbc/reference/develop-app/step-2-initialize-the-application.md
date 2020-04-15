---
title: 'Étape 2 : Initialiser l’application Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 843155ba6b641ea26717e63af55c8774f963a800
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288265"
---
# <a name="step-2-initialize-the-application"></a>Étape 2 : Initialiser l’application
La deuxième étape consiste à initialiser l’application, comme le montre l’illustration suivante. Exactement ce qui est fait ici varie avec l’application.  
  
 ![Présente l'initialisation d'une application ODBC](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 À ce stade, il est courant d’utiliser **SQLGetInfo** pour découvrir les capacités du conducteur. Pour plus d’informations, voir [Considering Database Features to Use](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Toutes les applications doivent allouer une poignée de déclaration avec **SQLAllocHandle**, et de nombreuses applications définissent des attributs d’énoncés, tels que le type de curseur, avec **SQLSetStmtAttr**. Pour plus d’informations, voir [Allouer une poignée de déclaration](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) et des [attributs de déclaration](../../../odbc/reference/develop-app/statement-attributes.md).
