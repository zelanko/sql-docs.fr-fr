---
title: Afficher des données spatiales dans l’Explorateur d’objets | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de527a4961ac3ba297929bc8fb9b808681c6c3ff
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37206779"
---
# <a name="view-spatial-data-in-object-explorer"></a>Afficher des données spatiales dans l'Explorateur d'objets
  La fenêtre **Résultats spatiaux** de l'Éditeur de requête propose des outils de mappage visuel permettant d'afficher des résultats de données spatiales en plus des données affichées au format grille dans la fenêtre **Résultats** . Pour afficher des données spatiales dans la fenêtre **Résultats spatiaux** , vos résultats de requête doivent contenir au moins une colonne de données spatiales avec des données géométriques ou géographiques.  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a>Pour afficher des données spatiales dans la fenêtre Résultats spatiaux  
  
1.  Dans l'Éditeur de requête, cliquez sur l'onglet **Résultats spatiaux** .  
  
    > [!NOTE]  
    >  Cette fenêtre n'est pas disponible si vos résultats de requête ne contiennent pas de données spatiales ou si vous spécifiez que les résultats doivent être retournés sous forme de texte.  
  
2.  Sélectionnez la colonne à afficher dans la liste **Sélectionner la colonne spatiale** . Si votre table ne contient qu'une seule colonne spatiale, celle-ci constitue l'option par défaut dans la liste.  
  
3.  Sélectionnez la colonne non spatiale à utiliser comme étiquettes de données dans la liste **Sélectionner la colonne d’étiquette** .  
  
4.  Sélectionnez la projection voulue pour les données géographiques dans la liste **Sélectionner la projection** . La projection par défaut est équirectangulaire ; les autres projections possibles sont les projections de Mercator, de Robinson ou de Bonne.  
  
    > [!NOTE]  
    >  **Sélectionner la projection** n’est pas disponible si votre colonne spatiale contient des données géométriques.  
  
5.  Ajustez le curseur **Zoom** pour augmenter la taille visuelle des éléments mappés. Pour les formes polygonales, l'étiquette est visible uniquement lorsque la forme est suffisamment grande pour contenir le texte d'étiquette.  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtre Résultats spatiaux](spatial-results-window.md)   
 [Éditeur de requête du moteur de base de données &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md)   
 [Éditeurs de texte et de requête &#40;SQL Server Management Studio&#41;](query-and-text-editors-sql-server-management-studio.md)  
  
  
