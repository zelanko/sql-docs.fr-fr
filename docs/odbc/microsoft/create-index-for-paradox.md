---
title: CRÉER un INDEX pour Paradox | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- Paradox driver [ODBC], create index
ms.assetid: 6472bd69-b931-4bc2-a9bf-f1873ed4cdfe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e68484efdc5194f93f2acab31973377d9c66f1c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280909"
---
# <a name="create-index-for-paradox"></a>CREATE INDEX pour Paradox
La syntaxe de l’instruction CREATe INDEX pour le pilote ODBC Paradox est la suivante :  
  
 **Create** [**unique** **] index index** *-Name*  
  
 Nom **de** la *table*  
  
 **(** *identificateur de colonne* [**ASC**]  
  
 [**,** *identificateur de colonne* [**ASC**]...] **)**  
  
 Le pilote ODBC Paradox ne prend pas en charge le mot clé **desc** dans la syntaxe SQL ODBC pour l’instruction CREATE index. L’argument *table-Name* peut spécifier le chemin d’accès complet de la table.  
  
 Si le mot clé **unique** est spécifié, le pilote ODBC Paradox crée un index unique. Le premier index unique est créé en tant qu’index primaire. Il s’agit d’un fichier de clé primaire Paradox nommé *table-Name*. Pix. Les index principaux sont soumis aux restrictions suivantes :  
  
-   L’index primaire doit être créé avant l’ajout de lignes à la table.  
  
-   Un index principal doit être défini sur les « n » premières colonnes d’une table.  
  
-   Un seul index primaire est autorisé par table.  
  
-   Une table ne peut pas être mise à jour par le pilote Paradox si un index principal n’est pas défini sur la table. (Notez que cela n’est pas vrai pour une table vide, qui peut être mise à jour même si un index unique n’est pas défini sur la table.)  
  
-   L’argument d' *index-Name* pour un index primaire doit être le même que le nom de base de la table, comme requis par Paradox.  
  
 Si le mot clé **unique** est omis, le pilote ODBC Paradox crée un index non unique. Il se compose de deux fichiers d’index secondaire Paradox nommés *table-Name*. X*nn* et *table-Name*. O*nn*, où *nn* est le numéro de la colonne dans la table. Les index non uniques sont soumis aux restrictions suivantes :  
  
-   Pour qu’un index non unique puisse être créé pour une table, un index primaire doit exister pour cette table.  
  
-   Pour Paradox 3. *x*, l’argument de *nom d’index* pour tout index autre qu’un index primaire (unique ou non unique) doit être identique au nom de la colonne. Pour Paradox 4. *x* et 5. *x*, le nom d’un tel index peut être, mais ne doit pas nécessairement être le même que le nom de la colonne.  
  
-   Une seule colonne peut être spécifiée pour un index non unique.  
  
 Les colonnes ne peuvent pas être ajoutées une fois qu’un index a été défini sur une table. Si la première colonne de la liste d’arguments d’une instruction CREATE TABLE crée un index, une deuxième colonne ne peut pas être incluse dans la liste d’arguments.  
  
 Par exemple, pour utiliser les colonnes numéro de commande client et numéro de ligne comme index unique sur la table SO_LINES, utilisez l’instruction suivante :  
  
```  
CREATE UNIQUE INDEX SO_LINES  
 ON SO_LINES (SONum, LineNum)  
```  
  
 Pour utiliser la colonne de numéro de référence en tant qu’index non unique sur la table SO_LINES, utilisez l’instruction suivante :  
  
```  
CREATE INDEX PartNum  
 ON SO_LINES (PartNum)  
```  
  
 Notez que lorsque deux instructions CREATe INDEX sont exécutées, la première instruction crée toujours un index primaire portant le même nom que la table et la deuxième instruction crée toujours un index non unique portant le même nom que la colonne. Ces index sont nommés ainsi, même si des noms différents sont entrés dans les instructions CREATe INDEX et même si l’index est étiqueté UNIQUE dans la deuxième instruction CREATe INDEX.  
  
> [!NOTE]  
>  Lorsque vous utilisez le pilote Paradox sans implémenter le Moteur de base de données Borland, seules les instructions Read et Append sont autorisées.
