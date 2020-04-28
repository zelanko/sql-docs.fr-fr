---
title: Tableaux de valeurs de paramètre | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 9b572c5b-1dfe-40af-bebd-051548ab6d90
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb9389c769e3a7bb0c39959a559531e8051a7bec
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298796"
---
# <a name="arrays-of-parameter-values"></a>Tableaux de valeurs de paramètre
Il est souvent utile pour les applications de passer des tableaux de paramètres. Par exemple, en utilisant des tableaux de paramètres et une instruction **Insert** paramétrable, une application peut insérer plusieurs lignes à la fois. L’utilisation de tableaux présente plusieurs avantages. Tout d’abord, le trafic réseau est réduit, car les données de nombreuses instructions sont envoyées dans un seul paquet (si la source de données prend en charge les tableaux de paramètres en mode natif). Deuxièmement, certaines sources de données peuvent exécuter des instructions SQL à l’aide de tableaux plus rapidement que d’exécuter le même nombre d’instructions SQL distinctes. Enfin, lorsque les données sont stockées dans un tableau, comme c’est souvent le cas pour les données d’écran, l’application peut lier toutes les lignes d’une colonne particulière avec un seul appel à **SQLBindParameter** et les mettre à jour en exécutant une instruction unique.  
  
 Malheureusement, certaines sources de données ne prennent pas en charge les tableaux de paramètres. Toutefois, un pilote peut émuler des tableaux de paramètres en exécutant une fois une instruction SQL pour chaque ensemble de valeurs de paramètre. Cela peut entraîner une augmentation de la vitesse, car le pilote peut ensuite préparer l’instruction qu’il prévoit d’exécuter une fois pour chaque jeu de paramètres. Cela peut également générer un code d’application plus simple.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison de tableaux de paramètres](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)  
  
-   [Utilisation de tableaux de paramètres](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)
