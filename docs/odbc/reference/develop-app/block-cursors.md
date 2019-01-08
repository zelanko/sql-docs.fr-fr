---
title: Les curseurs de bloc | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 1a92b5d8-7c6e-4ce5-8c99-600a387026aa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc62e7b5225c434bac33630f2f0cf8f39c72bfc9
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52504676"
---
# <a name="block-cursors"></a>Curseurs de bloc
De nombreuses applications passent beaucoup de temps à amener les données sur le réseau. Partie de ce temps est passé en fait acheminer les données sur le réseau et partie de celui-ci est passé sur réseau de surcharge, telles que l’appel lancé par le pilote pour demander une ligne de données. L’heure de ce dernier peut être réduit si l’application effectue une utilisation efficace de *bloc,* ou *fat,* *curseurs,* qui peut retourner plusieurs lignes à la fois.  
  
 Une application always a la possibilité d’utiliser un curseur de bloc. Sur les sources de données à partir de laquelle qu’une seule ligne à la fois peut être extraites, les curseurs de bloc doivent être simulées dans le pilote. Cela est possible en effectuant plusieurs extractions de ligne unique. Bien que cela soit peu probable fournir les gains de performances, il ouvre des opportunités pour les applications. De telles applications puis subit des augmentations de performances comme SGBD implémente des curseurs de bloc en mode natif et les exposent pas les pilotes associés à ces SGBD.  
  
 Les lignes retournées dans une seule extraction avec un curseur de bloc sont appelés les *ensemble de lignes*. Il est important de ne pas confondre l’ensemble de lignes avec le jeu de résultats. Le jeu de résultats est conservé à la source de données, tandis que l’ensemble de lignes est conservée dans les mémoires tampons d’application. Alors que le jeu de résultats est fixe, l’ensemble de lignes n’est pas, il change de position contenus et chaque fois un nouvel ensemble de lignes est extraites. Tout comme un curseur de la ligne unique, tels que les points de curseur avant uniquement SQL traditionnels à une ligne en cours, un curseur de bloc pointe vers l’ensemble de lignes, ce qui peut être considérée comme *lignes actuelles*.  
  
 Pour effectuer des opérations qui fonctionnent sur une seule ligne lorsque plusieurs lignes qui ont été extraites, l’application doit tout d’abord indiquer quelle ligne est la ligne actuelle. La ligne actuelle est requis par les appels à **SQLGetData** et positionné mise à jour et supprimer des instructions. Lorsqu’un curseur de bloc retourne tout d’abord un ensemble de lignes, la ligne actuelle est la première ligne de l’ensemble de lignes. Pour modifier la ligne actuelle, l’application appelle **SQLSetPos** ou **SQLBulkOperations** (mettre à jour en signet). L’illustration suivante montre la relation entre le jeu de résultats ensemble de lignes, ligne actuelle, ensemble de lignes du curseur et curseur de bloc. Pour plus d’informations, consultez [à l’aide des curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md), plus loin dans cette section, et [positionné instructions Update et Delete](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) et [la mise à jour des données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
 ![Extraction des suivante, avant, les premier et dernier ensembles de lignes](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 Si un curseur est un curseur de bloc est indépendante de s’il s’agit à défilement. Par exemple, l’essentiel du travail dans une application de rapports est passé à récupérer et de l’impression de lignes. Pour cette raison, il sont réalisées plus rapidement avec un type avant uniquement, curseur de bloc. Elle utilise un curseur avant uniquement pour éviter les dépenses liées à un curseur de défilement et un curseur de bloc pour réduire le trafic réseau.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Liaison de colonnes pour une utilisation avec des curseurs de bloc](../../../odbc/reference/develop-app/binding-columns-for-use-with-block-cursors.md)  
  
-   [Utilisation de curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md)  
  
-   [Tableau d’état des lignes](../../../odbc/reference/develop-app/row-status-array.md)
