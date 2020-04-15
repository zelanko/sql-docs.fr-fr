---
title: Compilation d’un programme SQL intégré (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306530"
---
# <a name="compiling-an-embedded-sql-program"></a>Compilation d’un programme Embedded SQL
Étant donné qu’un programme SQL intégré contient un mélange de SQL et d’instructions linguistiques d’hôte, il ne peut pas être soumis directement à un compilateur pour la langue d’accueil. Au lieu de cela, il est compilé par un processus multistep. Bien que ce processus diffère d’un produit à l’autre, les étapes sont à peu près les mêmes pour tous les produits.  
  
 Cette illustration montre les étapes nécessaires à la compilation d’un programme SQL intégré.  
  
 ![Étapes de compilation d'un programme SQL incorporé](../../odbc/reference/media/pr02.gif "pr02")  
  
 Cinq étapes sont nécessaires à la compilation d’un programme SQL intégré :  
  
1.  Le programme SQL intégré est soumis au précompiler SQL, un outil de programmation. Le précompileur scanne le programme, trouve les relevés SQL intégrés et les traite. Un précompileur différent est nécessaire pour chaque langage de programmation soutenu par le DBMS. Les produits DBMS offrent généralement des précompilateurs pour une ou plusieurs langues, y compris C, Pascal, COBOL, Fortran, Ada, PL/I, et diverses langues d’assemblage.  
  
2.  Le précompileur produit deux fichiers de sortie. Le premier fichier est le fichier source, dépouillé de ses déclarations SQL intégrées. À leur place, le précompiler remplace les appels à des routines DBMS propriétaires qui fournissent le lien de temps d’exécution entre le programme et le DBMS. Typiquement, les noms et les séquences d’appel de ces routines ne sont connus que du précompiler et du DBMS; ils ne sont pas une interface publique pour le DBMS. Le deuxième fichier est une copie de toutes les déclarations SQL intégrées utilisées dans le programme. Ce fichier est parfois appelé module de demande de base de données, ou DBRM.  
  
3.  La sortie du fichier source du précompiler est soumise au compilateur standard pour le langage de programmation hôte (comme un compilateur C ou COBOL). Le compilateur traite le code source et produit du code objet comme sortie. Notez que cette étape n’a rien à voir avec le DBMS ou avec SQL.  
  
4.  Le linker accepte les modules d’objets générés par le compilateur, les relie à diverses routines de bibliothèque et produit un programme exécutable. Les routines de bibliothèque liées au programme exécutable comprennent les routines exclusives DBMS décrites à l’étape 2.  
  
5.  Le module de demande de base de données généré par le précompiler est soumis à un utilitaire de liaison spécial. Cet utilitaire examine les relevés SQL, analyse, valide et les optimise, puis produit un plan d’accès pour chaque relevé. Il en résulte un plan d’accès combiné pour l’ensemble du programme, qui représente une version exécutable des relevés SQL intégrés. Le service public de liaison stocke le plan dans la base de données, en lui attribuant habituellement le nom du programme d’application qui l’utilisera. La question de savoir si cette étape a lieu au moment de la compilation ou de l’exécution dépend du DBMS.  
  
 Notez que les étapes utilisées pour compiler un programme SQL intégré sont très étroitement en corrélation avec les étapes décrites plus tôt dans le [traitement d’une déclaration SQL](../../odbc/reference/processing-a-sql-statement.md). En particulier, notez que le précompilateur sépare les relevés SQL du code de la langue hôte, et que l’utilité contraignante analyse et valide les relevés SQL et crée les plans d’accès. Dans les DBMS où l’étape 5 a lieu au moment de la compilation, les quatre premières étapes du traitement d’une déclaration SQL ont lieu au moment de la compilation, tandis que la dernière étape (exécution) a lieu au moment de la course. Cela a pour effet de rendre l’exécution des requêtes dans ces DBMS très rapidement.
