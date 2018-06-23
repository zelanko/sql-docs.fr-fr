---
title: Créer des requêtes avec des paramètres sans nom (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unnamed parameters
- parameters [SQL Server], unnamed
ms.assetid: 5f4b664b-3d3d-4d07-a0e7-791d78743504
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a2245bf5298d6b760b0b52a8dc83f233d337283f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052135"
---
# <a name="create-queries-with-unnamed-parameters-visual-database-tools"></a>Créer des requêtes avec des paramètres sans nom (Visual Database Tools)
  Vous pouvez créer une requête avec un paramètre sans nom en spécifiant un point d'interrogation (?) comme espace réservé pour une valeur littérale. Le Concepteur de requêtes et de vues lui donnera un nom temporaire. Vous pouvez définir autant de paramètres sans nom que vous le souhaitez dans la requête.  
  
 Lorsque vous exécutez la requête dans le Concepteur de requêtes et de vues, la boîte de dialogue Paramètres de la requête s'affiche avec le nom temporaire.  
  
### <a name="to-specify-an-unnamed-parameter"></a>Pour spécifier un paramètre sans nom  
  
1.  Ajoutez les colonnes ou expressions à rechercher dans le [volet Critères](visual-database-tools.md). Si vous ne souhaitez pas que les colonnes ou expressions de recherche apparaissent dans le résultat de la requête, supprimez-les comme colonnes de sortie.  
  
2.  Recherchez la ligne contenant la colonne de données ou l’expression à rechercher puis, dans la colonne **Filtre** de la grille, entrez un point d’interrogation (?).  
  
     Par défaut, le Concepteur de requêtes et de vues ajoute l'opérateur « = ». Toutefois, vous pouvez modifier la cellule pour le remplacer par « > », « < », ou un autre opérateur de comparaison SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Requête avec des paramètres &#40;Visual Database Tools&#41;](query-with-parameters-visual-database-tools.md)  
  
  