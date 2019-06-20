---
title: L’établissement d’une connexion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70f459f60616e7edd77078a7e9653ab9dff097e9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248348"
---
# <a name="establishing-a-connection"></a>Établissement d’une connexion
Après l’allocation de handles d’environnement et de connexion et en définissant les attributs de connexion, l’application est prête à se connecter à la source de données ou le pilote. Il existe trois fonctions différentes, que l’application peut utiliser pour ce faire : **SQLConnect** (niveau de conformité d’interface de base), **SQLDriverConnect** (Core), et **SQLBrowseConnect** (niveau 1). Chacun des trois est conçu pour être utilisé dans un autre scénario. Avant de vous connecter, l’application peut déterminer laquelle de ces fonctions est prise en charge avec le **ConnectFunctions** mot clé retournée par **SQLDrivers**.  
  
> [!NOTE]  
>  Certains pilotes de limitent le nombre de connexions actives, qu'elles prennent en charge. Une application appelle **SQLGetInfo** avec l’option SQL_MAX_DRIVER_CONNECTIONS pour déterminer le nombre de connexions actif un pilote spécifique prend en charge.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Source de données par défaut](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Connexion avec SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Chaînes de connexion](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Connexion avec SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Connexion avec SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
