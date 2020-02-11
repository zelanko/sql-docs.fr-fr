---
title: Fonctions de catalogue | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 232d2e9b7e9eb695a40058075ea511392e464a32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064402"
---
# <a name="catalog-functions"></a>Fonctions de catalogue
Toutes les bases de données ont une structure qui décrit la façon dont les données sont stockées dans la base de données. Par exemple, une base de données de commandes client simple peut avoir la structure présentée dans l’illustration suivante, dans laquelle les colonnes d’ID sont utilisées pour lier les tables.  
  
 ![Présente la structure d'une base de données simple](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Cette structure, ainsi que d’autres informations telles que les privilèges, sont stockées dans un ensemble de tables système nommé le *catalogue* de la base de données, également appelé « *dictionnaire de données*».  
  
 Une application peut découvrir cette structure par le biais d’appels aux *fonctions de catalogue*. Les fonctions de catalogue retournent des informations dans les jeux de résultats et sont généralement implémentées par le biais d’instructions **Select** sur les tables du catalogue. Par exemple, une application peut demander un jeu de résultats contenant des informations sur toutes les tables du système ou sur toutes les colonnes d'une table particulière.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Utilisations des données du catalogue](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Fonctions de catalogue dans ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
