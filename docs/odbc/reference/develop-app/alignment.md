---
title: Alignement Microsoft Docs
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
ms.openlocfilehash: 205cc3ff95dd60db215150f46ae894fbb99bd9ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288604"
---
# <a name="alignment"></a>Alignment
Les problèmes d’alignement dans une application ODBC ne sont généralement pas différents de ce qu’ils sont dans toute autre application. Autrement dit, la plupart des applications ODBC ont peu ou pas de problèmes avec l’alignement. Les pénalités pour ne pas aligner les adresses varient selon le matériel et le système d’exploitation et peuvent être aussi mineures qu’une légère pénalité de performance ou aussi importante qu’une erreur fatale en temps de fonctionnement. Par conséquent, les applications ODBC, et les applications ODBC portables en particulier, devraient prendre soin d’aligner correctement les données.  
  
 Un exemple de quand les applications ODBC rencontrent des problèmes d’alignement est quand ils allouent un grand bloc de mémoire et lient différentes parties de cette mémoire aux colonnes dans un ensemble de résultat. Cela est plus susceptible de se produire lorsqu’une application générique doit déterminer la forme d’un résultat réglé au moment de l’exécution et allouer et lier la mémoire en conséquence.  
  
 Supposons, par exemple, qu’une application exécute une instruction **SELECT** saisie par l’utilisateur et qu’elle récupère les résultats de cette déclaration. Étant donné que la forme de cet ensemble de résultats n’est pas connue lorsque le programme est écrit, l’application doit déterminer le type de chaque colonne après la création de l’ensemble de résultat et lier la mémoire en conséquence. La façon la plus simple de le faire est d’allouer un grand bloc de mémoire et de lier différentes adresses dans ce bloc à chaque colonne. Pour accéder aux données dans une colonne, l’application projette la mémoire liée à cette colonne.  
  
 Le diagramme suivant montre un ensemble de résultats d’échantillon et comment un bloc de mémoire pourrait être lié à elle en utilisant le type de données C par défaut pour chaque type de données SQL. Chaque "X" représente un seul byte de mémoire. (Cet exemple ne montre que les tampons de données qui sont liés aux colonnes. Ceci est fait pour la simplicité. Dans le code réel, les tampons de longueur/indicateur doivent également être alignés.)  
  
 ![Liaison par défaut du type de données C au type de données SQL](../../../odbc/reference/develop-app/media/pr24.gif "pr24")  
  
 En supposant que les adresses liées sont stockées dans le tableau *d’adresse,* l’application utilise les expressions suivantes pour accéder à la mémoire liée à chaque colonne :  
  
```  
(SQLCHAR *)       Address[0]  
(SQLSMALLINT *)   Address[1]  
(SQLINTEGER *)    Address[2]  
```  
  
 Notez que les adresses liées aux deuxième et troisième colonnes commencent sur des octets impairs et que l’adresse liée à la troisième colonne n’est pas divisible par quatre, qui est la taille d’un SDWORD. Sur certaines machines, ce ne sera pas un problème; sur d’autres, il causera une légère pénalité de performance; sur d’autres encore, il va causer une erreur fatale de temps d’exécution. Une meilleure solution serait d’aligner chaque adresse liée sur sa limite d’alignement naturel. En supposant que ce soit 1 pour un UCHAR, 2 pour un SWORD, et 4 pour un SDWORD, cela donnerait le résultat montré dans l’illustration suivante, où un "X" représente un byte de mémoire qui est utilisé et un "O" représente un sac de mémoire qui n’est pas utilisé.  
  
 ![Liaison par alignement naturel de limite](../../../odbc/reference/develop-app/media/pr25.gif "pr25")  
  
 Bien que cette solution n’utilise pas toute la mémoire de l’application, elle ne rencontre aucun problème d’alignement. Malheureusement, il faut une bonne quantité de code pour implémenter cette solution, car chaque colonne doit être alignée individuellement en fonction de son type. Une solution plus simple consiste à aligner toutes les colonnes sur la taille de la plus grande limite d’alignement, qui est de 4 dans l’exemple indiqué dans l’illustration suivante.  
  
 ![Liaison par alignement de la plus grande limite](../../../odbc/reference/develop-app/media/pr26.gif "pr26")  
  
 Bien que cette solution laisse de plus grands trous, le code pour l’implémenter est relativement simple et rapide. Dans la plupart des cas, cela compense la pénalité payée en mémoire inutilisée. Pour un exemple qui utilise cette méthode, voir [Utiliser SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).
