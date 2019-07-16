---
title: POUR Paradox | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 331613676b748453a56da1e41fe85f04a7715038
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081937"
---
# <a name="create-index-for-paradox"></a>CREATE INDEX pour Paradox
La syntaxe de l’instruction CREATE INDEX pour le pilote ODBC Paradox est :  
  
 **CREATE** [**UNIQUE**] **INDEX** *index-name*  
  
 **ON** *nom de la table*  
  
 **(** *identificateur de colonne* [**ASC**]  
  
 [ **,** *identificateur de colonne* [**ASC**]...] **)**  
  
 Le pilote ODBC Paradox ne prend pas en charge la **DESC** mot clé dans la grammaire SQL ODBC pour l’instruction CREATE INDEX. Le *nom de la table* argument peut spécifier le chemin d’accès complet de la table.  
  
 Si le mot clé **UNIQUE** est spécifié, le pilote ODBC Paradox créera un index unique. Le premier index unique est créé comme un index primaire. Il s’agit d’un fichier de clé primaire Paradox est nommé *nom de la table*. PX. Index primaires sont soumis aux restrictions suivantes :  
  
-   L’index primaire doit être créé avant que toutes les lignes sont ajoutées à la table.  
  
-   Un index primaire doit être défini sur les premières colonnes de « n » dans une table.  
  
-   Un seul index primaire est autorisé par table.  
  
-   Une table ne peut pas être mis à jour par le pilote Paradox si un index primaire n’est pas défini sur la table. (Notez que cela n’est pas vrai pour une table vide, ce qui peut être mise à jour même si un index unique n’est pas défini sur la table).  
  
-   Le *nom de l’index* argument pour un index principal doit être le même que le nom de base de la table, comme requis par Paradox.  
  
 Si le mot clé **UNIQUE** est omis, le pilote ODBC Paradox créera un index non unique. Cela se compose de deux fichiers d’index secondaire Paradox nommés *nom de la table*. X*nn* et *nom de la table*. Y*nn*, où *nn* est le numéro de la colonne dans la table. Index non uniques sont soumis aux restrictions suivantes :  
  
-   Avant de pouvoir créer un index non unique pour une table, un index principal doit exister pour cette table.  
  
-   Pour Paradox 3. *x*, le *nom de l’index* argument pour n’importe quel index autre que d’un index primaire (unique ou non) doit être le même que le nom de colonne. Pour Paradox 4. *x* et 5. *x*, le nom de cet index peut être, mais ne doit pas être le même que le nom de colonne.  
  
-   Une seule colonne peut être spécifiée pour un index non unique.  
  
 Colonnes ne peuvent pas être ajoutées une fois qu’un index a été défini sur une table. Si la première colonne de la liste d’arguments d’une instruction CREATE TABLE crée un index, une deuxième colonne ne peut pas être incluse dans la liste d’arguments.  
  
 Par exemple, pour utiliser le numéro de commande et de colonnes de numéro de ligne en tant que l’index unique sur la table SO_LINES, utilisez l’instruction :  
  
```  
CREATE UNIQUE INDEX SO_LINES  
 ON SO_LINES (SONum, LineNum)  
```  
  
 Pour utiliser la colonne de numéro de partie comme un index non unique sur la table SO_LINES, utilisez l’instruction :  
  
```  
CREATE INDEX PartNum  
 ON SO_LINES (PartNum)  
```  
  
 Notez que lorsque les deux instructions CREATE INDEX sont effectuées, la première instruction crée toujours un index primaire portant le même nom que la table et la deuxième instruction crée toujours un index non unique avec le même nom que la colonne. Ces index seront nommés ainsi, même si des noms différents sont entrés dans les instructions CREATE INDEX, et même si l’index est UNIQUE dans la deuxième instruction CREATE INDEX.  
  
> [!NOTE]  
>  Lorsque vous utilisez le pilote Paradox sans avoir à implémenter le moteur de base de données Borland, en lecture seule et ajoutez les instructions sont autorisées.
