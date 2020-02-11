---
title: Données Unicode | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 899924b5c0847d5f42e383a9e04c33298bb368b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087755"
---
# <a name="unicode-data"></a>Données Unicode
Les types de données Unicode SQL sont fournis pour décrire les données qui résident dans Unicode en mode natif sur le SGBD. Un type de données Unicode C est fourni pour permettre à une application de lier des données à une mémoire tampon Unicode. Le gestionnaire de pilotes peut convertir les données d’un type C Unicode (SQL_C_WCHAR) pour qu’il fonctionne avec un pilote ANSI.  
  
 ODBC 3,0 ou 2. l’application *x* est toujours liée aux types de données ANSI. Pour des performances optimales, une application ODBC 3,5 (ou version ultérieure) doit être liée au type de données ANSI C si le type de colonne SQL est ANSI et doit être lié au type de données C Unicode si le type de colonne SQL est Unicode.  
  
 Les indicateurs de type Unicode SQL sont SQL_WCHAR, SQL_WVARCHAR et SQL_WLONGVARCHAR. SQL_WCHAR données ont une longueur de chaîne fixe, tandis que SQL_WVARCHAR a une longueur variable avec une valeur maximale déclarée et SQL_WLONGVARCHAR a une longueur variable dont la valeur maximale dépend de la source de données.  
  
 L’indicateur de type Unicode C est SQL_C_WCHAR. Il s’agit de la valeur par défaut pour chacun des indicateurs de type Unicode SQL. Tous les types SQL peuvent être convertis en SQL_C_WCHAR et SQL_C_WCHAR peuvent être convertis en tous les types SQL. Une application peut récupérer des données de l’une des trois façons suivantes :  
  
-   Récupérez les données en tant que SQL_C_CHAR.  
  
-   Récupérez les données en tant que SQL_C_WCHAR.  
  
-   Déclarez les données en tant que SQL_C_TCHAR. Il s’agit d’une macro qui insère SQL_C_WCHAR si l’application est compilée en tant qu’application Unicode ou insère SQL_C_CHAR si elle est compilée en tant qu’application ANSI.  
  
 SQL_C_TCHAR est déclaré dans une fonction comme suit :  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 Lorsque l’application est compilée en tant qu’application Unicode, l’argument *ValueType* est modifié de SQL_C_TCHAR en SQL_C_WCHAR. Lorsque l’application est compilée en tant qu’application ANSI, l’argument *ValueType* est remplacé par SQL_C_CHAR.  
  
 Les pilotes Unicode doivent toujours prendre en charge les types de données ANSI, y compris SQL_CHAR. Si une application utilisant un pilote Unicode se lie à SQL_CHAR, le gestionnaire de pilotes ne mappe pas les données SQL_CHAR à SQL_WCHAR. Le pilote Unicode doit accepter les données de SQL_CHAR.  
  
 Le gestionnaire de pilotes stocke les noms de pilote et DSN en Unicode et les mappe à ANSI en fonction des besoins. Si un caractère Unicode ne peut pas être mappé à un caractère ANSI (comme cela peut se produire si les caractères d’une page de codes qui ne sont pas la page de codes native de l’ordinateur sont utilisés dans les noms de pilote et DSN), les caractères qui n’ont pas pu être convertis sont représentés par un sup de caractère par défaut plied par le système.
