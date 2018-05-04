---
title: Les instructions INSERT, DELETE et UPDATE | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- DELETE [ODBC]
- UPDATE [ODBC]
- INSERT [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 5004ea72-4c49-4064-9752-f7032ba7f133
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59e98d80962a059f885bd82ed8be465415a55774
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="update-delete-and-insert-statements"></a>Les instructions INSERT, DELETE et UPDATE
Applications basées sur SQL apporter des modifications aux tables en exécutant la **mise à jour**, **supprimer**, et **insérer** instructions. Ces instructions font partie du niveau de conformité grammaire SQL minimale et doivent être pris en charge par tous les pilotes et les sources de données.  
  
 La syntaxe de ces instructions est :  
  
 **Mise à jour***-nom de la table*  
  
 **Définissez** *identificateur de la colonne* **=** {*expression* &#124; **NULL**}  
  
 [**,** *identificateur de la colonne* **=** {*expression* &#124; **NULL**}]...  
  
 [**Où** *condition de recherche*]  
  
 **DELETE FROM** *-nom de la table*[**où** *condition de recherche*]  
  
 **INSERT INTO** *-nom de la table*[**(*** identificateur de la colonne* [**,** *identificateur de la colonne*]... **)**]  
  
 {*-spécification de la requête* &#124;  **valeurs (*** valeur à insérer* [**,** *-valeur à insérer*]... **)**}  
  
 Notez que la *-spécification de la requête* élément est valide uniquement dans les grammaires Core et SQL étendue et que le *expression* et *condition de recherche* éléments deviennent plus complexes dans les grammaires Core et SQL étendue.  
  
 Comme les autres instructions SQL, **mise à jour**, **supprimer**, et **insérer** instructions sont souvent plus efficaces lorsqu’ils utilisent des paramètres. Par exemple, l’instruction suivante peut être préparée et exécutée de façon répétée pour insérer plusieurs lignes dans la table Orders :  
  
```  
INSERT INTO Orders (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Cette efficacité peut être augmentée en passant des tableaux de valeurs de paramètre. Pour plus d’informations sur les paramètres de l’instruction et les tableaux de valeurs de paramètre, consultez [paramètres de l’instruction](../../../odbc/reference/develop-app/statement-parameters.md).
