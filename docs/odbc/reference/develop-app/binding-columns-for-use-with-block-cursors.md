---
title: Liaison de colonnes pour une utilisation avec les curseurs de bloc | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column-wise binding [ODBC]
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- cursors [ODBC], block
- binding columns [ODBC]
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 231beede-cdfa-4e28-8b10-2760b983250f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0ed819643e7ea818fc17c0fa317473afc8f5ca3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007864"
---
# <a name="binding-columns-for-use-with-block-cursors"></a>Liaison de colonnes pour une utilisation avec des curseurs de bloc
Étant donné que les curseurs de bloc retournent plusieurs lignes, les applications qui les utilisent doivent lier un tableau de variables à chaque colonne plutôt qu’une variable unique. Ces tableaux est collectivement regroupés sous le *tampons de l’ensemble de lignes*. Voici les deux styles de liaison :  
  
-   Lier un tableau à chaque colonne. Il s’agit *la liaison* , car chaque structure de données (tableau) contient des données pour une colonne unique.  
  
-   Définir une structure pour contenir les données pour une ligne entière et lier un tableau de ces structures. Il s’agit *la liaison* car chaque structure de données contient les données d’une seule ligne.  
  
 Comme lors de l’application lie les variables uniques aux colonnes, il appelle **SQLBindCol** pour lier les tableaux de colonnes. La seule différence est que les adresses transmises sont des adresses de tableau, les adresses de variables non unique. L’application définit l’attribut d’instruction SQL_BIND_BY_COLUMN pour spécifier si elle est à l’aide de la liaison selon les colonnes ou lignes. S’il faut utiliser la liaison selon les colonnes ou d’après les lignes est en grande partie une question de préférence de l’application. Liaison selon les lignes peut-être correspondre plus étroitement à la disposition de l’application des données, auquel cas il serait offrent de meilleures performances.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Liaison selon les colonnes](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [Liaison selon les lignes](../../../odbc/reference/develop-app/row-wise-binding.md)
