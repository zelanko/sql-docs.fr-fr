---
title: Longueur de type de données d’intervalle (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68bb4daa47cb58d5a0ff7b680a2d2154fb14b345
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284318"
---
# <a name="interval-data-type-length"></a>Longueur des types de données d’intervalle
Les règles suivantes sont utilisées pour déterminer la durée d’un type de données d’intervalle en caractères. La longueur s’exprime en nombre de caractères. Le nombre d’octets dépend de l’ensemble de caractères. La longueur comprend les valeurs suivantes ajoutées ensemble :  
  
-   Deux personnages pour chaque champ dans l’intervalle qui n’est pas le champ de tête.  
  
-   Pour le champ de tête, le nombre de personnages qui est la précision de premier plan expresse ou implicite. Si la précision de tête n’est pas spécifiée, la valeur par défaut est de 2.  
  
-   Un personnage pour le séparateur entre les champs.  
  
-   Un plus la précision express ou implicite secondes. Si la précision des secondes n’est pas spécifiée, la valeur par défaut est de 6.  
  
 Des valeurs spécifiques de longueur de colonne pour chaque type de données d’intervalle sont contenues dans [la taille de colonne](../../../odbc/reference/appendixes/column-size.md).
