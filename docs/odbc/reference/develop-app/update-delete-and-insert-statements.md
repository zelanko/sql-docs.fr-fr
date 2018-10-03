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
ms.openlocfilehash: 92fb7b0e9722c52c7f1e9fc071d434f531b2fc46
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721907"
---
# <a name="update-delete-and-insert-statements"></a>Instructions UPDATE, DELETE et INSERT
Applications basées sur SQL apporter des modifications aux tables en exécutant la **mise à jour**, **supprimer**, et **insérer** instructions. Ces instructions font partie d’au niveau de conformité de grammaire SQL minimale et doivent être pris en charge par tous les pilotes et les sources de données.  
  
 La syntaxe de ces instructions est :  
  
 **Mise à jour***nom de la table*   
  
 **Définissez** *identificateur de colonne* **=** {*expression* &#124; **NULL**}  
  
 [**,** *identificateur de colonne* **=** {*expression* &#124; **NULL**}]...  
  
 [**Où** *condition de recherche*]  
  
 **DELETE FROM** *nom de la table*[**où** *condition de recherche*]  
  
 **INSERT INTO** *nom de la table*[**(*** identificateur de colonne* [**,** *identificateur de colonne*]... **)**]  
  
 {*spécification de requête* &#124;  **valeurs (***-valeur à insérer* [**,** *-valeur à insérer*]... **)**}  
  
 Notez que le *spécification de requête* élément est valide uniquement dans les grammaires Core et SQL étendue et que le *expression* et *condition de recherche* éléments deviennent plus complexes dans les grammaires Core et SQL étendue.  
  
 Comme les autres instructions SQL, **mise à jour**, **supprimer**, et **insérer** instructions sont souvent plus efficaces lorsqu’ils utilisent des paramètres. Par exemple, l’instruction suivante peut être préparée et exécutée de façon répétée pour insérer plusieurs lignes dans la table Orders :  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Cette efficacité peut être augmentée par le passage de tableaux de valeurs de paramètre. Pour plus d’informations sur les paramètres d’instruction et les tableaux de valeurs de paramètre, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md).
