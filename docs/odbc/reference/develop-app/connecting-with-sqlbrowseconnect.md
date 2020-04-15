---
title: Connexion avec SQLBrowseConnect (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], SQLBrowseConnect
- SQLBrowseConnect function [ODBC], connecting
- connecting to data source [ODBC], SQLBrowseConnect
ms.assetid: 6c2e9f76-b766-48df-b109-246bb05ae45d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4d738d394bb3c507f6aa08f736016b51ac4fefb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294659"
---
# <a name="connecting-with-sqlbrowseconnect"></a>Connexion avec SQLBrowseConnect
**SQLBrowseConnect**, comme **SQLDriverConnect**, utilise une chaîne de connexion. Cependant, en utilisant **SQLBrowseConnect**, une application peut construire une chaîne de connexion complète au moment de l’exécution. L'application peut alors réaliser deux tâches :  
  
-   Construisez ses propres boîtes de dialogue pour inciter à cette information, conservant ainsi le contrôle de son « look and feel ».  
  
-   Parcourir le système à la recherche de sources de données qu'un pilote en particulier peut exploiter, et ce éventuellement en plusieurs étapes. Par exemple, l'utilisateur peut d'abord rechercher des serveurs sur le réseau, puis après avoir choisi un serveur, recherchez sur ce dernier des bases de données auxquelles le pilote peut accéder.  
  
 L’application appelle **SQLBrowseConnect** et passe une chaîne de connexion, connue sous le nom de *chaîne de connexion de demande de navigation,* qui spécifie un pilote ou une source de données. Le pilote retourne une chaîne de connexion, connue sous le nom de chaîne de *connexion de résultat de navigation,* qui contient des mots clés, des valeurs possibles (si le mot clé accepte un ensemble discret de valeurs), et des noms conviviaux. L’application construit une boîte de dialogue avec les noms conviviaux et invite l’utilisateur pour les valeurs. Il construit ensuite une nouvelle chaîne de connexion de demande de navigation à partir de ces valeurs et retourne cela au conducteur avec un autre appel à **SQLBrowseConnect**.  
  
 Étant donné que les chaînes de connexion sont transmises d’avant en arrière, le conducteur peut fournir plusieurs niveaux de navigation en retournant une nouvelle chaîne de connexion lorsque l’application retourne l’ancienne. Par exemple, la première fois qu’une application appelle **SQLBrowseConnect**, le pilote peut retourner des mots clés pour inciter l’utilisateur à obtenir un nom de serveur. Lorsque l’application renvoie le nom du serveur, le pilote peut retourner des mots clés pour inciter l’utilisateur à une base de données. Le processus de navigation serait terminé après que l’application a retourné le nom de base de données.  
  
 Chaque fois **que SQLBrowseConnect renvoie** une nouvelle chaîne de connexion de résultat de navigation, il renvoie SQL_NEED_DATA comme code de retour. Cela indique à l’application que le processus de connexion n’est pas terminé. Jusqu’à ce que **SQLBrowseConnect** revienne SQL_SUCCESS, la connexion est dans un état de données de besoin et ne peut pas être utilisée à d’autres fins, par exemple pour définir un attribut de connexion. L’application peut mettre fin au processus de navigation de connexion en appelant **SQLDisconnect**.  
  
 Cette section contient le sujet suivant.  
  
-   [Exemple de navigation SQL Server](../../../odbc/reference/develop-app/sql-server-browsing-example.md)
