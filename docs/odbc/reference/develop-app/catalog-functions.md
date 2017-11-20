---
title: Fonctions de catalogue | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 497676e6b87b6603d4bc6cb1615bb1b133c7acd4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-functions"></a>Fonctions de catalogue
Toutes les bases de données ont une structure qui décrit la façon dont les données sont stockées dans la base de données. Par exemple, une base de données simple commande peut-être la structure illustrée dans l’illustration suivante, dans lequel les colonnes ID sont utilisés pour lier les tables.  
  
 ![Présente la structure d’une base de données simple](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Cette structure, ainsi que d’autres informations telles que des privilèges, est stockée dans un ensemble de tables système de la base de données *catalogue,* qui est également appelé un *dictionnaire de données*.  
  
 Une application peut détecter cette structure via des appels à la *fonctions de catalogue*. Les fonctions de catalogue retournent des informations dans les jeux de résultats et sont généralement implémentées via **sélectionnez** instructions sur les tables dans le catalogue. Par exemple, une application peut demander un jeu de résultats contenant des informations sur toutes les tables du système ou sur toutes les colonnes d'une table particulière.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Utilise des données de catalogue](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Fonctions de catalogue dans ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)

