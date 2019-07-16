---
title: INSERT, instruction-Limitations | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1676af6216ac703e9a8976951ec2888b9e940b67
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085524"
---
# <a name="insert-statement-limitations"></a>INSERT, instruction - limitations
Les données insérées sont tronquées à droite sans avertissement si elle est trop long pour tenir dans la colonne.  
  
 Tentative d’insertion d’une valeur qui est en dehors de la plage du type de données d’une colonne entraîne une valeur NULL à insérer dans la colonne.  
  
 Quand un fichier dBASE, Microsoft Excel, Paradox ou Textdriver est utilisé, l’insertion d’une chaîne de longueur nulle dans une colonne insère en fait une valeur NULL à la place.  
  
 Lorsque le pilote Microsoft Excel est utilisé, si une chaîne vide est insérée dans une colonne, la chaîne vide est convertie en une valeur NULL ; une instruction SELECT recherchée qui est exécutée avec une chaîne vide dans la clause WHERE ne réussira pas sur cette colonne.  
  
 Une table n’est pas mis à jour par le pilote Paradox sous deux conditions :  
  
-   Lorsqu’un index unique n’est pas défini sur la table. Cela n’est pas vrai pour une table vide, ce qui peut être mis à jour avec une seule ligne même si un index unique n’est pas défini sur la table. Si une seule ligne est insérée dans une table vide qui ne dispose pas d’un index unique, une application ne peut pas créer un index unique ou insérer des données supplémentaires une fois que la ligne a été insérée.  
  
-   Si le moteur de base de données Borland n’est pas implémenté, uniquement lire et ajoutez les instructions sont autorisées sur la table Paradox.  
  
 Lorsque le pilote de texte est utilisé, les valeurs NULL sont représentées par une chaîne blancs dans les fichiers de longueur fixe, mais sont représentées par aucun espace dans les fichiers délimités. Par exemple, dans la ligne suivante qui contient trois champs, le deuxième champ est une valeur NULL :  
  
```  
"Smith:,, 123  
```  
  
 Lorsque le pilote de texte est utilisé, toutes les valeurs de colonne peuvent être remplis avec des espaces. La longueur de n’importe quelle ligne doit être inférieur ou égal à 65,543 octets.
