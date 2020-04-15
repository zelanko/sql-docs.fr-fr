---
title: Informations sur les connexions spécifiques au conducteur (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConnect function [ODBC], driver-specific connection information
- connecting to driver [ODBC], SQLConnect
- SQLDriverConnect function [ODBC], driver specific connection information
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SQLConnect
- connecting to driver [ODBC], driver-specific information
ms.assetid: 3748758a-f16a-4f3b-9c40-06f2e300704e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 16c8c5fc4fd3ac63aa3613b41e530446dffec118
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305789"
---
# <a name="driver-specific-connection-information"></a>Informations de connexion spécifiques du pilote
**SQLConnect** suppose qu’un nom de source de données, un identifiant d’utilisateur et un mot de passe sont suffisants pour se connecter à une source de données et que toutes les autres informations de connexion peuvent être stockées sur le système. Ce n’est souvent pas le cas. Par exemple, un pilote peut avoir besoin d’un identifiant d’utilisateur et d’un mot de passe pour se connecter à un serveur et à un identifiant et un mot de passe différents pour se connecter à un DBMS. Étant donné que **SQLConnect** accepte un seul identifiant d’utilisateur et un mot de passe, cela signifie que l’autre identifiant et mot de passe de l’utilisateur doivent être stockés avec les informations de source de données sur le système si **SQLConnect** doit être utilisé. Il s’agit d’une violation potentielle de la sécurité et doit être évitée à moins que le mot de passe soit crypté.  
  
 **SQLDriverConnect** permet au conducteur de définir une quantité arbitraire d’informations de connexion dans les paires de mots-clés de la chaîne de connexion. Supposons, par exemple, qu’un pilote ait besoin d’un nom de source de données, d’un identifiant d’utilisateur et d’un mot de passe pour le serveur, ainsi qu’d’un identifiant et d’un mot de passe pour le DBMS. Un programme personnalisé qui utilise toujours la source de données XYZ Corp peut inciter l’utilisateur pour les identifiants et les mots de passe et de construire l’ensemble suivant de paires de mots clés,ou chaîne de *connexion,* de passer à **SQLDriverConnect**:  
  
> [!NOTE]  
>  Si vous vous connectez à un fournisseur de sources `Trusted_Connection=yes` de données qui prend en charge l’authentification de Windows, vous devez spécifier au lieu d’informations d’identification et de mot de passe de l’utilisateur dans la chaîne de connexion.  
  
```  
DSN={MyDataSourceName};UID={MyUserID};PWD={MyServerPassword};UIDDBMS={MyDBMSUserID};PWDDBMS={MyDBMSUserPassword};  
```  
  
 Le mot clé **DSN** (Data Source Name) nomme la source de données, les mots clés **UID** et **PWD** spécifient l’identifiant et le mot de passe de l’utilisateur pour le serveur, ainsi que les mots clés **UIDDBMS** et **PWDDBMS** spécifier l’identifiant et le mot de passe de l’utilisateur pour le DBMS. Notez que le semi-remorque final est facultatif. **SQLDriverConnect** analyse cette chaîne; utilise le nom de source de données XYZ Corp pour récupérer des informations de connexion supplémentaires à partir du système, telles que l’adresse du serveur; et se connecte au serveur et au DBMS à l’aide des identifiants et mots de passe spécifiés.  
  
 Les paires de mots-clés de **SQLDriverConnect** doivent suivre certaines règles de syntaxe. Les mots-clés et leurs valeurs ne devraient pas contenir le **[]{}(),;? Des \*personnages.** La valeur du mot clé **DSN** ne peut pas se composer uniquement de blancs et ne doit pas contenir de blancs de premier plan. En raison de la grammaire du registre, les mots\\clés et les noms de source de données ne peuvent pas contenir le caractère de barre oblique inverse. Les espaces ne sont pas autorisés autour du signe égal dans la paire de valeur de mot-clé.  
  
 Le mot clé **FILEDSN** peut être utilisé lors d’un appel à **SQLDriverConnect** pour spécifier le nom d’un fichier qui contient des informations sur les sources de données (voir [Connecting Using File Data Sources](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md), plus tard dans cette section). Le mot clé **SAVEFILE** peut être utilisé pour spécifier le nom d’un fichier .dsn dans lequel les paires de mots clés d’une connexion réussie effectuée par l’appel à **SQLDriverConnect** seront enregistrées. Pour plus d’informations sur les sources de données de fichiers, consultez la description de la fonction [SQLDriverConnect.](../../../odbc/reference/syntax/sqldriverconnect-function.md)
