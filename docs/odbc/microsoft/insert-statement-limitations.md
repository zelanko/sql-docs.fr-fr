---
title: Limitations de déclaration INSERT (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, INSERT statement limitations
- INSERT statement limitations [ODBC]
- truncation of data [ODBC]
ms.assetid: dea05698-527a-41ab-8729-bbed85556185
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f903f15ec13baa28a789891c1527dc742daa68ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300002"
---
# <a name="insert-statement-limitations"></a>INSERT, instruction - limitations
Les données insérées sont tronquées sur la droite sans avertissement si elles sont trop longues pour s’insérer dans la colonne.  
  
 Tenter d’insérer une valeur qui est hors de la portée du type de données d’une colonne provoque un NULL à être inséré dans la colonne.  
  
 Lorsqu’un dBASE, Microsoft Excel, Paradox ou Textdriver est utilisé, l’insertion d’une chaîne de longueur zéro dans une colonne insère en fait un NULL à la place.  
  
 Lorsque le pilote Microsoft Excel est utilisé, si une chaîne vide est insérée dans une colonne, la chaîne vide est convertie en NULL ; une instruction SELECT recherchée qui est exécutée avec une chaîne vide dans la clause WHERE ne réussira pas sur cette colonne.  
  
 Une table n’est pas updatable par le pilote Paradox dans deux conditions:  
  
-   Lorsqu’un index unique n’est pas défini sur la table. Ce n’est pas vrai pour une table vide, qui peut être mise à jour avec une seule ligne, même si un index unique n’est pas défini sur la table. Si une seule ligne est insérée dans une table vide qui n’a pas d’index unique, une application ne peut pas créer un index unique ou insérer des données supplémentaires après l’insertion de la ligne unique.  
  
-   Si le moteur de base de données Borland n’est pas implémenté, seules les instructions de lecture et d’appendice sont autorisées sur la table Paradox.  
  
 Lorsque le pilote textuel est utilisé, les valeurs NULL sont représentées par une chaîne à vide dans des fichiers à durée fixe, mais ne sont représentées par aucun espace dans les fichiers délimités. Par exemple, dans la rangée suivante contenant trois champs, le deuxième champ est une valeur NULL :  
  
```  
"Smith:,, 123  
```  
  
 Lorsque le pilote de texte est utilisé, toutes les valeurs de colonne peuvent être rembourrées avec des espaces de tête. La longueur de toute rangée doit être inférieure ou égale à 65 543 octets.
