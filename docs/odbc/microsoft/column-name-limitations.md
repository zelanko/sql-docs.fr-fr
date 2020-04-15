---
title: Limitations de nom de colonne (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], column names
- ODBC desktop database drivers [ODBC], column names
ms.assetid: 5a339f61-c52f-40ad-8deb-d785f72753d4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 41d973afdac360af114da41620997cad23a2c740
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281379"
---
# <a name="column-name-limitations"></a>Limitations des noms de colonne
Les noms de colonne peuvent contenir tous les caractères valides (par exemple, les espaces). Si les noms de colonne contiennent des caractères, sauf des lettres, des chiffres et des souligne, le nom doit être délimité en l’enfermant dans des citations de dos (').  
  
 Lorsque le pilote Microsoft Access ou Microsoft Excel est utilisé, les noms de colonnes sont limités à 64 caractères, et les noms plus longs génèrent une erreur. Lorsque le pilote Paradox est utilisé, le nom de colonne maximum est de 25 caractères. Lorsque le pilote de texte est utilisé, le nom de colonne maximum est de 64 caractères, et les noms plus longs sont tronqués.  
  
 Lorsque le pilote dBASE est utilisé, les caractères d’une valeur ASCII supérieure à 127 sont convertis en souligne.  
  
 Lorsque le pilote Microsoft Excel est utilisé, si les noms de colonnes sont présents, ils doivent être dans la première rangée. Un nom qui dans Microsoft Excel utiliserait le caractère "!" doit être enfermé dans des citations de dos ('). Le personnage "!" est converti au personnage "$", parce que le personnage "!" n’est pas légal dans un nom ODBC, même lorsque le nom est inclus dans des citations de dos. Tous les autres personnages Microsoft Excel valides (à l’exception du caractère de pipe (&#124;)) peuvent être utilisés dans un nom de colonne, y compris les espaces. Un identifiant délimité doit être utilisé pour un nom de colonne Microsoft Excel pour inclure un espace. Les noms de colonnes non spécifiés seront remplacés par des noms générés par le conducteur, par exemple, "Col1" pour la première colonne.  
  
 Le caractère de tuyau (&#124;) ne peut pas être utilisé dans un nom de colonne, que le nom soit inclus dans des citations de dos ou non.  
  
 Lorsque le pilote textuel est utilisé, le pilote fournit un nom par défaut si un nom de colonne n’est pas spécifié. Par exemple, le conducteur appelle la première colonne F1, la deuxième colonne F2, et ainsi de suite.
