---
title: SQL intégré ( Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ad6fd2753d026f026d72a7aa8f68d5d48ce03cb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306672"
---
# <a name="embedded-sql"></a>Embedded SQL
La première technique d’envoi des relevés SQL au DBMS est intégrée SQL. Étant donné que SQL n’utilise pas de variables et de relevés de contrôle du flux, il est souvent utilisé comme sous-langage de base de données qui peut être ajouté à un programme écrit dans un langage de programmation classique, comme C ou COBOL. Il s’agit d’une idée centrale de SQL intégré: placer des déclarations SQL dans une émission écrite dans un langage de programmation hôte. En bref, les techniques suivantes sont utilisées pour intégrer les déclarations SQL dans une langue d’hôte:  
  
-   Les relevés SQL intégrés sont traités par un précompatateur SQL spécial. Toutes les déclarations SQL commencent par un introducteur et se terminent par un terminateur, qui signalent tous les deux la déclaration SQL pour le précompiler. L’introducteur et le terminateur varient selon la langue d’accueil. Par exemple, l’introducteur est «EXEC SQL» en C et «&SQL(» dans MUMPS, et le terminateur est un point-virgule (;) dans C et une parenthèse droite dans MUMPS.  
  
-   Les variables du programme d’application, appelées variables hôtes, peuvent être utilisées dans les relevés SQL intégrés partout où les constantes sont autorisées. Ceux-ci peuvent être utilisés sur l’entrée pour adapter une déclaration SQL à une situation particulière et sur la sortie pour recevoir les résultats d’une requête.  
  
-   Les requêtes qui renvoient une seule série de données sont traitées avec une déclaration unique; cette déclaration spécifie à la fois la requête et les variables hôtes dans lesquelles retourner les données.  
  
-   Les requêtes qui renvoient plusieurs rangées de données sont traitées avec des curseurs. Un curseur garde une trace de la ligne actuelle dans un ensemble de résultats. La déclaration DE DECLARE CURSOR définit la requête, l’instruction OPEN commence le traitement des requêtes, la déclaration FETCH récupère les lignes successives de données, et l’instruction CLOSE met fin au traitement des requêtes.  
  
-   Bien qu’un curseur soit ouvert, les instructions de mise à jour et de suppression positionnées peuvent être utilisées pour mettre à jour ou supprimer la ligne actuellement sélectionnée par le curseur.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Exemple Embedded SQL](../../odbc/reference/embedded-sql-example.md)  
  
-   [Compilation d’un programme Embedded SQL](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [SQL statique](../../odbc/reference/static-sql.md)  
  
-   [SQL dynamique](../../odbc/reference/dynamic-sql.md)
