---
description: Alignment
title: Alignement | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1402eee289111ca100e80730d8df4a6d0e3299cd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483142"
---
# <a name="alignment"></a>Alignment
Les problèmes d’alignement dans une application ODBC ne sont généralement pas différents de ceux d’une autre application. Autrement dit, la plupart des applications ODBC n’ont que peu ou pas de problèmes d’alignement. Les pénalités pour ne pas aligner les adresses varient en fonction du matériel et du système d’exploitation et peuvent être aussi mineures qu’une légère baisse des performances ou d’une erreur d’exécution irrécupérable. Par conséquent, les applications ODBC et les applications ODBC portables en particulier doivent veiller à aligner correctement les données.  
  
 Un exemple de cas où des applications ODBC rencontrent des problèmes d’alignement consiste à allouer un grand bloc de mémoire et à lier différentes parties de cette mémoire aux colonnes d’un jeu de résultats. Cela peut se produire lorsqu’une application générique doit déterminer la forme d’un jeu de résultats au moment de l’exécution et allouer et lier la mémoire en conséquence.  
  
 Par exemple, supposons qu’une application exécute une instruction **Select** entrée par l’utilisateur et récupère les résultats de cette instruction. Étant donné que la forme de ce jeu de résultats n’est pas connue lors de l’écriture du programme, l’application doit déterminer le type de chaque colonne après la création du jeu de résultats et la liaison de la mémoire en conséquence. Le moyen le plus simple consiste à allouer un grand bloc de mémoire et à lier différentes adresses dans ce bloc à chaque colonne. Pour accéder aux données d’une colonne, l’application convertit la mémoire liée à cette colonne.  
  
 Le diagramme suivant montre un exemple de jeu de résultats et la façon dont un bloc de mémoire peut être lié à celui-ci à l’aide du type de données C par défaut pour chaque type de données SQL. Chaque « X » représente un seul octet de mémoire. (Cet exemple montre uniquement les mémoires tampons de données qui sont liées aux colonnes. Cette opération est effectuée pour des raisons de simplicité. Dans le code réel, les tampons de longueur/indicateur doivent également être alignés.  
  
 ![Liaison par défaut du type de données C au type de données SQL](../../../odbc/reference/develop-app/media/pr24.gif "pr24")  
  
 En supposant que les adresses liées sont stockées dans le tableau d' *adresses* , l’application utilise les expressions suivantes pour accéder à la mémoire liée à chaque colonne :  
  
```  
(SQLCHAR *)       Address[0]  
(SQLSMALLINT *)   Address[1]  
(SQLINTEGER *)    Address[2]  
```  
  
 Notez que les adresses liées aux deuxième et troisième colonnes commencent sur les octets impair et que l’adresse liée à la troisième colonne n’est pas divisible par quatre, ce qui correspond à la taille d’un SDWORD. Sur certains ordinateurs, cela ne pose pas de problème. sur d’autres, cela entraîne une légère baisse des performances ; sur d’autres encore, cela entraîne une erreur d’exécution irrécupérable. Une meilleure solution consisterait à aligner chaque adresse liée sur sa limite d’alignement naturelle. En supposant que cette valeur est 1 pour un UCHAR, 2 pour un épée et 4 pour un SDWORD, cela donne le résultat indiqué dans l’illustration suivante, où « X » représente un octet de mémoire utilisé et un « O » représente un octet de mémoire qui n’est pas utilisé.  
  
 ![Liaison par alignement naturel de limite](../../../odbc/reference/develop-app/media/pr25.gif "pr25")  
  
 Bien que cette solution n’utilise pas toute la mémoire de l’application, elle ne rencontre pas de problèmes d’alignement. Malheureusement, il faut un peu de code pour implémenter cette solution, car chaque colonne doit être alignée individuellement en fonction de son type. Une solution plus simple consiste à aligner toutes les colonnes sur la taille de la plus grande limite d’alignement, soit 4 dans l’exemple présenté dans l’illustration suivante.  
  
 ![Liaison par alignement de la plus grande limite](../../../odbc/reference/develop-app/media/pr26.gif "pr26")  
  
 Bien que cette solution laisse des trous plus importants, le code permettant de l’implémenter est relativement simple et rapide. Dans la plupart des cas, cela décale la pénalité payée dans la mémoire inutilisée. Pour obtenir un exemple qui utilise cette méthode, consultez [utilisation de SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).
