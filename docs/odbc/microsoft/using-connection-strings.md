---
title: "À l’aide de chaînes de connexion | Documents Microsoft"
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
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 76aa702a2fe055daaea55f18ffa951f1808e31df
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="using-connection-strings"></a>À l’aide de chaînes de connexion
Vous pouvez utiliser une chaîne de connexion pour se connecter à une source de données Visual FoxPro.  
  
 Par exemple, pour vous connecter à la source de données TasTrade et que vous remplacez que le paramètre actuel d’exclusif associé à la source de données, vous utiliseriez la chaîne :  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Pour obtenir la liste des mots clés des attributs et des valeurs que vous pouvez inclure dans la chaîne de connexion, consultez [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Pour obtenir une explication complète de la syntaxe de chaîne de connexion, consultez [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) dans les *de référence du programmeur ODBC*.
