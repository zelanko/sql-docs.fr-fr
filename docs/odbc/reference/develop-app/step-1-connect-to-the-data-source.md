---
title: "Étape 1 : Se connecter à la Source de données | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 42da1bad914342a2f2973a63dc35f6e53f8b6c93
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="step-1-connect-to-the-data-source"></a>Étape 1 : Se connecter à la Source de données
La première étape dans n’importe quelle application consiste à se connecter à la source de données. Cette phase, y compris les fonctions qu’il requiert, est indiquée dans l’illustration suivante.  
  
 ![Connexion à la source de données dans une application ODBC](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 La première étape de la connexion à la source de données consiste à charger le Gestionnaire de pilotes et allouer le handle d’environnement avec **SQLAllocHandle**. Pour plus d’informations, consultez [allouer le Handle d’environnement](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 L’application enregistre la version d’ODBC à laquelle elle se conforme en appelant **SQLSetEnvAttr** avec l’attribut d’environnement SQL_ATTR_APP_ODBC_VER. Pour plus d’informations, consultez [déclarant ODBC Version l’Application](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) et [la compatibilité descendante et la conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Ensuite, l’application alloue un handle de connexion avec **SQLAllocHandle** et se connecte à la source de données avec **SQLConnect**, **SQLDriverConnect**, ou **SQLBrowseConnect**. Pour plus d’informations, consultez [allouer un Handle de connexion](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) et [l’établissement d’une connexion](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 L’application définit les attributs de connexion, par exemple s’il faut valider manuellement des transactions. Pour plus d’informations, consultez [attributs de connexion](../../../odbc/reference/develop-app/connection-attributes.md).

