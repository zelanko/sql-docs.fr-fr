---
title: Informations de connexion spécifiques au pilote | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305789"
---
# <a name="driver-specific-connection-information"></a>Informations de connexion spécifiques du pilote
**SQLConnect** suppose qu’un nom de source de données, un ID d’utilisateur et un mot de passe sont suffisants pour se connecter à une source de données et que toutes les autres informations de connexion peuvent être stockées sur le système. Ce n’est souvent pas le cas. Par exemple, un pilote peut avoir besoin d’un ID d’utilisateur et d’un mot de passe pour se connecter à un serveur et d’un ID d’utilisateur et d’un mot de passe différents pour se connecter à un SGBD. Étant donné que **SQLConnect** accepte un ID d’utilisateur et un mot de passe uniques, cela signifie que l’autre ID utilisateur et le mot de passe doivent être stockés avec les informations de la source de données sur le système si **SQLConnect** doit être utilisé. Il s’agit d’une violation potentielle de la sécurité et doit être évitée, sauf si le mot de passe est chiffré.  
  
 **SQLDriverConnect** permet au pilote de définir une quantité arbitraire d’informations de connexion dans les paires mot clé/valeur de la chaîne de connexion. Supposons, par exemple, qu’un pilote requiert un nom de source de données, un ID d’utilisateur et un mot de passe pour le serveur, ainsi qu’un ID utilisateur et un mot de passe pour le SGBD. Un programme personnalisé qui utilise toujours la source de données société XYZ peut inviter l’utilisateur à entrer des ID et des mots de passe et créer l’ensemble suivant de paires mot clé/valeur, ou *chaîne de connexion,* à passer à **SQLDriverConnect**:  
  
> [!NOTE]  
>  Si vous vous connectez à un fournisseur de sources de données qui prend en charge l’authentification `Trusted_Connection=yes` Windows, vous devez spécifier à la place de l’ID d’utilisateur et des informations de mot de passe dans la chaîne de connexion.  
  
```  
DSN={MyDataSourceName};UID={MyUserID};PWD={MyServerPassword};UIDDBMS={MyDBMSUserID};PWDDBMS={MyDBMSUserPassword};  
```  
  
 Le mot clé **DSN** (nom de la source de données) nomme la source de données, les mots clés **UID** et **PWD** spécifient l’ID d’utilisateur et le mot de passe du serveur, et les mots clés **UIDDBMS** et **PWDDBMS** spécifient l’ID d’utilisateur et le mot de passe du SGBD. Notez que le point-virgule final est facultatif. **SQLDriverConnect** analyse cette chaîne ; utilise le nom de la source de données XYZ Corp pour récupérer des informations de connexion supplémentaires à partir du système, telles que l’adresse du serveur ; et ouvre une session sur le serveur et le SGBD à l’aide des ID d’utilisateur et des mots de passe spécifiés.  
  
 Les paires mot clé-valeur dans **SQLDriverConnect** doivent respecter certaines règles syntaxiques. Les mots clés et leurs valeurs ne doivent pas contenir les **[]{}(),;? = \*! @** caractères. La valeur du mot clé **DSN** ne peut pas se composer uniquement d’espaces blancs et ne doit pas contenir d’espaces à gauche. En raison de la grammaire du Registre, les mots clés et les noms de sources\\de données ne peuvent pas contenir de barre oblique inverse (). Les espaces ne sont pas autorisés autour du signe égal dans la paire mot clé-valeur.  
  
 Le mot clé **FILEDSN** peut être utilisé dans un appel à **SQLDriverConnect** pour spécifier le nom d’un fichier qui contient des informations sur la source de données (consultez [connexion à l’aide de sources de données de fichiers](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md), plus loin dans cette section). Le mot clé **SaveFile** peut être utilisé pour spécifier le nom d’un fichier. DSN dans lequel les paires mot clé/valeur d’une connexion réussie effectuée par l’appel à **SQLDriverConnect** seront enregistrées. Pour plus d’informations sur les sources de données de fichier, consultez la description de la fonction [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) .
