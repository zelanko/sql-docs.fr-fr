---
title: Index dBASE | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66dab60f4a9a180d2a8b74ce4d0c8f4d7bf8d242
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682837"
---
# <a name="dbase-indexes"></a>Index dBASE
Le pilote dBASE s’ouvre automatiquement et met à jour les fichiers d’index dBASE IV. Vous devez utiliser le **index sélectionnez** boîte de dialogue affichée par l’administrateur de sources de données ODBC à associer les fichiers dBASE III .ndx dBASE (fichiers).  
  
 Les limitations suivantes s’appliquent à la création d’index dBASE :  
  
-   Tous les noms de colonne doivent être valides.  
  
-   Toutes les colonnes doivent être le même croissant ou décroissant.  
  
-   La longueur de n’importe quelle colonne de texte unique doit être inférieure à 100 octets.  
  
-   En cas de plusieurs colonnes, toutes les colonnes doivent être des colonnes de texte et la somme des tailles de colonne doit être inférieure à 100 octets.  
  
-   Les champs Mémo ne peuvent pas être indexées.  
  
-   Un index ne doit pas être spécifié pour le jeu actuel de champs (autrement dit, les index dupliqués non autorisés).  
  
-   Le nom d’index doit correspondre à la convention d’affectation de noms d’index dBASE. dBASE III nécessite que chaque index dans un fichier distinct, ayant chacun une extension .ndx. Dans dBASE IV, les index sont créés en tant que noms de balise qui sont stockés dans un fichier .mdx unique. Le fichier .mdx a le même nom que le fichier de base de données (par exemple, emp.MDX est le fichier d’index pour la base de données Emp.dbf).  
  
-   dBASE définit un index unique comme où un seul enregistrement à partir d’un jeu avec des valeurs de clés identiques est ajouté à l’index.
