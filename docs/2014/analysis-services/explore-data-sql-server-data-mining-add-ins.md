---
title: Explorer des données (SQL Server des compléments d’exploration de données) | Microsoft Docs
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
ms.openlocfilehash: 4a20484a85b459dad58e5e6687a6cc34a093b130
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528355"
---
# <a name="explore-data-sql-server-data-mining-add-ins"></a>Explorer des données (Compléments d'exploration de données SQL Server)
  ![Assistant Explorer les données](media/dmc-explore.gif "Assistant Explorer les données")  
  
 L’Assistant **exploration des données** vous aide à comprendre le type et la quantité de données de votre table de données. Cet Assistant représente sous forme graphique la distribution et les valeurs des colonnes sélectionnées, une colonne à la fois. Vous pouvez ensuite essayer de changer la manière de regrouper les données ou copier le graphique qui représente le contenu dans un classeur Excel pour consultation ultérieure.  
  
 Si vos données contiennent des données numériques continues, vous pouvez alterner entre ces deux vues :  
  
-   **Graphique en courbes.** Ce graphique affiche les valeurs de données sur l'axe X et le nombre de cas sur l'axe Y.  
  
-   **Graphique à barres.** Ce graphique regroupe les valeurs selon le nombre de cas pour chaque valeur.  
  
 Lorsque l'Assistant recherche des groupes dans les données, il utilise la distribution réelle des valeurs de données. Par conséquent, le graphique à barres ne montre pas les marqueurs standard de l'axe numérique entier tels que 10 ou 100. À la place, les plages affichées dans le graphique à barres peuvent ressembler à 43521-55603 (pour la colonne de revenus).  
  
 Si vous souhaitez regrouper vos données dans d'autres plages, vous devez le faire dans Excel avant d'analyser les données. Ou vous pouvez réétiqueter les données à l’aide de l’Assistant [réétiqueter](relabel-sql-server-data-mining-add-ins.md) .  
  
## <a name="using-the-explore-data-wizard"></a>Utilisation de l'Assistant Explorer les données  
  
1.  Dans le ruban **exploration de données** , cliquez sur Explorer les **données**.  
  
2.  Dans la boîte de dialogue **Sélectionner une source** , sélectionnez la table ou la plage de cellules qui contient vos données.  
  
3.  Dans la boîte de dialogue **Sélectionner une colonne** , choisissez la colonne à analyser, parmi les exemples de données affichés dans le volet.  
  
4.  Dans la boîte de dialogue **Explorer les données** , choisissez les types de graphiques pour l’affichage de la distribution des données.  
  
5.  Le cas échéant, ajoutez de nouvelles colonnes aux données, modifiez la segmentation des données ou copiez le graphique dans Excel.  
  
### <a name="requirements"></a>Spécifications  
 Pour utiliser l’Assistant **Explorer les données** , vos données doivent se trouver dans une table de données Excel.   
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : préparation pour l'exploration de données](checklist-of-preparation-for-data-mining.md)  
  
  
