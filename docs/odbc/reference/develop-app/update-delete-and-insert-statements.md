---
title: Instructions UPDATE, DELETE et INSERT | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284259"
---
# <a name="update-delete-and-insert-statements"></a>Instructions UPDATE, DELETE et INSERT
Les applications basées sur SQL apportent des modifications aux tables en exécutant les instructions **Update**, **Delete**et **Insert** . Ces instructions font partie du niveau minimal de conformité de la grammaire SQL et doivent être prises en charge par tous les pilotes et sources de données.  
  
 La syntaxe de ces instructions est la suivante :  
  
 **Mettre à jour** _le nom de la table_  
  
 **Set** _Column-identifier_ **=** {*expression* &#124; **null**}  
  
 [**,** _identificateur de colonne_ **=** {*expression* &#124; **null**}]...  
  
 [**Where** _recherche-condition_]  
  
 **Supprimer de** _table-Name_[**Where** _Search-condition_]  
  
 **INSERT dans** _table-Name_[**(** _Column-identifier_ [**,** _Column-identifier_]... **)**]  
  
 {value *-Specification* &#124; **valeurs (** _Insert-value_ [**,** _Insert-value_]... **)**}  
  
 Notez que l’élément de *spécification de requête* est valide uniquement dans les grammaires SQL principales et étendues, et que les éléments d' *expression* et de *condition de recherche* deviennent plus complexes dans les grammaires SQL principales et étendues.  
  
 Comme d’autres instructions SQL, les instructions **Update**, **Delete**et **Insert** sont souvent plus efficaces lorsqu’elles utilisent des paramètres. Par exemple, l’instruction suivante peut être préparée et exécutée à plusieurs reprises pour insérer plusieurs lignes dans la table Orders :  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Cette efficacité peut être augmentée en transmettant des tableaux de valeurs de paramètre. Pour plus d’informations sur les paramètres d’instruction et les tableaux de valeurs de paramètre, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md).
