---
title: Données Unicode (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], data
- data types [ODBC], Unicode
- C data types [ODBC], Unicode
- SQL data types [ODBC], Unicode
ms.assetid: abc28718-e6d9-49fb-97ff-402d50c3c375
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 73ea9035b05f04fec1527ca2aa98531a807db8cf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307396"
---
# <a name="unicode-data"></a>Données Unicode
Les types de données SQL Unicode sont fournis pour décrire les données qui résident dans Unicode natif sur le DBMS. Un type de données C Unicode est fourni pour permettre à une application de lier les données à un tampon Unicode. Le Driver Manager peut convertir les données d’un type Unicode C (SQL_C_WCHAR) pour les faire fonctionner avec un pilote ANSI.  
  
 Un ODBC 3.0 ou 2. *x* application se liera toujours aux types de données ANSI. Pour des performances optimales, une application ODBC 3.5 (ou plus) doit se lier au type de données ANSI C si le type de colonne SQL est ANSI, et doit se lier au type de données Unicode C si le type de colonne SQL est Unicode.  
  
 Les indicateurs de type SQL Unicode sont SQL_WCHAR, SQL_WVARCHAR et SQL_WLONGVARCHAR. SQL_WCHAR données a une longueur fixe de chaîne, tandis que SQL_WVARCHAR a une longueur variable avec un maximum déclaré et SQL_WLONGVARCHAR a une longueur variable avec un maximum qui dépend de la source de données.  
  
 L’indicateur de type C Unicode est SQL_C_WCHAR. Il s’agit de la valeur par défaut de chacun des indicateurs de type SQL Unicode. Tous les types SQL peuvent être convertis en SQL_C_WCHAR, et SQL_C_WCHAR peuvent être convertis en tous les types SQL. Une application peut récupérer des données de l’une des trois façons :  
  
-   Récupérez les données comme SQL_C_CHAR.  
  
-   Récupérez les données comme SQL_C_WCHAR.  
  
-   Déclarez les données comme SQL_C_TCHAR. Il s’agit d’une macro qui insère SQL_C_WCHAR si l’application est compilée sous forme d’application Unicode ou insère SQL_C_CHAR si elle est compilée comme une application ANSI.  
  
 SQL_C_TCHAR est déclarée dans une fonction comme suit:  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 Lorsque l’application est compilée sous forme d’application Unicode, l’argument *ValueType* passerait de SQL_C_TCHAR à SQL_C_WCHAR. Lorsque la demande est compilée sous forme d’application ANSI, l’argument *ValueType* serait modifié pour SQL_C_CHAR.  
  
 Les conducteurs d’Unicode doivent toujours prendre en charge les types de données ANSI, y compris SQL_CHAR. Si une application travaillant avec un pilote Unicode se lie à SQL_CHAR, le gestionnaire de conducteur ne cartographiera pas les données SQL_CHAR pour SQL_WCHAR. Le pilote Unicode doit accepter les données SQL_CHAR.  
  
 Le Driver Manager stocke les noms des chauffeurs et des DSN dans Unicode et les cartographie à l’ANSI au besoin. Si un personnage Unicode ne peut pas être cartographié sur un personnage DE l’ANSI (comme cela peut se produire si les caractères d’une page de code qui n’est pas la page de code native de l’ordinateur sont utilisés dans les noms du pilote et DSN), les caractères qui ne pourraient pas être convertis sont représentés par un personnage par défaut fourni par le système.
