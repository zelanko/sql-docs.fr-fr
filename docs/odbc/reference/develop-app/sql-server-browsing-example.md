---
description: Exemple de navigation SQL Server
title: Exemple d’exploration de SQL Server | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 14016832989c6fcba1dc39bc64434e72b049c18a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424561"
---
# <a name="sql-server-browsing-example"></a>Exemple de navigation SQL Server
L’exemple suivant montre comment **SQLBrowseConnect** peut être utilisé pour parcourir les connexions disponibles avec un pilote pour SQL Server. Tout d’abord, l’application demande un descripteur de connexion :  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 Ensuite, l’application appelle **SQLBrowseConnect** et spécifie le pilote SQL Server à l’aide de la description de pilote retournée par **SQLDrivers**:  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Étant donné qu’il s’agit du premier appel à **SQLBrowseConnect**, le gestionnaire de pilotes charge le pilote SQL Server et appelle la fonction **SQLBrowseConnect** du pilote avec les mêmes arguments que ceux reçus de l’application.  
  
> [!NOTE]  
>  Si vous vous connectez à un fournisseur de sources de données qui prend en charge l’authentification Windows, vous devez spécifier à `Trusted_Connection=yes` la place de l’ID d’utilisateur et des informations de mot de passe dans la chaîne de connexion.  
  
 Le pilote détermine qu’il s’agit du premier appel à **SQLBrowseConnect** et retourne le deuxième niveau des attributs de connexion : serveur, nom d’utilisateur, mot de passe, nom de l’application et ID de station de travail. Pour l’attribut Server, elle retourne une liste de noms de serveurs valides. Le code de retour de **SQLBrowseConnect** est SQL_NEED_DATA. Voici la chaîne de résultat de navigation :  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 Chaque mot clé dans la chaîne de résultat de navigation est suivi d’un signe deux-points et d’un ou de plusieurs mots avant le signe égal. Ces mots sont le nom convivial qu’une application peut utiliser pour créer une boîte de dialogue. Les mots clés **app** et **wsid** sont préfixés par un astérisque, ce qui signifie qu’ils sont facultatifs. Les mots clés **Server**, **UID**et **PWD** ne sont pas préfixés par un astérisque. les valeurs doivent être fournies pour eux dans la chaîne de requête de navigation suivante. La valeur du mot clé **Server** peut être l’un des serveurs retournés par **SQLBrowseConnect** ou un nom fourni par l’utilisateur.  
  
 L’application appelle de nouveau **SQLBrowseConnect** , en spécifiant le serveur vert et en omettant les mots clés **app** et **wsid** et les noms conviviaux après chaque mot clé :  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Le pilote tente de se connecter au serveur vert. En cas d’erreurs irrécupérables (par exemple, une paire mot clé/valeur manquante), **SQLBrowseConnect** retourne SQL_NEED_DATA et reste dans le même État qu’avant l’erreur. L’application peut appeler **SQLGetDiagField** ou **SQLGetDiagRec** pour déterminer l’erreur. Si la connexion réussit, le pilote retourne SQL_NEED_DATA et retourne la chaîne de résultat de navigation :  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 Comme les attributs de cette chaîne sont facultatifs, l’application peut les omettre. Toutefois, l’application doit à nouveau appeler **SQLBrowseConnect** . Si l’application choisit d’omettre le nom et la langue de la base de données, elle spécifie une chaîne de demande de navigation vide. Dans cet exemple, l’application choisit la base de données pubs et appelle **SQLBrowseConnect** une dernière fois, en omettant le mot clé **Language** et l’astérisque avant le mot clé **Database** :  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Étant donné que l’attribut **de base de données** est l’attribut de connexion final requis par le pilote, le processus de navigation est terminé, l’application est connectée à la source de données et **SQLBrowseConnect** retourne SQL_SUCCESS. **SQLBrowseConnect** retourne également la chaîne de connexion complète comme chaîne de résultat de navigation :  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 La dernière chaîne de connexion retournée par le pilote ne contient pas de noms conviviaux après chaque mot clé et ne contient pas de mots clés facultatifs non spécifiés par l’application. L’application peut utiliser cette chaîne avec **SQLDriverConnect** pour se reconnecter à la source de données sur le handle de connexion actuel (après la déconnexion) ou pour se connecter à la source de données sur un autre handle de connexion. Par exemple :  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
