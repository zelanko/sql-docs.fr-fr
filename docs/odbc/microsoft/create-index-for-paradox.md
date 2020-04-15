---
title: CREATE INDEX pour Paradox Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280909"
---
# <a name="create-index-for-paradox"></a>CREATE INDEX pour Paradox
La syntaxe de la déclaration CREATE INDEX pour le pilote ODBC Paradox est :  
  
 **CREATE** [**UNIQUE**] *INDEX-nom* **INDEX**  
  
 **ON** *nom de table*  
  
 **(** *colonne-identifiant* [**ASC**]  
  
 [**,** *colonne-identifiant* [**ASC**]...] **)**  
  
 Le pilote ODBC Paradox ne prend pas en charge le mot clé **DESC** dans la grammaire SQL ODBC pour la déclaration CREATE INDEX. *L’argument du nom de table* peut spécifier le chemin complet de la table.  
  
 Si le mot clé **UNIQUE** est spécifié, le pilote ODBC Paradox créera un index unique. Le premier indice unique est créé comme un indice primaire. Il s’agit d’un fichier clé primaire Paradox nommé *nom de table*. Px. Les indices primaires sont soumis aux restrictions suivantes :  
  
-   L’index primaire doit être créé avant que les lignes ne soient ajoutées à la table.  
  
-   Un indice primaire doit être défini sur les premières colonnes «n» dans un tableau.  
  
-   Un seul indice primaire est autorisé par tableau.  
  
-   Un tableau ne peut pas être mis à jour par le pilote Paradox si un indice primaire n’est pas défini sur la table. (Notez que ce n’est pas vrai pour une table vide, qui peut être mise à jour même si un indice unique n’est pas défini sur la table.)  
  
-   *L’argument de l’index* d’un indice primaire doit être le même que le nom de base du tableau, comme l’exige Paradox.  
  
 Si le mot clé **UNIQUE** est omis, le pilote ODBC Paradox créera un index non unique. Il s’agit de deux fichiers d’index secondaire Paradox nommés *nom de table*. X*nn* et *nom de table*. Y*nn*, où *nn* est le nombre de la colonne dans le tableau. Les indices non uniques sont assujettis aux restrictions suivantes :  
  
-   Avant qu’un indice non unique puisse être créé pour une table, un indice primaire doit exister pour ce tableau.  
  
-   Pour Paradox 3. *x*, l’argument du *nom de l’index* pour tout indice autre qu’un indice primaire (unique ou non unique) doit être le même que le nom de la colonne. Pour Paradox 4. *x* et 5. *x*, le nom d’un tel index peut être, mais n’a pas à être, le même que le nom de colonne.  
  
-   Une seule colonne peut être spécifiée pour un index non unique.  
  
 Les colonnes ne peuvent pas être ajoutées une fois qu’un index a été défini sur une table. Si la première colonne de la liste d’arguments d’une instruction CREATE TABLE crée un index, une deuxième colonne ne peut pas être incluse dans la liste d’arguments.  
  
 Par exemple, pour utiliser le numéro de commande de vente et les colonnes de numéro de ligne comme indice unique sur le tableau SO_LINES, utilisez l’énoncé :  
  
```  
CREATE UNIQUE INDEX SO_LINES  
 ON SO_LINES (SONum, LineNum)  
```  
  
 Pour utiliser la colonne de numéro de pièce comme un index non unique sur la table SO_LINES, utilisez l’énoncé :  
  
```  
CREATE INDEX PartNum  
 ON SO_LINES (PartNum)  
```  
  
 Notez que lorsque deux relevés CREATE INDEX sont exécutés, la première déclaration créera toujours un index primaire du même nom que le tableau et la deuxième déclaration créera toujours un index non unique du même nom que la colonne. Ces index seront nommés de cette façon même si différents noms sont entrés dans les relevés CREATE INDEX et même si l’indice est étiqueté UNIQUE dans la deuxième déclaration CREATE INDEX.  
  
> [!NOTE]  
>  Lorsque vous utilisez le pilote Paradox sans implémenter le moteur de base de données Borland, seules les instructions de lecture et d’appendice sont autorisées.
