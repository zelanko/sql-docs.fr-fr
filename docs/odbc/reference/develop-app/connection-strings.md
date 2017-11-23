---
title: "Chaînes de connexion | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to driver [ODBC], connection strings
- functions [ODBC], data source or driver connections
- connection strings [ODBC], about connection strings
- connecting to data source [ODBC], connection strings
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: 724c7b86-300a-4fa9-ad96-4afa0fdcb3e9
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 99c0ebcad365396bd2ebab2d03df4cb6a6627003
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="connection-strings"></a>Chaînes de connexion
Une chaîne de connexion contient des informations utilisées pour établir une connexion. Chaîne de connexion complète contient toutes les informations nécessaires pour établir une connexion. La chaîne de connexion est une série de paires mot clé/valeur séparées par des points-virgules. (Pour la syntaxe complète d’une chaîne de connexion, consultez le [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) description de fonction.) La chaîne de connexion est utilisée par :  
  
-   **SQLDriverConnect**, qui termine la chaîne de connexion en interaction avec l’utilisateur.  
  
-   **SQLBrowseConnect**, qui termine de manière itérative avec la source de données, la chaîne de connexion.  
  
 **SQLConnect** n’utilise pas une chaîne de connexion ; à l’aide de **SQLConnect** est analogue à la connexion à l’aide d’une chaîne de connexion avec des paires mot clé/valeur exactement trois (pour le nom de source de données et, éventuellement, utilisateur ID et mot de passe).
