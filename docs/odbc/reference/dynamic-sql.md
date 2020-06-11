---
title: SQL dynamique | Microsoft Docs
ms.custom: ''
ms.date: 06/03/2020
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
ms.openlocfilehash: fa4ac69602761f7c2a8d28e56db76bbfc39fc753
ms.sourcegitcommit: dc6ea6665cd2fb58a940c722e86299396b329fec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84423253"
---
# <a name="dynamic-sql"></a>SQL dynamique
Bien que SQL statique fonctionne bien dans de nombreux cas, il existe une classe d’applications dans laquelle l’accès aux données ne peut pas être déterminé à l’avance. Par exemple, supposons qu’une feuille de calcul permette à un utilisateur d’entrer une requête, que la feuille de calcul envoie ensuite au SGBD pour récupérer des données. Le contenu de cette requête ne peut évidemment pas être connu du programmeur lors de l’écriture du programme de feuille de calcul.  
  
 Pour résoudre ce problème, la feuille de calcul utilise une forme de SQL incorporé appelée SQL dynamique. Contrairement aux instructions SQL statiques, qui sont codées en dur dans le programme, les instructions SQL dynamiques peuvent être générées au moment de l’exécution et placées dans une variable hôte de type chaîne. Ils sont ensuite envoyés au SGBD pour traitement. Étant donné que le SGBD doit générer un plan d’accès au moment de l’exécution pour les instructions SQL dynamiques, le SQL dynamique est généralement plus lent que SQL statique. Lorsqu’un programme contenant des instructions SQL dynamiques est compilé, les instructions SQL dynamiques ne sont pas supprimées du programme, comme dans le SQL statique. Au lieu de cela, ils sont remplacés par un appel de fonction qui passe l’instruction au SGBD ; les instructions SQL statiques dans le même programme sont traitées normalement.  
  
 La façon la plus simple d’exécuter une instruction SQL dynamique est d’utiliser une instruction EXECUTe immediate. Cette instruction passe l’instruction SQL au SGBD pour la compilation et l’exécution.  
  
 L’un des inconvénients de l’instruction EXECUTe Immediate est que le SGBD doit passer par chacune des cinq étapes de traitement d’une instruction SQL chaque fois que l’instruction est exécutée. La surcharge impliquée dans ce processus peut être significative si de nombreuses instructions sont exécutées de manière dynamique, et c’est un gaspillage si ces instructions sont similaires. Pour résoudre ce problème, SQL dynamique offre une forme d’exécution optimisée appelée exécution préparée, qui utilise les étapes suivantes :  
  
1.  Le programme construit une instruction SQL dans une mémoire tampon, comme c’est le cas pour l’instruction EXECUTe immediate. Au lieu de variables hôtes, un point d’interrogation ( ?) peut se substituer à une constante n’importe où dans le texte de l’instruction pour indiquer qu’une valeur pour la constante sera fournie ultérieurement. Le point d’interrogation est appelé comme marqueur de paramètre.  
  
2.  Le programme passe l’instruction SQL au SGBD à l’aide d’une instruction PREPARe, qui demande que le SGBD analyse, valide et optimise l’instruction et génère un plan d’exécution pour celui-ci. Le programme utilise ensuite une instruction EXECUTe (et non une instruction EXECUTe immediate) pour exécuter l’instruction PREPARe ultérieurement. Elle transmet les valeurs de paramètres de l’instruction par le biais d’une structure de données spéciale appelée zone de données SQL ou SQLDA.  
  
3.  Le programme peut utiliser l’instruction EXECUTe à plusieurs reprises, en fournissant des valeurs de paramètre différentes chaque fois que l’instruction dynamique est exécutée.  
  
 L’exécution préparée n’est toujours pas la même que SQL statique. Dans le SQL statique, les quatre premières étapes du traitement d’une instruction SQL sont effectuées au moment de la compilation. Dans l’exécution préparée, ces étapes ont toujours lieu au moment de l’exécution, mais elles ne sont exécutées qu’une seule fois. l’exécution du plan n’a lieu que lorsque l’instruction EXECUTE est appelée. Cela permet d’éliminer certains des inconvénients en matière de performances inhérents à l’architecture du SQL dynamique.
