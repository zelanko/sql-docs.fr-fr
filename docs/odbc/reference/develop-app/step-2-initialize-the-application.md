---
title: 'Étape 2 : Initialiser l’Application | Documents Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf8cf5a5d697b1e8c52da84d93ccf23c6e127c3b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="step-2-initialize-the-application"></a>Étape 2 : Initialiser l’Application
La deuxième étape consiste à initialiser l’application, comme indiqué dans l’illustration suivante. Exactement ce qui est fait ici varie en fonction de l’application.  
  
 ![Illustre l’initialisation d’une application ODBC](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 À ce stade, il est courant d’utiliser **SQLGetInfo** pour découvrir les fonctionnalités du pilote. Pour plus d’informations, consultez [tenant compte des fonctionnalités de base de données à utiliser](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Toutes les applications ont besoin allouer un descripteur d’instruction avec **SQLAllocHandle**, et de nombreuses applications avec attributs d’instruction, telles que le type de curseur, **SQLSetStmtAttr**. Pour plus d’informations, consultez [allouer un Handle d’instruction](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) et [les attributs d’instruction](../../../odbc/reference/develop-app/statement-attributes.md).
