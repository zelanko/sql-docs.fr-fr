---
title: SQL dynamique ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], dynamic SQL
- SQL statements [ODBC], embedded SQL
- dynamic SQL [ODBC]
- SQL [ODBC], dynamic SQL
- embedded SQL [ODBC]
ms.assetid: 0bfb9ab7-9c15-4433-93bc-bad8b6c9d287
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 56419723540114f122be2582f0de7c7e7d0c54f3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306687"
---
# <a name="dynamic-sql"></a>SQL dynamique
Bien que sqL statique fonctionne bien dans de nombreuses situations, il existe une catégorie d’applications dans lesquelles l’accès aux données ne peut pas être déterminé à l’avance. Supposons, par exemple, qu’une feuille de calcul permette à un utilisateur d’entrer une requête, que la feuille de calcul envoie ensuite au DBMS pour récupérer des données. Le contenu de cette requête ne peut évidemment pas être connu du programmeur lorsque le programme de feuilles de calcul est écrit.  
  
 Pour résoudre ce problème, la feuille de calcul utilise une forme de SQL intégrée appelée SQL dynamique. Contrairement aux déclarations STATIQUEs SQL, qui sont codées en dur dans le programme, les déclarations SQL dynamiques peuvent être construites au moment de l’exécution et placées dans une variable d’hôte de chaîne. Ils sont ensuite envoyés au DBMS pour traitement. Étant donné que le DBMS doit générer un plan d’accès à l’heure d’exécution pour les déclarations dynamiques sqL, SQL dynamique est généralement plus lent que SQL statique. Lorsqu’un programme contenant des énoncés SQL dynamiques est compilé, les énoncés dynamiques de SQL ne sont pas retirés du programme, comme dans SQL statique. Au lieu de cela, ils sont remplacés par un appel de fonction qui transmet la déclaration à la DBMS; les déclarations statiques SQL dans le même programme sont traitées normalement.  
  
 La façon la plus simple d’exécuter une déclaration SQL dynamique est avec une déclaration EXECUTE IMMEDIATE. Cette déclaration transmet la déclaration SQL à la DBMS pour compilation et exécution.  
  
 Un inconvénient de la déclaration EXECUTE IMMEDIATE est que le DBMS doit passer par chacune des cinq étapes du traitement d’une déclaration SQL chaque fois que la déclaration est exécutée. Les frais généraux impliqués dans ce processus peuvent être importants si de nombreuses déclarations sont exécutées de façon dynamique, et il est inutile si ces déclarations sont similaires. Pour faire face à cette situation, sqL dynamique offre une forme optimisée d’exécution appelée exécution préparée, qui utilise les étapes suivantes:  
  
1.  Le programme construit une déclaration SQL dans un tampon, tout comme il le fait pour la déclaration EXECUTE IMMEDIATE. Au lieu de variables d’hôte, un point d’interrogation (?) peut être remplacé par une constante n’importe où dans le texte de déclaration pour indiquer qu’une valeur pour la constante sera fournie plus tard. Le point d’interrogation est appelé comme marqueur de paramètres.  
  
2.  Le programme transmet la déclaration SQL au DBMS avec une déclaration PREPARE, qui demande que le DBMS analyse, valide et optimise l’énoncé et génère un plan d’exécution pour elle. Le programme utilise ensuite une déclaration EXECUTE (et non une déclaration EXECUTE IMMEDIATE) pour exécuter la déclaration PREPARE ultérieurement. Il transmet les valeurs de paramètres pour l’instruction par l’intermédiaire d’une structure de données spéciale appelée SQL Data Area ou SQLDA.  
  
3.  Le programme peut utiliser l’instruction EXECUTE à plusieurs reprises, fournissant des valeurs de paramètres différentes chaque fois que l’énoncé dynamique est exécuté.  
  
 L’exécution préparée n’est toujours pas la même que la SQL statique. Dans le SQL statique, les quatre premières étapes du traitement d’une déclaration SQL ont lieu au moment de la compilation. Lors de l’exécution préparée, ces étapes ont encore lieu au moment de la course, mais elles ne sont exécutées qu’une seule fois; l’exécution du plan n’a lieu que lorsque l’EXECUTE est appelé. Cela permet d’éliminer certains des inconvénients de performance inhérents à l’architecture de SQL dynamique. L’illustration suivante montre les différences entre SQL statique, SQL dynamique avec exécution immédiate, et SQL dynamique avec exécution préparée.
