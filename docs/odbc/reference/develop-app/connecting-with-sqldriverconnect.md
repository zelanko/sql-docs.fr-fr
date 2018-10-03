---
title: Connexion avec SQLDriverConnect | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- SQLDriverConnect function [ODBC], connecting
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: e46e959f-d3c5-4ddb-810a-107bfcb83fd2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78cdaabe867ae67e3a1dfcb80e82cfaf95a94ed1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797907"
---
# <a name="connecting-with-sqldriverconnect"></a>Connexion avec SQLDriverConnect
**SQLDriverConnect** est utilisé pour se connecter à une source de données à l’aide d’une chaîne de connexion. **SQLDriverConnect** est utilisé au lieu de **SQLConnect** pour les raisons suivantes :  
  
-   Pour permettre l’application d’utiliser les informations de connexion spécifiques au pilote.  
  
-   Pour demander que le pilote invite l'utilisateur à fournir des informations sur la connexion.  
  
-   Pour vous connecter sans spécifier une source de données.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Informations de connexion spécifiques du pilote](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [Demande des informations de connexion à l’utilisateur](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [Connexion à l’aide de sources de données de fichier](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [Connexion directe à des pilotes](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
