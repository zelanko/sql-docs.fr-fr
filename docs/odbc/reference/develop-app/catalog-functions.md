---
title: Fonctions de catalogue (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb28ec6f4ea299dae8737fc707fd53e4d102442d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305200"
---
# <a name="catalog-functions"></a>Fonctions de catalogue
Toutes les bases de données ont une structure qui décrit comment les données seront stockées dans la base de données. Par exemple, une simple base de données sur les commandes de vente peut avoir la structure indiquée dans l’illustration suivante, dans laquelle les colonnes d’identification sont utilisées pour lier les tables.  
  
 ![Présente la structure d'une base de données simple](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Cette structure, ainsi que d’autres informations telles que les privilèges, est stockée dans un ensemble de tables système appelée catalogue de la base de *données,* qui est également connu sous le nom d’un dictionnaire de *données*.  
  
 Une application peut découvrir cette structure grâce à des appels vers les fonctions du *catalogue.* Les fonctions de catalogue retournent les informations dans les ensembles de résultats et sont généralement implémentées par le biais de déclarations **SELECT** contre les tables du catalogue. Par exemple, une application peut demander un jeu de résultats contenant des informations sur toutes les tables du système ou sur toutes les colonnes d'une table particulière.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Utilisations des données du catalogue](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Fonctions de catalogue dans ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
