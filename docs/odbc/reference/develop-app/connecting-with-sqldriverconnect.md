---
title: Connexion à SQLDriverConnect | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6cd95364d8a5316a50d9f55616236a8677bf99e4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299069"
---
# <a name="connecting-with-sqldriverconnect"></a>Connexion avec SQLDriverConnect
**SQLDriverConnect** est utilisé pour se connecter à une source de données à l’aide d’une chaîne de connexion. **SQLDriverConnect** est utilisé à la place de **SQLConnect** pour les raisons suivantes :  
  
-   Pour permettre à l’application d’utiliser des informations de connexion spécifiques au pilote.  
  
-   Pour demander que le pilote invite l'utilisateur à fournir des informations sur la connexion.  
  
-   Pour se connecter sans spécifier de source de données.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Informations de connexion spécifiques du pilote](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [Demande des informations de connexion à l’utilisateur](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [Connexion à l’aide de sources de données de fichier](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [Connexion directe à des pilotes](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
