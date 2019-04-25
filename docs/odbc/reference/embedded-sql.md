---
title: Embedded SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], embedded SQL
- ODBC [ODBC], SQL
- embedded SQL [ODBC]
ms.assetid: 8eee3527-f225-4aa2-bd18-a16bd3ab0fb7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47936b5c085514fca4ecc1c81057ef78a19f05c5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62628462"
---
# <a name="embedded-sql"></a>Embedded SQL
La première technique pour l’envoi d’instructions SQL au SGBD est incorporée SQL. Étant donné que SQL n’utilise pas les variables et les instructions de contrôle de flux, il est souvent utilisé comme une sous-langue de la base de données qui peut être ajoutée à un programme écrit dans un langage de programmation conventionnels, tels que C ou COBOL. Il s’agit d’une idée centrale d’embedded SQL : placer des instructions SQL dans un programme écrit dans un hôte de langage de programmation. En bref, les techniques suivantes sont utilisées pour incorporer des instructions SQL dans un langage hôte :  
  
-   Les instructions SQL incorporées sont traitées par un précompilateur SQL spéciaux. Toutes les instructions SQL commencent par un dispositif d’introduction et se terminent par une marque de fin, les deux affectez-lui un indicateur pour le précompilateur l’instruction SQL. Le dispositif d’introduction et le terminateur varient selon la langue de l’hôte. Par exemple, le dispositif d’introduction est « EXEC SQL » dans C et » & SQL (« dans virus ourlien., et la marque de fin est un point-virgule ( ;) en C et une parenthèse fermante dans virus ourlien.  
  
-   Variables du programme d’application, appelées des variables de l’hôte, peuvent être utilisées dans les instructions SQL incorporées partout où des constantes sont autorisées. Il est utilisable sur ENTRÉE pour adapter une instruction SQL à une situation particulière et de la sortie de recevoir les résultats d’une requête.  
  
-   Requêtes qui retournent une seule ligne de données sont traités avec une instruction SELECT singleton ; Cette instruction spécifie que la requête et les variables de l’hôte dans lequel retourner les données.  
  
-   Requêtes qui retournent plusieurs lignes de données sont gérées avec les curseurs. Un curseur effectue le suivi de la ligne actuelle au sein d’un jeu de résultats. L’instruction DECLARE CURSOR définit la requête, l’instruction OPEN commence le traitement des requêtes, l’instruction FETCH récupère les lignes successives de données et l’instruction CLOSE termine le traitement des requêtes.  
  
-   Lorsqu’un curseur est ouvert, positionnée instructions update et delete positionnées peuvent servir à mettre à jour ou supprimer la ligne actuellement sélectionnée par le curseur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Exemple Embedded SQL](../../odbc/reference/embedded-sql-example.md)  
  
-   [Compilation d’un programme Embedded SQL](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [SQL statique](../../odbc/reference/static-sql.md)  
  
-   [SQL dynamique](../../odbc/reference/dynamic-sql.md)
