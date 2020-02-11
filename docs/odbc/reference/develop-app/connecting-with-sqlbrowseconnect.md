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
ms.openlocfilehash: 04df089b97bf385925c87a98b3f89cdac3ef21e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083134"
---
# <a name="connecting-with-sqlbrowseconnect"></a>Connexion avec SQLBrowseConnect
**SQLBrowseConnect**, comme **SQLDriverConnect**, utilise une chaîne de connexion. Toutefois, en utilisant **SQLBrowseConnect**, une application peut construire une chaîne de connexion complète au moment de l’exécution. L'application peut alors réaliser deux tâches :  
  
-   Créez ses propres boîtes de dialogue pour demander ces informations, ce qui permet de conserver le contrôle de son apparence.  
  
-   Parcourir le système à la recherche de sources de données qu'un pilote en particulier peut exploiter, et ce éventuellement en plusieurs étapes. Par exemple, l'utilisateur peut d'abord rechercher des serveurs sur le réseau, puis après avoir choisi un serveur, recherchez sur ce dernier des bases de données auxquelles le pilote peut accéder.  
  
 L’application appelle **SQLBrowseConnect** et transmet une chaîne de connexion, connue sous le nom de *chaîne de connexion de requête de navigation,* qui spécifie un pilote ou une source de données. Le pilote retourne une chaîne de connexion, connue sous le nom de *chaîne de connexion du résultat de navigation,* qui contient des mots clés, des valeurs possibles (si le mot clé accepte un ensemble discret de valeurs) et des noms conviviaux. L’application génère une boîte de dialogue avec les noms conviviaux et invite l’utilisateur à entrer des valeurs. Il génère ensuite une nouvelle chaîne de connexion de requête de navigation à partir de ces valeurs et le retourne au pilote avec un autre appel à **SQLBrowseConnect**.  
  
 Étant donné que les chaînes de connexion sont transmises dans l’autre sens, le pilote peut fournir plusieurs niveaux de navigation en retournant une nouvelle chaîne de connexion lorsque l’application retourne l’ancienne. Par exemple, la première fois qu’une application appelle **SQLBrowseConnect**, le pilote peut retourner des mots clés pour inviter l’utilisateur à entrer un nom de serveur. Lorsque l’application retourne le nom du serveur, le pilote peut retourner des mots clés pour inviter l’utilisateur à entrer une base de données. Le processus de navigation est terminé une fois que l’application a retourné le nom de la base de données.  
  
 Chaque fois que **SQLBrowseConnect** retourne une nouvelle chaîne de connexion de résultat de navigation, il retourne SQL_NEED_DATA comme code de retour. Cela indique à l’application que le processus de connexion n’est pas terminé. Jusqu’à ce que **SQLBrowseConnect** retourne SQL_SUCCESS, la connexion est dans un état de données requis et ne peut pas être utilisée à d’autres fins, par exemple pour définir un attribut de connexion. L’application peut mettre fin au processus de navigation des connexions en appelant **SQLDisconnect**.  
  
 Cette section contient la rubrique suivante.  
  
-   [Exemple de navigation SQL Server](../../../odbc/reference/develop-app/sql-server-browsing-example.md)
