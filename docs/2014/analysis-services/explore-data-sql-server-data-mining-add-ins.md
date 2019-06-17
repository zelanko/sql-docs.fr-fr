---
title: Explorer les données (SQL Server Data Mining Add-ins) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- histogram [data mining]
- data visualization
ms.assetid: 714845a9-4c27-461a-9ba3-149e1e818386
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0bad2a2e65a65bbafa8218a3e0afbedd4b9f13b6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66081309"
---
# <a name="explore-data-sql-server-data-mining-add-ins"></a>Explorer des données (Compléments d'exploration de données SQL Server)
  ![Assistant de données Explorer](media/dmc-explore.gif "Assistant Exploration des données")  
  
 Le **Explorer les données** Assistant vous aide à comprendre le type et la quantité de données dans votre table de données. Cet Assistant représente sous forme graphique la distribution et les valeurs des colonnes sélectionnées, une colonne à la fois. Vous pouvez ensuite essayer de changer la manière de regrouper les données ou copier le graphique qui représente le contenu dans un classeur Excel pour consultation ultérieure.  
  
 Si vos données contiennent des données numériques continues, vous pouvez alterner entre ces deux vues :  
  
-   **Graphique linéaire.** Ce graphique affiche les valeurs de données sur l'axe X et le nombre de cas sur l'axe Y.  
  
-   **Graphique à barres.** Ce graphique regroupe les valeurs selon le nombre de cas pour chaque valeur.  
  
 Lorsque l'Assistant recherche des groupes dans les données, il utilise la distribution réelle des valeurs de données. Par conséquent, le graphique à barres ne montre pas les marqueurs standard de l'axe numérique entier tels que 10 ou 100. À la place, les plages affichées dans le graphique à barres peuvent ressembler à 43521-55603 (pour la colonne de revenus).  
  
 Si vous souhaitez regrouper vos données dans d'autres plages, vous devez le faire dans Excel avant d'analyser les données. Ou, vous pouvez également réétiqueter les données à l’aide de la [réétiquetage](relabel-sql-server-data-mining-add-ins.md) Assistant.  
  
## <a name="using-the-explore-data-wizard"></a>Utilisation de l'Assistant Explorer les données  
  
1.  Dans le **d’exploration de données** ruban, cliquez sur **Explorer les données**.  
  
2.  Dans le **sélectionner une Source** boîte de dialogue, sélectionnez la table ou la plage de cellules qui contient vos données.  
  
3.  Dans le **sélectionner la colonne** boîte de dialogue, sélectionnez la colonne à analyser, à partir d’exemples de données affichés dans le volet.  
  
4.  Dans le **Explorer les données** boîte de dialogue, sélectionnez les types de graphiques pour afficher la distribution des données.  
  
5.  Le cas échéant, ajoutez de nouvelles colonnes aux données, modifiez la segmentation des données ou copiez le graphique dans Excel.  
  
### <a name="requirements"></a>Configuration requise  
 Pour utiliser le **Explorer les données** Assistant, vos données doivent être dans une table de données Excel.   
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : préparation pour l’exploration de données](checklist-of-preparation-for-data-mining.md)  
  
  
