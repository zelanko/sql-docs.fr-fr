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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb801dc532009410055b67031b3e036cc6b9c3d0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306530"
---
# <a name="compiling-an-embedded-sql-program"></a>Compilation d’un programme Embedded SQL
Étant donné qu’un programme SQL incorporé contient une combinaison d’instructions SQL et de langage hôte, il ne peut pas être envoyé directement à un compilateur pour le langage hôte. Au lieu de cela, il est compilé à l’aide d’un processus à étapes. Bien que ce processus diffère du produit au produit, les étapes sont à peu près les mêmes pour tous les produits.  
  
 Cette illustration montre les étapes nécessaires à la compilation d’un programme SQL incorporé.  
  
 ![Étapes de compilation d'un programme SQL incorporé](../../odbc/reference/media/pr02.gif "pr02")  
  
 Cinq étapes sont impliquées dans la compilation d’un programme SQL incorporé :  
  
1.  Le programme EmbeddedSQL est soumis au précompilateur SQL, un outil de programmation. Le précompilateur analyse le programme, recherche les instructions SQL incorporées et les traite. Un précompilateur différent est requis pour chaque langage de programmation pris en charge par le SGBD. Les produits SGBD offrent généralement des précompilations pour une ou plusieurs langues, notamment C, Pascal, COBOL, Fortran, Ada, PL/I et divers langages d’assembly.  
  
2.  Le précompilateur produit deux fichiers de sortie. Le premier fichier est le fichier source, supprimé de ses instructions SQL incorporées. À leur place, le précompilateur remplace les appels aux routines SGBD propriétaires qui fournissent le lien d’exécution entre le programme et le SGBD. En règle générale, les noms et les séquences d’appel de ces routines sont connus uniquement du précompilateur et du SGBD. il ne s’agit pas d’une interface publique pour le SGBD. Le deuxième fichier est une copie de toutes les instructions SQL incorporées utilisées dans le programme. Ce fichier est parfois appelé module de demande de base de données, ou nom DBRM.  
  
3.  La sortie du fichier source du précompilateur est soumise au compilateur standard pour le langage de programmation hôte (tel qu’un compilateur C ou COBOL). Le compilateur traite le code source et produit le code de l’objet comme sortie. Notez que cette étape n’a rien à faire avec le SGBD ou avec SQL.  
  
4.  L’éditeur de liens accepte les modules d’objets générés par le compilateur, les lie à diverses routines de bibliothèque et produit un programme exécutable. Les routines de bibliothèque liées dans le programme exécutable incluent les routines SGBD propriétaires décrites à l’étape 2.  
  
5.  Le module de demande de base de données généré par le précompilateur est soumis à un utilitaire de liaison spécial. Cet utilitaire examine les instructions SQL, les analyse, les valide et les optimise, puis produit un plan d’accès pour chaque instruction. Le résultat est un plan d’accès combiné pour l’ensemble du programme, représentant une version exécutable des instructions SQL incorporées. L’utilitaire de liaison stocke le plan dans la base de données, en lui assignant généralement le nom du programme d’application qui va l’utiliser. L’exécution de cette étape au moment de la compilation ou au moment de l’exécution dépend du SGBD.  
  
 Notez que les étapes utilisées pour compiler un programme SQL incorporé sont très proches de celles décrites précédemment dans [traitement d’une instruction SQL](../../odbc/reference/processing-a-sql-statement.md). En particulier, Notez que le précompilateur sépare les instructions SQL du code de langue de l’hôte, et que l’utilitaire de liaison analyse et valide les instructions SQL et crée les plans d’accès. Dans les SGBD où l’étape 5 a lieu au moment de la compilation, les quatre premières étapes du traitement d’une instruction SQL sont effectuées au moment de la compilation, tandis que la dernière étape (exécution) a lieu au moment de l’exécution. Cela a pour effet de rendre très rapides l’exécution des requêtes dans de tels SGBD.
