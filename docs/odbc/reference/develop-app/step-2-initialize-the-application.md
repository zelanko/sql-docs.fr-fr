---
title: 'Étape 2 : initialiser l’application | Microsoft Docs'
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
ms.openlocfilehash: 41030015645bda11242a703a163f26104e66dba0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114251"
---
# <a name="step-2-initialize-the-application"></a>Étape 2 : Initialiser l’application
La deuxième étape consiste à initialiser l’application, comme indiqué dans l’illustration suivante. Exactement ce qui est effectué ici varie en fonction de l’application.  
  
 ![Présente l'initialisation d'une application ODBC](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 À ce stade, il est courant d’utiliser **SQLGetInfo** pour découvrir les fonctionnalités du pilote. Pour plus d’informations, consultez prise [en compte des fonctionnalités de base de données à utiliser](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Toutes les applications doivent allouer un descripteur d’instruction avec **SQLAllocHandle**, et de nombreuses applications définissent des attributs d’instruction, tels que le type de curseur, avec **SQLSetStmtAttr**. Pour plus d’informations, consultez [allocation d’un handle d’instruction](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) et d' [attributs d’instruction](../../../odbc/reference/develop-app/statement-attributes.md).
