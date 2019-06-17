---
title: Alignment | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- alignment issues [ODBC]
ms.assetid: 06a01e51-e7a5-495f-aa27-e304b0d005ff
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e4c86fd8fba66e6424b41fa4b80b42fc089e6d64
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63287425"
---
# <a name="alignment"></a>Alignement
Les problèmes d’alignement dans une application ODBC sont généralement pas de différence entre elles se trouvent dans n’importe quel autre application. Autrement dit, la plupart des applications ODBC ont peu ou pas des problèmes avec l’alignement. Les pénalités pour aligner ne pas les adresses varient selon le matériel et le système d’exploitation et peuvent être aussi mineure que légèrement les performances ou comme majeures comme une erreur d’exécution irrécupérable. Par conséquent, les applications ODBC et les applications ODBC portables en particulier, prudence aligner correctement les données.  
  
 Un exemple de lorsque les applications ODBC rencontrent des problèmes d’alignement est lorsqu’ils allouer un grand bloc de mémoire et lier les différentes parties de cette mémoire pour les colonnes dans un jeu de résultats. Il s’agit probablement de se produire lorsqu’une application générique doit déterminer la forme d’un jeu de résultats au moment de l’exécution et allouer et lier de mémoire en conséquence.  
  
 Par exemple, une application exécute un **sélectionnez** instruction entré par l’utilisateur et extrait les résultats de cette instruction. Étant donné que la forme de ce jeu de résultats n’est pas connue lorsque le programme est écrit, l’application doit déterminer le type de chaque colonne une fois que le jeu de résultats est créé et lier de mémoire en conséquence. Pour ce faire, le plus simple consiste à allouer un grand bloc de mémoire et de lier des adresses différentes dans ce bloc à chaque colonne. Pour accéder aux données dans une colonne, l’application effectue un cast de la mémoire liée à cette colonne.  
  
 Le diagramme suivant montre un exemple de résultat défini et comment un bloc de mémoire peut être lié à l’aide du type de données C par défaut pour chaque type de données SQL. Chaque « X » représente un seul octet de mémoire. (Cet exemple montre uniquement les mémoires tampons de données qui sont liées aux colonnes. Pour cela, par souci de simplicité. Dans le code réel, les mémoires tampon de longueur / d’indicateur doivent également être alignées.)  
  
 ![Liaison par type de données C par défaut pour le type de données SQL](../../../odbc/reference/develop-app/media/pr24.gif "pr24")  
  
 En supposant que les adresses liées sont stockés dans le *adresse* array, l’application utilise les expressions suivantes d’accéder à la mémoire associée à chaque colonne :  
  
```  
(SQLCHAR *)       Address[0]  
(SQLSMALLINT *)   Address[1]  
(SQLINTEGER *)    Address[2]  
```  
  
 Notez que les adresses lié à la deuxième et troisième colonnes démarrer sur octets impaire, et que l’adresse lié à la troisième colonne n’est pas divisible par quatre, qui est la taille d’un SDWORD. Sur certains ordinateurs, il s’agit pas d’un problème ; sur d’autres, elle entraîne une baisse des performances légères ; sur d’autres, cela entraînera une erreur d’exécution irrécupérable. Une meilleure solution consisterait à aligner chaque adresse liée sur son alignement naturel de limite. En supposant que la valeur est 1 pour un UCHAR, 2 pour un mot de passe et 4 pour un SDWORD, cela donnerait le résultat illustré dans l’illustration suivante, où un « X » représente un octet de mémoire qui est utilisée et un « O » représente un octet de mémoire qui n’est pas utilisé.  
  
 ![Liaison par alignement naturel de limite](../../../odbc/reference/develop-app/media/pr25.gif "pr25")  
  
 Bien que cette solution n’utilise pas toutes de la mémoire de l’application, elle ne rencontre pas de problèmes d’alignement. Malheureusement, il prend une grande quantité de code pour implémenter cette solution, chaque colonne doit être aligné individuellement en fonction de son type. Une solution plus simple consiste à aligner toutes les colonnes de la taille de la plus grande limite d’alignement, qui est de 4 dans l’exemple illustré dans l’illustration suivante.  
  
 ![Liaison par alignement plus grande limite](../../../odbc/reference/develop-app/media/pr26.gif "pr26")  
  
 Bien que cette solution laisse trous plus volumineux, le code à son implémentation est relativement simple et rapide. Dans la plupart des cas, cela compense la pénalité payée dans la mémoire inutilisée. Pour obtenir un exemple qui utilise cette méthode, consultez [à l’aide de SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).
