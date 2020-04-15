---
title: MISES À JOUR, DELETE et INSERT Statements (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- DELETE [ODBC]
- UPDATE [ODBC]
- INSERT [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f12682a5d012d6981afce0085e9c920ed2f2ffbc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284259"
---
# <a name="update-delete-and-insert-statements"></a>Instructions UPDATE, DELETE et INSERT
Les applications basées sur SQL modifient les tableaux en exécutant les instructions **UPDATE**, **DELETE**et **INSERT.** Ces énoncés font partie du niveau de conformité de grammaire minimum SQL et doivent être pris en charge par tous les conducteurs et sources de données.  
  
 La syntaxe de ces énoncés est la suivante :  
  
 **NOM** _de table_ UPDATE  
  
 **SET** _colonne-identificateur_ **=** -*expression* &#124; **NULL**'  
  
 [,**,** _colonne-identifiant_ **=** -*expression* &#124; **NULL]...**  
  
 [**Où** _la recherche-condition_]  
  
 **DELETE FROM** _table-name_[**WHERE** _search-condition_]  
  
 **INSERT INTO** _nom de table_[**(** _colonne-identifiant_ [**,** _colonne-identifiant_]... **)**]  
  
 -*requête-spécification* &#124; VALUES **(** _insert-value_ [**,** _insert-value_]... **)**}  
  
 Notez que *l’élément de spécification de requête* n’est valable que dans les grammaires Core et Extended SQL, et que les éléments *d’expression* et *de condition de recherche* deviennent plus complexes dans les grammaires Core et Extended SQL.  
  
 Comme d’autres déclarations SQL, **UPDATE**, **DELETE**, et **INSERT** déclarations sont souvent plus efficaces quand ils utilisent des paramètres. Par exemple, la déclaration suivante peut être préparée et exécutée à plusieurs reprises pour insérer plusieurs lignes dans le tableau des ordres :  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Cette efficacité peut être augmentée en passant des gammes de valeurs de paramètres. Pour plus d’informations sur les paramètres de l’énoncé et les tableaux de valeurs de paramètres, voir [Paramètres d’énoncé .](../../../odbc/reference/develop-app/statement-parameters.md)
