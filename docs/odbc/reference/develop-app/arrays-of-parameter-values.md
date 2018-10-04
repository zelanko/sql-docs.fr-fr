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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 03479a0187c7720a595b550290a8f5ac8197fa9c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686327"
---
# <a name="arrays-of-parameter-values"></a>Tableaux de valeurs de paramètre
Il est souvent utile pour les applications de passer des tableaux de paramètres. Par exemple, à l’aide de tableaux de paramètres et une commande paramétrable **insérer** instruction, une application peut insérer un nombre de lignes à la fois. Il existe plusieurs avantages à l’utilisation de tableaux. Tout d’abord, le trafic réseau est réduit, car les données pour de nombreuses instructions sont envoyées dans un paquet unique (si la source de données prend en charge les tableaux de paramètres en mode natif). En second lieu, certaines sources de données peuvent exécuter des instructions SQL à l’aide des tableaux plus rapidement que l’exécution le même nombre d’instructions SQL séparées. Enfin, lorsque les données sont stockées dans un tableau, comme c’est souvent le cas pour les données d’écran, l’application peut lier toutes les lignes dans une colonne particulière avec un seul appel à **SQLBindParameter** et les mettre à jour en exécutant une instruction unique.  
  
 Malheureusement, pas de nombreuses sources de données prend en charge les tableaux de paramètres. Toutefois, un pilote peut émuler des tableaux de paramètres en exécutant une instruction SQL une fois pour chaque ensemble de valeurs de paramètre. Cela peut entraîner les augmentations de vitesse, car le pilote peut préparer ensuite l’instruction qu’il prévoit d’exécuter une fois pour chaque jeu de paramètres. Elle peut également entraîner au code d’application plus simple.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Liaison de tableaux de paramètres](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)  
  
-   [Utilisation de tableaux de paramètres](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)
