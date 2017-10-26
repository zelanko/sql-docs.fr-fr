---
title: Embedded SQL | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], embedded SQL
- ODBC [ODBC], SQL
- embedded SQL [ODBC]
ms.assetid: 8eee3527-f225-4aa2-bd18-a16bd3ab0fb7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7e27c80832143ff9907878ffc35c9479ce39ce1e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="embedded-sql"></a>Embedded SQL
La première technique pour l’envoi d’instructions SQL au SGBD est incorporée SQL. Étant donné que SQL n’utilise pas les variables et les instructions de flux de contrôle, il est souvent utilisé comme une sous-langue de base de données qui peut être ajoutée à un programme écrit dans un langage de programmation classique, tels que C ou COBOL. Il s’agit d’une idée centrale SQL incorporée : placer des instructions SQL dans un programme écrit dans un hôte de langage de programmation. En bref, les techniques suivantes sont utilisés pour incorporer des instructions SQL dans un langage hôte :  
  
-   Les instructions SQL incorporées sont traitées par un précompilés SQL spéciale. Toutes les instructions SQL commencent par un dispositif d’introduction et se terminent par une marque de fin, qui indicateur de l’instruction SQL pour le précompilés. Le dispositif d’introduction et le terminateur varient selon le langage hôte. Par exemple, le dispositif d’introduction est « EXEC SQL » dans C et « & SQL (« dans virus ourlien., et la marque de fin est un point-virgule ( ;) en C et une parenthèse fermante dans virus ourlien..  
  
-   Variables à partir de l’application, appelées variables de l’hôte, peuvent être utilisées dans les instructions SQL incorporées partout où des constantes sont autorisées. Ils peuvent être utilisés en entrée pour personnaliser une instruction SQL à une situation donnée et de la sortie de recevoir les résultats d’une requête.  
  
-   Requêtes qui retournent une seule ligne de données sont traitées avec une instruction SELECT de singleton ; Cette instruction spécifie que la requête et les variables de l’hôte dans lequel retourner les données.  
  
-   Requêtes qui retournent plusieurs lignes de données sont gérées avec les curseurs. Un curseur effectue le suivi de la ligne active dans un jeu de résultats. L’instruction DECLARE CURSOR définit la requête, l’instruction OPEN commence le traitement de la requête, l’instruction FETCH récupère les lignes successives de données et l’instruction CLOSE termine le traitement des requêtes.  
  
-   Lorsqu’un curseur est ouvert, positionnée instructions update et delete positionnées peuvent servir à mettre à jour ou supprimer la ligne actuellement sélectionnée par le curseur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Exemple SQL incorporé](../../odbc/reference/embedded-sql-example.md)  
  
-   [Compilez un programme SQL incorporé](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [SQL statique](../../odbc/reference/static-sql.md)  
  
-   [Instructions SQL dynamiques](../../odbc/reference/dynamic-sql.md)

