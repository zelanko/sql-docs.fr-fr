---
title: dBASE Indexes (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase indexes [ODBC]
- DBase driver [ODBC], indexes
ms.assetid: fdfa56f5-e324-4ec2-9267-fdf95ab99373
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9300a38a0e36da771a238f73b77d3dda527334ae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307670"
---
# <a name="dbase-indexes"></a>Index dBASE
Le pilote ODBC dBASE ouvre automatiquement et met à jour les fichiers d’index DBASE IV. Vous devez utiliser la boîte de dialogue **Select Indexes** affichée par l’administrateur de source de données ODBC pour associer les fichiers dBASE III .ndx avec des fichiers dBASE.  
  
 Les limites suivantes s’appliquent à la création d’indices dBASE :  
  
-   Tous les noms de colonne doivent être valides.  
  
-   Toutes les colonnes doivent être dans le même ordre ascendant ou descendant.  
  
-   La longueur d’une colonne de texte doit être inférieure à 100 octets.  
  
-   Si plus d’une colonne existe, toutes les colonnes doivent être des colonnes de texte et la somme des tailles de colonne doit être inférieure à 100 octets.  
  
-   Les champs de notes ne peuvent pas être indexés.  
  
-   Un indice ne doit pas être spécifié pour l’ensemble actuel de champs (c’est-à-dire que les indices en double ne sont pas autorisés).  
  
-   Le nom de l’index doit correspondre à la convention de nommage de l’indice dBASE. dBASE III exige que chaque index soit dans un fichier séparé, chacun ayant une extension .ndx. Dans dBASE IV, les index sont créés sous forme de noms d’étiquettes stockés dans un seul fichier .mdx. Le fichier .mdx a le même nom de base que le fichier de base (par exemple, Emp.mdx est le fichier d’index de la base de données Emp.dbf).  
  
-   dBASE définit un indice unique comme un indice où un seul enregistrement d’un ensemble avec des valeurs clés identiques est ajouté à l’indice.
