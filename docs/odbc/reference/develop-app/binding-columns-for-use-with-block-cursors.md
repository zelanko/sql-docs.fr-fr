---
title: Colonnes de liaison pour l’utilisation avec les curseurs de bloc ( Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc7e527658a7d6945921510de898c648075c41fc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284899"
---
# <a name="binding-columns-for-use-with-block-cursors"></a>Liaison de colonnes pour une utilisation avec des curseurs de bloc
Étant donné que les curseurs de blocs retournent plusieurs lignes, les applications qui les utilisent doivent lier un éventail de variables à chaque colonne au lieu d’une seule variable. Ces tableaux sont collectivement connus sous le nom de *tampons rowset*. Voici les deux styles de liaison :  
  
-   Lier un tableau à chaque colonne. C’est ce qu’on appelle *la liaison de colonne-sage* parce que chaque structure de données (tableau) contient des données pour une seule colonne.  
  
-   Définissez une structure pour conserver les données pour une rangée entière et lier un tableau de ces structures. C’est ce qu’on appelle *la liaison en ligne* parce que chaque structure de données contient les données pour une seule ligne.  
  
 Comme lorsque l’application lie des variables uniques à des colonnes, elle appelle **SQLBindCol** pour lier les tableaux aux colonnes. La seule différence est que les adresses transmises sont des adresses de tableau, pas des adresses variables simples. L’application définit l’attribut SQL_BIND_BY_COLUMN énoncé pour spécifier s’il utilise la liaison de colonne-sage ou de ligne-sage. L’utilisation de la liaison de colonne ou de ligne est en grande partie une question de préférence d’application. La liaison de la ligne peut correspondre plus étroitement à la disposition des données de l’application, auquel cas elle offrirait de meilleures performances.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison selon les colonnes](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [Liaison selon les lignes](../../../odbc/reference/develop-app/row-wise-binding.md)
