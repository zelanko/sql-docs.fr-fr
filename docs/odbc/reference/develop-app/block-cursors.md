---
title: Curseurs de bloc | Microsoft Docs
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
ms.openlocfilehash: 3e0ea6ff655140c979f400f67a59cd7259bac9e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68118817"
---
# <a name="block-cursors"></a>Curseurs de bloc
De nombreuses applications consacrent beaucoup de temps à l’acheminement des données sur le réseau. Une partie de ce temps est passée à placer les données sur le réseau et une partie de celle-ci est consacrée à la surcharge du réseau, telle que l’appel émis par le pilote pour demander une ligne de données. La dernière fois peut être réduite si l’application utilise efficacement des *curseurs* de *bloc* , ou *FAT* , qui peuvent retourner plusieurs lignes à la fois.  
  
 Une application a toujours la possibilité d’utiliser un curseur de bloc. Sur les sources de données à partir desquelles une seule ligne à la fois peut être extraite, les curseurs de bloc doivent être simulés dans le pilote. Pour ce faire, vous pouvez effectuer plusieurs extractions sur une seule ligne. Bien qu’il ne soit pas rare de fournir des gains de performances, il ouvre des opportunités pour les applications. Ces applications subissent alors des performances accrues, car les SGBD implémentent des curseurs de bloc en mode natif et les pilotes associés à ces SGBD les exposent.  
  
 Les lignes retournées dans une extraction unique avec un curseur de bloc sont appelées « *rowset*». Il est important de ne pas confondre l’ensemble de lignes avec le jeu de résultats. Le jeu de résultats est conservé au niveau de la source de données, tandis que l’ensemble de lignes est conservé dans les tampons d’application. Tandis que le jeu de résultats est fixe, l’ensemble de lignes ne change pas de position et de contenu chaque fois qu’un nouvel ensemble de lignes est extrait. Tout comme un curseur à une seule ligne, tel que le curseur avant uniquement SQL traditionnel, pointe vers une ligne actuelle, un curseur de bloc pointe vers l’ensemble de lignes, qui peut être considéré comme des *lignes actuelles*.  
  
 Pour effectuer des opérations qui fonctionnent sur une seule ligne lorsque plusieurs lignes ont été extraites, l’application doit d’abord indiquer la ligne qui est la ligne actuelle. La ligne actuelle est requise par les appels à **SQLGetData** et aux instructions Update et DELETE positionnées. Lorsqu’un curseur de bloc retourne d’abord un ensemble de lignes, la ligne actuelle est la première ligne de l’ensemble de lignes. Pour modifier la ligne actuelle, l’application appelle **SQLSetPos** ou **SQLBulkOperations** (pour effectuer une mise à jour par signet). L’illustration suivante montre la relation entre le jeu de résultats, l’ensemble de lignes, la ligne actuelle, le curseur de l’ensemble de lignes et le curseur de bloc. Pour plus d’informations, consultez [utilisation de curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md), plus loin dans cette section, et [instructions Update et DELETE positionnées](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) et [mise à jour de données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
 ![Extraction des ensembles de lignes suivante, précédente, première et dernière](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 Le fait qu’un curseur soit un curseur de bloc est indépendant de la possibilité de faire défiler. Par exemple, la majeure partie du travail dans une application de rapport est consacrée à la récupération et à l’impression de lignes. C’est la raison pour laquelle elle fonctionnera plus rapidement avec un curseur de bloc avant uniquement. Elle utilise un curseur avant uniquement pour éviter les dépenses d’un curseur de défilement et un curseur de bloc pour réduire le trafic réseau.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison de colonnes pour une utilisation avec des curseurs de bloc](../../../odbc/reference/develop-app/binding-columns-for-use-with-block-cursors.md)  
  
-   [Utilisation de curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md)  
  
-   [Tableau d’état des lignes](../../../odbc/reference/develop-app/row-status-array.md)
