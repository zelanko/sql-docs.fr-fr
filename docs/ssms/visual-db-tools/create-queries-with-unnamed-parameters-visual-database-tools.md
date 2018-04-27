---
title: Créer des requêtes avec des paramètres sans nom (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unnamed parameters
- parameters [SQL Server], unnamed
ms.assetid: 5f4b664b-3d3d-4d07-a0e7-791d78743504
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5257b8156ee0c993f448c8dc020bb90be0f34c49
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="create-queries-with-unnamed-parameters-visual-database-tools"></a>Créer des requêtes avec des paramètres sans nom (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Vous pouvez créer une requête avec un paramètre sans nom en spécifiant un point d'interrogation (?) comme espace réservé pour une valeur littérale. Le Concepteur de requêtes et de vues lui donnera un nom temporaire. Vous pouvez définir autant de paramètres sans nom que vous le souhaitez dans la requête.  
  
Lorsque vous exécutez la requête dans le Concepteur de requêtes et de vues, la boîte de dialogue Paramètres de la requête s'affiche avec le nom temporaire.  
  
### <a name="to-specify-an-unnamed-parameter"></a>Pour spécifier un paramètre sans nom  
  
1.  Ajoutez les colonnes ou expressions à rechercher dans le [volet Critères](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md). Si vous ne souhaitez pas que les colonnes ou expressions de recherche apparaissent dans le résultat de la requête, supprimez-les comme colonnes de sortie.  
  
2.  Recherchez la ligne contenant la colonne de données ou l’expression à rechercher puis, dans la colonne **Filtre** de la grille, entrez un point d’interrogation (?).  
  
    Par défaut, le Concepteur de requêtes et de vues ajoute l'opérateur « = ». Toutefois, vous pouvez modifier la cellule pour le remplacer par « > », « < », ou un autre opérateur de comparaison SQL.  
  
## <a name="see-also"></a> Voir aussi  
[Requête avec des paramètres &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  
