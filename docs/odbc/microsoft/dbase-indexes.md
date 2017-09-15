---
title: Index dBASE | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DBase indexes [ODBC]
- DBase driver [ODBC], indexes
ms.assetid: fdfa56f5-e324-4ec2-9267-fdf95ab99373
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9f2725f312691d3cb644f9a096b5f469f1356c55
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="dbase-indexes"></a>Index dBASE
Le pilote dBASE s’ouvre automatiquement et met à jour les fichiers d’index dBASE IV. Vous devez utiliser le **sélectionner les index** boîte de dialogue affichée par l’administrateur de Source de données ODBC pour associer les fichiers dBASE III .ndx dBASE (fichiers).  
  
 Les limitations suivantes s’appliquent à la création d’index dBASE :  
  
-   Tous les noms de colonne doivent être valides.  
  
-   Toutes les colonnes doivent être dans le même croissant ou décroissant.  
  
-   La longueur d’une colonne de texte doit être inférieure à 100 octets.  
  
-   En cas de plusieurs colonnes, toutes les colonnes doivent être des colonnes de texte et la somme des tailles de colonne doit être inférieure à 100 octets.  
  
-   Les champs Mémo ne peuvent pas être indexées.  
  
-   Un index ne doit pas être spécifié pour l’ensemble de champs (autrement dit, les index en double non autorisés).  
  
-   Le nom d’index doit correspondre à la convention d’affectation de noms d’index dBASE. dBASE III nécessite que chaque index soit dans un fichier distinct, ayant chacun une extension .ndx. Dans dBASE IV, les index sont créés en tant que noms de balise sont stockés dans un fichier .mdx unique. Le fichier .mdx a le même nom que le fichier de base de données (par exemple, emp.MDX est le fichier d’index pour la base de données Emp.dbf).  
  
-   dBASE définit un index unique comme un où un seul enregistrement d’un ensemble de valeurs clés identiques est ajouté à l’index.
