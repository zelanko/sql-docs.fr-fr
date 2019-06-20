---
title: Les données Unicode | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 74de6c44aaf109a434f0cf76c6902abfba92efe1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305769"
---
# <a name="unicode-data"></a>Données Unicode
Types de données SQL Unicode sont fournis pour décrire les données qui se trouvent au format Unicode en mode natif sur le SGBD. Un type de données Unicode de C est fourni pour permettre à une application lier des données dans une mémoire tampon Unicode. Le Gestionnaire de pilotes peuvent convertir des données d’un type Unicode C (SQL_C_WCHAR) pour le rendre fonction avec un pilote ANSI.  
  
 Une application ODBC 3.0 ou 2. *x* application créera toujours une liaison aux types de données ANSI. Pour des performances optimales, une application de ODBC 3.5 (ou version ultérieure) doit lier au type de données C ANSI si le type de colonne SQL est la norme ANSI et doit être lié au type de données Unicode C si le type de colonne SQL est Unicode.  
  
 Les indicateurs de type SQL Unicode sont SQL_WCHAR, SQL_WVARCHAR et SQL_WLONGVARCHAR. Les données SQL_WCHAR ont une longueur de chaîne fixe, tandis que SQL_WVARCHAR a une longueur variable avec un maximum de déclaré et SQL_WLONGVARCHAR a une longueur variable avec une valeur maximale dépend de la source de données.  
  
 L’indicateur de type C Unicode est SQL_C_WCHAR. Il s’agit de la valeur par défaut pour chacun des indicateurs de type SQL Unicode. Tous les types SQL peuvent être convertis en SQL_C_WCHAR, et SQL_C_WCHAR peut être converti à tous les types SQL. Une application peut récupérer des données de trois manières :  
  
-   Récupérer les données en tant que SQL_C_CHAR.  
  
-   Récupérer les données en tant que SQL_C_WCHAR.  
  
-   Déclarer les données en tant que SQL_C_TCHAR. Il s’agit d’une macro qui insère SQL_C_WCHAR si l’application est compilée dans une application Unicode ou insère SQL_C_CHAR s’il est compilé en tant qu’une application ANSI.  
  
 SQL_C_TCHAR est déclarée dans une fonction comme suit :  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 Lorsque l’application est compilée comme une application Unicode, le *ValueType* argument sera remplacé SQL_C_TCHAR à SQL_C_WCHAR. Lorsque l’application est compilée en tant qu’une application ANSI, la *ValueType* argument SQL_C_CHAR \\mb1\instance1 sera remplacé.  
  
 Pilotes Unicode doivent prendre encore en charge ANSI les types de données SQL_CHAR. Si une application fonctionne avec un pilote Unicode se lie à SQL_CHAR, le Gestionnaire de pilotes ne mappera pas les données SQL_CHAR en SQL_WCHAR. Le pilote Unicode doit accepter les données SQL_CHAR.  
  
 Le Gestionnaire de pilotes stocke les pilotes et les noms de source de données au format Unicode et les mappe vers ANSI en fonction des besoins. Si un caractère Unicode ne peut pas être mappé à un caractère ANSI (comme peut se produire si les caractères à partir d’une page de codes qui n’est pas la page de code natif de l’ordinateur sont utilisés dans les noms de source de données et de pilote), les caractères qui n’a pas pu être convertis. sont représentées par un sup de caractère par défaut plied par le système.
