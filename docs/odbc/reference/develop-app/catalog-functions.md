---
title: Fonctions de catalogue | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a9ef633c9d5ee19489e8c796e99562ec26ec9d03
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="catalog-functions"></a>Fonctions de catalogue
Toutes les bases de données ont une structure qui décrit la façon dont les données sont stockées dans la base de données. Par exemple, une base de données simple commande peut-être la structure illustrée dans l’illustration suivante, dans lequel les colonnes ID sont utilisés pour lier les tables.  
  
 ![Présente la structure d’une base de données simple](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Cette structure, ainsi que d’autres informations telles que des privilèges, est stockée dans un ensemble de tables système de la base de données *catalogue,* qui est également appelé un *dictionnaire de données*.  
  
 Une application peut détecter cette structure via des appels à la *fonctions de catalogue*. Les fonctions de catalogue retournent des informations dans les jeux de résultats et sont généralement implémentées via **sélectionnez** instructions sur les tables dans le catalogue. Par exemple, une application peut demander un jeu de résultats contenant des informations sur toutes les tables du système ou sur toutes les colonnes d'une table particulière.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Utilisations des données du catalogue](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Fonctions de catalogue dans ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
