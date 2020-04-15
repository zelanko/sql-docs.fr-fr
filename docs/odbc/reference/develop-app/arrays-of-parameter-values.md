---
title: Arrays de valeurs paramètres (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298796"
---
# <a name="arrays-of-parameter-values"></a>Tableaux de valeurs de paramètre
Il est souvent utile pour les applications de passer des tableaux de paramètres. Par exemple, à l’aide de tableaux de paramètres et d’une instruction **INSERT** paramétrée, une application peut insérer un certain nombre de lignes à la fois. Il y a plusieurs avantages à utiliser des tableaux. Tout d’abord, le trafic réseau est réduit parce que les données pour de nombreuses déclarations sont envoyées dans un seul paquet (si la source de données prend en charge les tableaux de paramètres natifs). Deuxièmement, certaines sources de données peuvent exécuter des relevés SQL à l’aide de tableaux plus rapidement que l’exécution du même nombre d’instructions SQL distinctes. Enfin, lorsque les données sont stockées dans un tableau, comme c’est souvent le cas pour les données d’écran, l’application peut lier toutes les lignes dans une colonne particulière avec un seul appel à **SQLBindParameter** et les mettre à jour en exécutant une seule déclaration.  
  
 Malheureusement, peu de sources de données prennent en charge les paramètres. Cependant, un pilote peut imiter les tableaux de paramètres en exécutant une déclaration SQL une fois pour chaque ensemble de valeurs de paramètres. Cela peut conduire à des augmentations de vitesse parce que le conducteur peut alors préparer l’instruction qu’il prévoit d’exécuter une fois pour chaque paramètre défini. Il pourrait également conduire à un code d’application plus simple.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison de tableaux de paramètres](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)  
  
-   [Utilisation de tableaux de paramètres](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)
