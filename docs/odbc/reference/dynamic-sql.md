---
title: SQL dynamique | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbecd1d6db1d5ed77082253f6a6a57a96ceec4d1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62628695"
---
# <a name="dynamic-sql"></a>SQL dynamique
Bien que SQL statique fonctionne bien dans de nombreuses situations, il existe une classe d’applications dans lequel l’accès aux données ne peut pas être déterminé à l’avance. Par exemple, qu'une feuille de calcul permet à un utilisateur à entrer une requête, puis envoie à la feuille de calcul au SGBD pour récupérer des données. Évidemment, le contenu de cette requête ne peut pas être connu au programmeur lorsque le programme de feuille de calcul est écrit.  
  
 Pour résoudre ce problème, la feuille de calcul utilise une forme de SQL incorporée appelée SQL dynamique. Contrairement à des instructions SQL statiques, qui sont codées en dur dans le programme, les instructions SQL dynamiques peuvent être générées au moment de l’exécution et placées dans une variable d’hôte de chaîne. Ils sont ensuite envoyées au SGBD pour traitement. Étant donné que le SGBD doit générer un plan d’accès en cours d’exécution pour les instructions SQL dynamiques, SQL dynamique est généralement plus lent que SQL statique. Lorsqu’un programme contenant des instructions SQL dynamiques est compilé, les instructions SQL dynamiques ne sont pas supprimées du programme, comme dans SQL statique. Au lieu de cela, ils sont remplacés par un appel de fonction qui transmet l’instruction au SGBD ; les instructions SQL statiques dans le même programme sont traitées normalement.  
  
 La façon la plus simple d’exécuter une instruction SQL dynamique est avec une instruction EXECUTE IMMEDIATE. Cette instruction transmet l’instruction SQL au SGBD pour la compilation et l’exécution.  
  
 L’un des inconvénients de l’instruction EXECUTE IMMEDIATE sont que le SGBD doit passer par chacune des cinq étapes de traitement d’une instruction SQL chaque fois que l’instruction est exécutée. La surcharge impliquée dans ce processus peut être significative si de nombreuses instructions sont exécutées de manière dynamique, et il est inutile si ces instructions sont similaires. Pour résoudre ce problème, SQL dynamique offre une version optimisée d’exécution appelé l’exécution préparée, qui utilise les étapes suivantes :  
  
1.  Le programme construit une instruction SQL dans une mémoire tampon, comme il le fait pour l’instruction EXECUTE IMMEDIATE. Au lieu de variables de l’hôte, un point d’interrogation ( ?) peuvent être remplacée par une constante n’importe où dans le texte d’instruction pour indiquer qu’une valeur pour la constante sera fournie plus loin. Le point d’interrogation est appelé un marqueur de paramètre.  
  
2.  Le programme transmet l’instruction SQL au SGBD avec une instruction PREPARE, les demandes que le SGBD analyse, valide et optimiser l’instruction et de générer une exécution planifier. Le programme utilise ensuite une instruction EXECUTE (pas une instruction EXECUTE IMMEDIATE) pour exécuter l’instruction PREPARE ultérieurement. Il transmet les valeurs de paramètre pour l’instruction via une structure de données spéciale appelée SQLDA ou exposition de données SQL.  
  
3.  Le programme peut utiliser l’instruction EXECUTE à plusieurs reprises, en fournissant des valeurs de paramètre différentes chaque fois que l’instruction dynamique est exécutée.  
  
 Exécution préparée n’est toujours pas le même que SQL statique. Dans SQL statique, les quatre premières étapes de traitement d’une instruction SQL lieu au moment de la compilation. Dans l’exécution préparée, ces étapes sont toujours effectuées au moment de l’exécution, mais elles sont exécutées qu’une seule fois ; exécution du plan a lieu uniquement lorsque EXECUTE est appelée. Cela permet d’éliminer certains des inconvénients de performances inhérentes à l’architecture de code SQL dynamique. L’illustration suivante montre les différences entre SQL statique, SQL dynamique avec l’exécution immédiate et SQL dynamique avec l’exécution préparée.
