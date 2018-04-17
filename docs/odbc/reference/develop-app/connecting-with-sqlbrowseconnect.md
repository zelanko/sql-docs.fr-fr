---
title: Connexion avec SQLBrowseConnect | Documents Microsoft
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
- connecting to driver [ODBC], SQLBrowseConnect
- SQLBrowseConnect function [ODBC], connecting
- connecting to data source [ODBC], SQLBrowseConnect
ms.assetid: 6c2e9f76-b766-48df-b109-246bb05ae45d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f6382b0a02963395008dd02c962c10479aa5f29d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="connecting-with-sqlbrowseconnect"></a>Connexion avec SQLBrowseConnect
**SQLBrowseConnect**, comme **SQLDriverConnect**, utilise une chaîne de connexion. Toutefois, à l’aide de **SQLBrowseConnect**, une application peut construire une chaîne de connexion complète en cours d’exécution. L'application peut alors réaliser deux tâches :  
  
-   Créer ses propres boîtes de dialogue pour demander ces informations, et conserver ainsi contrôler son « apparence. »  
  
-   Parcourir le système à la recherche de sources de données qu'un pilote en particulier peut exploiter, et ce éventuellement en plusieurs étapes. Par exemple, l'utilisateur peut d'abord rechercher des serveurs sur le réseau, puis après avoir choisi un serveur, recherchez sur ce dernier des bases de données auxquelles le pilote peut accéder.  
  
 L’application appelle **SQLBrowseConnect** et passe une chaîne de connexion, appelée le *parcourir la requête de chaîne de connexion,* qui spécifie une source de données ou de pilote. Le pilote retourne une chaîne de connexion, appelée le *parcourir la chaîne de connexion du résultat,* qui contient les mots clés, les valeurs possibles (si le mot clé accepte un ensemble discret de valeurs) et les noms conviviaux. L’application génère une boîte de dialogue avec les noms conviviaux et invite l’utilisateur pour les valeurs. Il génère une nouvelle chaîne de connexion Parcourir demande à partir de ces valeurs et retourne cette du pilote avec un autre appel à **SQLBrowseConnect**.  
  
 Étant donné que les chaînes de connexion sont passés dans les deux sens, le pilote peut fournir plusieurs niveaux de navigation en retournant une nouvelle chaîne de connexion lors de l’application renvoie le. Par exemple, la première fois une application appelle **SQLBrowseConnect**, le pilote peut retourner des mots clés pour inviter l’utilisateur pour un nom de serveur. Lorsque l’application renvoie le nom du serveur, le pilote peut retourner des mots clés pour inviter l’utilisateur à une base de données. Le processus de navigation serait complète une fois que l’application a retourné le nom de la base de données.  
  
 Chaque fois que **SQLBrowseConnect** retourne une nouvelle chaîne de connexion résultats Parcourir, il retourne SQL_NEED_DATA en tant que son code de retour. Cela indique à l’application que le processus de connexion n’est pas terminé. Jusqu'à ce que **SQLBrowseConnect** retourne SQL_SUCCESS, la connexion est dans un état besoin des données et ne peut pas être utilisé à d’autres fins, telles que pour définir un attribut de connexion. L’application peut mettre fin à la connexion de navigation des processus en appelant **SQLDisconnect**.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Exemple de navigation SQL Server](../../../odbc/reference/develop-app/sql-server-browsing-example.md)
