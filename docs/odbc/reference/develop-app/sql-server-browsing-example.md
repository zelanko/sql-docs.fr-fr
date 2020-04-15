---
title: SqL Server Browsing Exemple (fr) Microsoft Docs
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
ms.openlocfilehash: 7b15aa8e3d573660a312fceb5b9100a41f0384d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301980"
---
# <a name="sql-server-browsing-example"></a>Exemple de navigation SQL Server
L’exemple suivant montre comment **SQLBrowseConnect** peut être utilisé pour parcourir les connexions disponibles avec un pilote pour SQL Server. Tout d’abord, la demande une poignée de connexion :  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 Ensuite, l’application appelle **SQLBrowseConnect** et spécifie le conducteur SQL Server, en utilisant la description du conducteur retournée par **SQLDrivers**:  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Parce qu’il s’agit du premier appel à **SQLBrowseConnect**, le gestionnaire de conducteur charge le pilote SQL Server et appelle la fonction **SQLBrowseConnect** du conducteur avec les mêmes arguments qu’il a reçus de l’application.  
  
> [!NOTE]  
>  Si vous vous connectez à un fournisseur de sources `Trusted_Connection=yes` de données qui prend en charge l’authentification de Windows, vous devez spécifier au lieu d’informations d’identification et de mot de passe de l’utilisateur dans la chaîne de connexion.  
  
 Le conducteur détermine qu’il s’agit du premier appel à **SQLBrowseConnect** et renvoie le deuxième niveau d’attributs de connexion : serveur, nom d’utilisateur, mot de passe, nom d’application et id de poste de travail. Pour l’attribut serveur, il renvoie une liste de noms de serveur valides. Le code de retour de **SQLBrowseConnect** est SQL_NEED_DATA. Voici la chaîne de résultat de navigation:  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 Chaque mot clé dans la chaîne de résultat de navigation est suivi d’un côlon et d’un ou plusieurs mots avant le signe égal. Ces mots sont le nom convivial qu’une application peut utiliser pour construire une boîte de dialogue. Les mots clés **APP** et **WSID** sont préfixés par un astérisque, ce qui signifie qu’ils sont facultatifs. Les mots-clés **SERVER**, **UID**et **PWD** ne sont pas préfixés par un astérisque; les valeurs doivent être fournies pour eux dans la prochaine chaîne de demande de navigation. La valeur du mot clé **SERVER** peut être l’un des serveurs retournés par **SQLBrowseConnect** ou un nom fourni par l’utilisateur.  
  
 L’application appelle **SQLBrowseConnect** à nouveau, en spécifiant le serveur vert et en omettant les mots clés **APP** et **WSID** et les noms conviviaux après chaque mot clé:  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Le conducteur tente de se connecter au serveur vert. S’il y a des erreurs non mortelles, comme une paire de mots clés manquante, **SQLBrowseConnect** retourne SQL_NEED_DATA et reste dans le même état qu’avant l’erreur. L’application peut appeler **SQLGetDiagField** ou **SQLGetDiagRec** pour déterminer l’erreur. Si la connexion est réussie, le pilote retourne SQL_NEED_DATA et renvoie la chaîne de résultat de navigation :  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 Parce que les attributs de cette chaîne sont facultatifs, l’application peut les omettre. Toutefois, l’application doit à nouveau appeler **SQLBrowseConnect.** Si l’application choisit d’omettre le nom et la langue de la base de données, elle spécifie une chaîne de demande de navigation vide. Dans cet exemple, l’application choisit la base de données pubs et appelle **SQLBrowseConnect** une dernière fois, en omettant le mot-clé **LANGUAGE** et l’astérisque avant le mot clé **DATABASE:**  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Étant donné que l’attribut **DATABASE** est l’attribut de connexion final requis par le pilote, le processus de navigation est terminé, l’application est connectée à la source de données, et **SQLBrowseConnect renvoie** SQL_SUCCESS. **SQLBrowseConnect renvoie** également la chaîne de connexion complète comme la chaîne de résultat de navigation :  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 La chaîne de connexion finale retournée par le pilote ne contient pas les noms conviviaux après chaque mot clé, ni ne contient de mots clés optionnels non spécifiés par l’application. L’application peut utiliser cette chaîne avec **SQLDriverConnect** pour se reconnecter à la source de données sur la poignée de connexion actuelle (après déconnexion) ou pour se connecter à la source de données sur une poignée de connexion différente. Par exemple :  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
