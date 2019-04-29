---
title: Connexion avec SQLBrowseConnect | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec1cd42e6704bc5168b1eb20841100fc279a66ab
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63042765"
---
# <a name="connecting-with-sqlbrowseconnect"></a>Connexion avec SQLBrowseConnect
**SQLBrowseConnect**, comme **SQLDriverConnect**, utilise une chaîne de connexion. Toutefois, à l’aide **SQLBrowseConnect**, une application peut construire une chaîne de connexion complète en cours d’exécution. L'application peut alors réaliser deux tâches :  
  
-   Créer ses propres boîtes de dialogue pour demander ces informations, et conserver ainsi contrôler son « apparence. »  
  
-   Parcourir le système à la recherche de sources de données qu'un pilote en particulier peut exploiter, et ce éventuellement en plusieurs étapes. Par exemple, l'utilisateur peut d'abord rechercher des serveurs sur le réseau, puis après avoir choisi un serveur, recherchez sur ce dernier des bases de données auxquelles le pilote peut accéder.  
  
 L’application appelle **SQLBrowseConnect** et transmet une chaîne de connexion, appelée le *parcourir la chaîne de connexion de demande,* qui spécifie une pilote ou source de données. Le pilote retourne une chaîne de connexion, appelée le *parcourir la chaîne de connexion de résultat,* qui contient les mots clés, les valeurs possibles (si le mot clé accepte un ensemble discret de valeurs) et des noms conviviaux. L’application génère une boîte de dialogue avec les noms conviviaux et invite l’utilisateur pour les valeurs. Il génère une nouvelle chaîne de connexion demande Parcourir à partir de ces valeurs, puis il retourne le pilote avec un autre appel à **SQLBrowseConnect**.  
  
 Étant donné que les chaînes de connexion sont passés dans les deux sens, le pilote peut fournir plusieurs niveaux de la navigation en retournant une nouvelle chaîne de connexion lors de l’application renvoie l’ancienne version. Par exemple, la première fois une application appelle **SQLBrowseConnect**, le pilote peut retourner des mots clés pour inviter l’utilisateur pour un nom de serveur. Lorsque l’application renvoie le nom du serveur, le pilote peut retourner des mots clés pour inviter l’utilisateur pour une base de données. Le processus de navigation serait complète une fois que l’application a retourné le nom de la base de données.  
  
 Chaque fois **SQLBrowseConnect** retourne une nouvelle chaîne de connexion de résultat Parcourir, elle retourne SQL_NEED_DATA en tant que son code de retour. Cela indique à l’application que le processus de connexion n’est pas terminé. Jusqu'à ce que **SQLBrowseConnect** retourne SQL_SUCCESS, la connexion est dans un état besoin des données et ne peut pas être utilisé à d’autres fins, telles que pour définir un attribut de connexion. L’application peut mettre fin à la connexion de navigation des processus en appelant **SQLDisconnect**.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Exemple de navigation SQL Server](../../../odbc/reference/develop-app/sql-server-browsing-example.md)
