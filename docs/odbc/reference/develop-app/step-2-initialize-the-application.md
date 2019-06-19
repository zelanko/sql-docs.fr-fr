---
title: 'Étape 2 : Initialiser l’Application | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0d25173dc8dc14aa1ed41a4a88496ef654e2ff0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149193"
---
# <a name="step-2-initialize-the-application"></a>Étape 2 : Initialiser l’application
La deuxième étape consiste à initialiser l’application, comme indiqué dans l’illustration suivante. Exactement ce qui se fait ici varie en fonction de l’application.  
  
 ![Présente l’initialisation d’une application ODBC](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 À ce stade, il est courant d’utiliser **SQLGetInfo** pour découvrir les fonctionnalités du pilote. Pour plus d’informations, consultez [tenir compte des fonctionnalités de base de données à utiliser](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Toutes les applications ont besoin d’allouer un descripteur d’instruction avec **SQLAllocHandle**, et de nombreuses applications définissent les attributs d’instruction, telles que le type de curseur, avec **SQLSetStmtAttr**. Pour plus d’informations, consultez [allouer un Handle d’instruction](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) et [les attributs d’instruction](../../../odbc/reference/develop-app/statement-attributes.md).
