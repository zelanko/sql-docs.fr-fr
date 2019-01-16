---
title: Instructions UPDATE, DELETE et insertion | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00732de7eca32dc8b2984fdda14163c77c66ad43
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54256224"
---
# <a name="update-delete-and-insert-statements"></a>Instructions UPDATE, DELETE et INSERT
Applications basées sur SQL apporter des modifications aux tables en exécutant la **mise à jour**, **supprimer**, et **insérer** instructions. Ces instructions font partie d’au niveau de conformité de grammaire SQL minimale et doivent être pris en charge par tous les pilotes et les sources de données.  
  
 La syntaxe de ces instructions est :  
  
 **Mise à jour** _nom de la table_  
  
 **SET** _column-identifier_ **=** {*expression* &#124; **NULL**}  
  
 [**,** _identificateur de colonne_ **=** {*expression* &#124; **NULL**}]...  
  
 [**WHERE** _search-condition_]  
  
 **DELETE FROM** _nom de la table_[**où** _condition de recherche_]  
  
 **INSERT INTO** _nom de la table_[**(** _identificateur de colonne_ [**,** _-identificateur de la colonne_]... **)**]  
  
 {*spécification de requête* &#124; **valeurs (** _-valeur à insérer_ [**,** _-valeur à insérer_]... **)**}  
  
 Notez que le *spécification de requête* élément est valide uniquement dans les grammaires Core et SQL étendue et que le *expression* et *condition de recherche* éléments deviennent plus complexes dans les grammaires Core et SQL étendue.  
  
 Comme les autres instructions SQL, **mise à jour**, **supprimer**, et **insérer** instructions sont souvent plus efficaces lorsqu’ils utilisent des paramètres. Par exemple, l’instruction suivante peut être préparée et exécutée de façon répétée pour insérer plusieurs lignes dans la table Orders :  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Cette efficacité peut être augmentée par le passage de tableaux de valeurs de paramètre. Pour plus d’informations sur les paramètres d’instruction et les tableaux de valeurs de paramètre, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md).
