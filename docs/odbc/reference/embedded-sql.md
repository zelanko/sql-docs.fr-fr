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
ms.openlocfilehash: 6a7fa2b3105aedee6cb054c5d5dfa76f3c430f35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915423"
---
# <a name="embedded-sql"></a>Embedded SQL
La première technique pour envoyer des instructions SQL au SGBD est Embedded SQL. Étant donné que SQL n’utilise pas de variables et d’instructions de contrôle de workflow, il est souvent utilisé comme sous-langage de base de données qui peut être ajouté à un programme écrit dans un langage de programmation conventionnel, tel que C ou COBOL. Il s’agit d’une idée centrale d’Embedded SQL : placer des instructions SQL dans un programme écrit dans un langage de programmation hôte. Brièvement, les techniques suivantes sont utilisées pour incorporer des instructions SQL dans un langage hôte :  
  
-   Les instructions SQL incorporées sont traitées par un précompilateur SQL spécial. Toutes les instructions SQL commencent par un introducteur et se terminent par un terminateur, qui marquent toutes les deux l’instruction SQL pour le précompilateur. L’introducteur et le terminateur varient en fonction du langage hôte. Par exemple, l’introducteur est « EXEC SQL » en C et « &SQL ( » dans MUMPS, et le terminateur est un point-virgule (;) en C et une parenthèse fermante dans MUMPS.  
  
-   Les variables du programme d’application, appelées variables hôtes, peuvent être utilisées dans des instructions SQL incorporées là où les constantes sont autorisées. Elles peuvent être utilisées en entrée pour adapter une instruction SQL à une situation particulière et à la sortie pour recevoir les résultats d’une requête.  
  
-   Les requêtes qui retournent une seule ligne de données sont gérées avec une instruction SELECT Singleton ; Cette instruction spécifie à la fois la requête et les variables hôtes dans lesquelles les données doivent être retournées.  
  
-   Les requêtes qui retournent plusieurs lignes de données sont gérées avec des curseurs. Un curseur effectue le suivi de la ligne actuelle dans un jeu de résultats. L’instruction DECLARE CURSOR définit la requête, l’instruction OPEN commence le traitement de la requête, l’instruction FETCH extrait des lignes de données successives et l’instruction CLOSE termine le traitement des requêtes.  
  
-   Lorsqu’un curseur est ouvert, les instructions Update et DELETE positionnées peuvent être utilisées pour mettre à jour ou supprimer la ligne actuellement sélectionnée par le curseur.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Exemple Embedded SQL](../../odbc/reference/embedded-sql-example.md)  
  
-   [Compilation d’un programme Embedded SQL](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [SQL statique](../../odbc/reference/static-sql.md)  
  
-   [SQL dynamique](../../odbc/reference/dynamic-sql.md)
