---
title: Bloquer les curseurs Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fa35888ef93da9648fe6422bdc35ebf9da3a0525
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306350"
---
# <a name="block-cursors"></a>Curseurs de bloc
De nombreuses applications passent beaucoup de temps à apporter des données sur l’ensemble du réseau. Une partie de ce temps est consacrée à apporter les données à travers le réseau, et une partie de celui-ci est consacrée aux frais généraux du réseau, comme l’appel effectué par le conducteur pour demander une série de données. Ce dernier délai peut être réduit si l’application fait un usage efficace des *curseurs* de *bloc,* ou *de graisse,* qui peuvent retourner plus d’une rangée à la fois.  
  
 Une application a toujours la possibilité d’utiliser un curseur de bloc. Sur les sources de données à partir desquelles une seule rangée à la fois peut être récupérée, les curseurs de blocs doivent être simulés dans le conducteur. Cela peut être fait en effectuant plusieurs allers-bas à une seule rangée. Bien qu’il soit peu probable que cela procure des gains de performance, il ouvre des possibilités d’applications. Ces applications connaîtront alors des augmentations de performance à mesure que les DBMS implémentent les curseurs de bloc natifs et que les pilotes associés à ces DBMS les exposent.  
  
 Les lignes retournées en un seul aller chercher avec un curseur de bloc sont appelés le *rowset*. Il est important de ne pas confondre le ligne avec l’ensemble de résultats. L’ensemble de résultat est maintenu à la source de données, tandis que le jeu de ligne est maintenu dans les tampons d’application. Bien que l’ensemble de résultat soit fixé, le jeu de ligne n’est pas - il change de position et de contenu chaque fois qu’un nouvel ensemble de lignes est récupéré. Tout comme un curseur à une seule rangée comme le curseur traditionnel SQL avant seulement pointe vers une rangée actuelle, un curseur de bloc pointe vers le ramage, qui peut être considéré comme des *lignes actuelles*.  
  
 Pour effectuer des opérations qui fonctionnent sur une seule rangée lorsque plusieurs lignes ont été récupérées, l’application doit d’abord indiquer quelle ligne est la ligne actuelle. La ligne actuelle est requise par les appels à **SQLGetData** et les instructions de mise à jour et de suppression positionnées. Lorsqu’un curseur de bloc renvoie pour la première fois un jeu de ligne, la ligne actuelle est la première rangée de la rangée. Pour modifier la ligne actuelle, l’application appelle **SQLSetPos** ou **SQLBulkOperations** (à mettre à jour par signet). L’illustration suivante montre la relation de l’ensemble de résultat, de l’acart, de la ligne actuelle, du curseur encastré et du curseur de bloc. Pour plus d’informations, voir [Using Block Cursors](../../../odbc/reference/develop-app/using-block-cursors.md), plus tard dans cette section, et [Positioned Update and Delete Statements](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) and Update Data with [SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
 ![Extraction des ensembles de lignes suivante, précédente, première et dernière](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 La question de savoir si un curseur est un curseur de bloc est indépendante de savoir si elle est défilementable. Par exemple, la majeure partie du travail d’une application de rapport est consacrée à la récupération et à l’impression de lignes. Pour cette raison, il fonctionnera plus rapidement avec un avant-seulement, curseur de bloc. Il utilise un curseur avant seulement pour éviter les frais d’un curseur défilementable, et un curseur de bloc pour réduire le trafic réseau.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison de colonnes pour une utilisation avec des curseurs de bloc](../../../odbc/reference/develop-app/binding-columns-for-use-with-block-cursors.md)  
  
-   [Utilisation de curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md)  
  
-   [Tableau d’état des lignes](../../../odbc/reference/develop-app/row-status-array.md)
