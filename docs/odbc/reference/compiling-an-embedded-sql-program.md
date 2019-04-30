---
title: Compilation d’un programme SQL incorporé | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- compiling embedded SQL programs [ODBC]
- embedded SQL [ODBC]
ms.assetid: 9e94146a-5b80-4a01-b586-1e03ff05b9ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc8133241ad0b76579e87164350a5c6fe2a39f2e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63186331"
---
# <a name="compiling-an-embedded-sql-program"></a>Compilation d’un programme Embedded SQL
Comme un programme SQL incorporé contient une combinaison d’instructions de langage SQL et l’hôte, il ne peut être envoyé directement à un compilateur pour le langage hôte. Au lieu de cela, il est compilé dans un processus en plusieurs étapes. Bien que ce processus varie d’un produit, les étapes sont à peu près les mêmes pour tous les produits.  
  
 Cette illustration montre les étapes nécessaires pour compiler un programme SQL incorporé.  
  
 ![Étapes de compilation d’un programme SQL incorporé](../../odbc/reference/media/pr02.gif "pr02")  
  
 Cinq étapes sont nécessaires pour la compilation d’un programme SQL incorporé :  
  
1.  Le programme SQL incorporé est soumis au précompilateur SQL, un outil de programmation. Le précompilateur analyse le programme détecte les instructions SQL incorporées et les traite. Un précompilateur différent est requis pour chaque langage de programmation pris en charge par le SGBD. Produits SGBD offrent généralement precompilers pour une ou plusieurs langues, y compris C, Pascal, COBOL, Fortran, Ada, PL / j’et divers langages d’assembly.  
  
2.  Le précompilateur génère deux fichiers de sortie. Le premier fichier est le fichier source, débarrassé des signes de ses instructions SQL incorporées. À leur place, le précompilateur remplace les appels aux routines de SGBD propriétaires qui fournissent le lien de l’exécution entre le programme et le SGBD. En règle générale, les noms et les séquences d’appel de ces routines sont connus uniquement le précompilateur et le SGBD ; ils ne sont pas une interface publique au SGBD. Le deuxième fichier est une copie de toutes les instructions SQL incorporées utilisée dans le programme. Ce fichier est parfois appelé un module de requête de base de données, ou nom DBRM.  
  
3.  La sortie du fichier source à partir du précompilateur est soumise au compilateur standard pour l’hôte de langage (par exemple, un compilateur C ou COBOL) de programmation. Le compilateur traite le code source et produit le code de l’objet en tant que sa sortie. Notez que cette étape n’a rien à voir avec le SGBD ou SQL.  
  
4.  L’éditeur de liens accepte les modules de l’objet générés par le compilateur, les lie avec les différentes routines de bibliothèque et génère un programme exécutable. Les routines de bibliothèque liées dans le programme exécutable incluent les routines de SGBD propriétaires décrits à l’étape 2.  
  
5.  Le module de requête de base de données généré par le précompilateur est soumis à un utilitaire de liaison spéciale. Cet utilitaire examine les instructions SQL, analyse, valide et les optimise et puis génère un plan d’accès pour chaque instruction. Le résultat est un plan d’accès combiné pour la totalité du programme, qui représente une version exécutable de le des instructions SQL incorporées. L’utilitaire de liaison stocke le plan dans la base de données, en lui assignant généralement le nom de l’application qui va l’utiliser. Indique si cette étape a lieu au moment ou le moment de l’exécution de compilation varie selon le SGBD.  
  
 Notez que les étapes utilisées pour compiler un programme SQL incorporé correspondent très étroitement avec les étapes décrites précédemment dans [traitement d’une instruction SQL](../../odbc/reference/processing-a-sql-statement.md). En particulier, notez que le précompilateur sépare les instructions SQL à partir du code de langage hôte, et l’utilitaire de liaison analyse valide les instructions SQL et crée des plans de l’accès. Dans le SGBD où l’étape 5 a lieu au moment de la compilation, les quatre premières étapes de traitement d’une instruction SQL lieu au moment de la compilation, tandis que la dernière étape (exécution) a lieu au moment de l’exécution. Cela a pour effet de rendre l’exécution des requêtes dans ce type SGBD très rapide.
