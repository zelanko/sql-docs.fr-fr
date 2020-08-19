---
description: Chaînes de connexion
title: Chaînes de connexion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fbb2d4b0c80a93b225bac754d2905b27e8844cbb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424771"
---
# <a name="connection-strings"></a>Chaînes de connexion
Une chaîne de connexion contient des informations utilisées pour établir une connexion. Une chaîne de connexion complète contient toutes les informations nécessaires pour établir une connexion. La chaîne de connexion est une série de paires mot clé/valeur séparées par des points-virgules. (Pour la syntaxe complète d’une chaîne de connexion, consultez la description de la fonction [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) .) La chaîne de connexion est utilisée par :  
  
-   **SQLDriverConnect**, qui complète la chaîne de connexion par interaction avec l’utilisateur.  
  
-   **SQLBrowseConnect**, qui complète la chaîne de connexion de façon itérative avec la source de données.  
  
 **SQLConnect** n’utilise pas de chaîne de connexion ; l’utilisation de **SQLConnect** est analogue à la connexion à l’aide d’une chaîne de connexion avec exactement trois paires mot clé/valeur (pour le nom de la source de données et, éventuellement, l’ID utilisateur et le mot de passe).
