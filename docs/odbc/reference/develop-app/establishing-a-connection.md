---
title: Établissement d’une connexion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- SQLBrowseConnect function [ODBC], establishing a connection
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- SQLConnect function [ODBC], establishing a connection
- SQLDriverConnect function [ODBC], making a connection
- ODBC drivers [ODBC], connection functions
ms.assetid: 8e3c717e-35e3-47ef-b5d3-3a96eeb7b869
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f71190a8a2ca1dd8af0d28adb5531540fb1b57e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298699"
---
# <a name="establishing-a-connection"></a>Établissement d’une connexion
Après l’allocation des handles d’environnement et de connexion et la définition de tous les attributs de connexion, l’application est prête à se connecter à la source de données ou au pilote. L’application peut utiliser trois fonctions différentes : **SQLConnect** (niveau de conformité de l’interface principale), **SQLDriverConnect** (Core) et **SQLBrowseConnect** (niveau 1). Chacun des trois est conçu pour être utilisé dans un autre scénario. Avant de se connecter, l’application peut déterminer laquelle de ces fonctions est prise en charge avec le mot clé **ConnectFunctions** retourné par **SQLDrivers**.  
  
> [!NOTE]  
>  Certains pilotes limitent le nombre de connexions actives qu’ils prennent en charge. Une application appelle **SQLGetInfo** avec l’option SQL_MAX_DRIVER_CONNECTIONS pour déterminer le nombre de connexions actives prises en charge par un pilote particulier.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Source de données par défaut](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Connexion avec SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Chaînes de connexion](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Connexion avec SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Connexion avec SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
