---
title: Connexion à SQLDriverConnect | Microsoft Docs
description: SQLDriverConnect fournit des fonctionnalités de connexion supplémentaires sur SQLConnect, y compris des options pour inviter l’utilisateur à fournir des informations supplémentaires.
ms.custom: ''
ms.date: 08/20/2020
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
ms.openlocfilehash: 78186e903405aa1b59cfac185e62646dbda6e77a
ms.sourcegitcommit: dc8a30a4a27e15fc6671ca2674da9b7c637ec255
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88746169"
---
# <a name="connecting-with-sqldriverconnect"></a>Connexion avec SQLDriverConnect

**SQLDriverConnect** est utilisé pour se connecter à une source de données à l’aide d’une chaîne de connexion. **SQLDriverConnect** est utilisé à la place de **SQLConnect** pour les scénarios suivants :  
  
- Établissez une connexion à l’aide d’une chaîne de connexion qui contient le nom de la source de données, un ou plusieurs ID d’utilisateur, un ou plusieurs mots de passe et d’autres informations requises par la source de données.  
  
- Établissez une connexion à l’aide d’une chaîne de connexion partielle ou de l’absence d’informations supplémentaires. dans ce cas, le gestionnaire de pilotes et le pilote peuvent inviter l’utilisateur à entrer les informations de connexion.  
  
- Établissez une connexion à une source de données qui n’est pas définie dans les informations système. Si l’application fournit une chaîne de connexion partielle, le pilote peut demander des informations de connexion à l’utilisateur.  
  
- Établissez une connexion à une source de données à l’aide d’une chaîne de connexion construite à partir des informations contenues dans un fichier. DSN.  
  
Après l’établissement d’une connexion, **SQLDriverConnect** retourne la chaîne de connexion terminée. L’application peut utiliser cette chaîne pour les demandes de connexion suivantes.

Cette section contient les rubriques suivantes :  
  
- [Informations de connexion spécifiques du pilote](driver-specific-connection-information.md)  
  
- [Demande des informations de connexion à l’utilisateur](prompting-the-user-for-connection-information.md)  
  
- [Connexion à l’aide de sources de données de fichier](connecting-using-file-data-sources.md)  
  
- [Connexion directe à des pilotes](connecting-directly-to-drivers.md)
