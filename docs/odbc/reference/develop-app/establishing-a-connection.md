---
title: L’établissement d’une connexion | Documents Microsoft
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
- data sources [ODBC], connection functions
- SQLBrowseConnect function [ODBC], establising a connection
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- SQLConnect function [ODBC], establising a connection
- SQLDriverConnect function [ODBC], making a connection
- ODBC drivers [ODBC], connection functions
ms.assetid: 8e3c717e-35e3-47ef-b5d3-3a96eeb7b869
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 80de9f41bf4c535f7d9daa34b7b14d0377ab2383
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="establishing-a-connection"></a>L’établissement d’une connexion
Après l’allocation de handles d’environnement et de connexion et en définissant les attributs de connexion, l’application est prête pour se connecter à la source de données ou le pilote. Il existe trois fonctions différentes, l’application peut utiliser pour ce faire : **SQLConnect** (niveau de conformité d’interface de base), **SQLDriverConnect** (base), et **SQLBrowseConnect** (niveau 1). Chacun des trois est conçu pour être utilisé dans un autre scénario. Avant de vous connecter, l’application peut déterminer laquelle de ces fonctions est prise en charge avec la **ConnectFunctions** mot clé retourné par **SQLDrivers**.  
  
> [!NOTE]  
>  Certains pilotes de limitent le nombre de connexions actives, qu'ils prennent en charge. Une application appelle **SQLGetInfo** avec l’option SQL_MAX_DRIVER_CONNECTIONS pour déterminer le nombre de connexions actif prend en charge un pilote spécifique.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Source de données par défaut](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Connexion avec SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Chaînes de connexion](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Connexion avec SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Connexion avec SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
