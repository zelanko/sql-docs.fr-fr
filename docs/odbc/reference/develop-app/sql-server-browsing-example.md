---
title: Exemple de navigation de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBrowseConnect function [ODBC], example
- connecting to data source [ODBC], SqlBrowseConnect
- connecting to driver [ODBC], SQLBrowseConnect
ms.assetid: 6e0d5fd1-ec93-4348-a77a-08f5ba738bc6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8dc57d738c1d5726d2208b930c5d4fadcd93b39
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149324"
---
# <a name="sql-server-browsing-example"></a>Exemple de navigation SQL Server
L’exemple suivant montre comment **SQLBrowseConnect** peut être utilisé pour parcourir les connexions disponibles avec un pilote pour SQL Server. Tout d’abord, l’application demande un handle de connexion :  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 Ensuite, l’application appelle **SQLBrowseConnect** et spécifie le pilote SQL Server, à l’aide de la description du pilote retournée par **SQLDrivers**:  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Comme il s’agit du premier appel à **SQLBrowseConnect**, le Gestionnaire de pilotes charge le pilote SQL Server et appelle le pilote **SQLBrowseConnect** fonction avec les mêmes arguments qu’il a reçu à partir de la application.  
  
> [!NOTE]  
>  Si vous vous connectez à un fournisseur de source de données qui prend en charge l’authentification Windows, vous devez spécifier `Trusted_Connection=yes` au lieu des informations d’ID et mot de passe utilisateur dans la chaîne de connexion.  
  
 Le pilote détermine qu’il s’agit du premier appel à **SQLBrowseConnect** et retourne le deuxième niveau des attributs de connexion : serveur, nom d’utilisateur, mot de passe, nom de l’application et les ID de station de travail. Pour l’attribut de serveur, elle retourne une liste de noms de serveur valide. Le code de retour de **SQLBrowseConnect** est SQL_NEED_DATA. Voici la chaîne de résultat Parcourir :  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 Chaque mot clé dans la chaîne de résultat Parcourir est suivi par un signe deux-points et d’un ou plusieurs mots avant le signe égal. Ces mots sont le nom convivial qu’une application peut utiliser pour créer une boîte de dialogue. Le **application** et **WSID** mots clés sont préfixées par un astérisque, ce qui signifie qu’ils sont facultatifs. Le **SERVER**, **UID**, et **PWD** mots clés ne sont pas préfixés par un astérisque ; doivent être fournies pour eux dans la chaîne de requête de navigation suivante. La valeur de la **SERVER** mot clé peut être un des serveurs retournées par **SQLBrowseConnect** ou un nom fourni par l’utilisateur.  
  
 L’application appelle **SQLBrowseConnect** à nouveau, en spécifiant le serveur vert et l’omission du **application** et **WSID** mots clés et les noms conviviaux après chaque mot clé :  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Le pilote tente de se connecter au serveur vert. S’il existe des erreurs récupérables, par exemple une paire mot clé-valeur manquante, **SQLBrowseConnect** retourne SQL_NEED_DATA et reste dans le même état tel qu’il était avant l’erreur. L’application peut appeler **SQLGetDiagField** ou **SQLGetDiagRec** pour déterminer l’erreur. Si la connexion est établie, le pilote retourne SQL_NEED_DATA et retourne la chaîne de résultat Parcourir :  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 Étant donné que les attributs de cette chaîne sont facultatifs, l’application les omettre. Toutefois, l’application doit appeler **SQLBrowseConnect** à nouveau. Si l’application choisit d’omettre le nom de la base de données et le langage, elle spécifie une chaîne de requête de navigation vide. Dans cet exemple, l’application choisit la base de données pubs et appelle **SQLBrowseConnect** une dernière fois, en omettant le **langage** mot clé et l’astérisque avant la **base de données**mot clé :  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Étant donné que le **base de données** attribut est l’attribut de connexion finale requis par le pilote, la navigation terminée, l’application est connectée à la source de données, et **SQLBrowseConnect** Retourne SQL_SUCCESS. **SQLBrowseConnect** retourne également la chaîne de connexion complète en tant que la chaîne de résultat Parcourir :  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 La chaîne de connexion finale retournée par le pilote ne contient pas les noms conviviaux après chaque mot clé, ni si elle contient des mots clés facultatifs non spécifiées par l’application. L’application peut utiliser cette chaîne par **SQLDriverConnect** se reconnecter à la source de données sur le handle de connexion actuel (après la déconnexion) ou pour vous connecter à la source de données sur un handle de connexion différents. Exemple :  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
