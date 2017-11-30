---
title: "Définir un message d’absence de données pour une région de données (Générateur de rapports et SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
caps.latest.revision: "7"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 7fdb370afe8d06b33d6e69bc0b2b1fc52c30c195
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="set-a-no-data-message-for-a-data-region-report-builder-and-ssrs"></a>Définir un message d'absence de données pour une région de données (Générateur de rapports et SSRS)
  Quand vous souhaitez qu’un texte s’affiche dans le rapport rendu à la place d’une région de données ne contenant pas de données, vous devez définir la propriété NoRowsMessage de la région de données de table, de matrice ou de liste souhaitée, la propriété NoDataMessage de la région de données de graphique et la propriété NoDataText de l’échelle de couleurs de la carte. Au moment de l'exécution, le processeur de rapports exécute la requête pour chaque dataset d'un rapport et la requête de dataset peut ne produire aucun jeu de résultats. Pour une région de données liée à un dataset vide, vous pouvez spécifier le texte à afficher à la place de la région de données vide. Vous pouvez également définir la propriété NoRowsMessage pour un sous-rapport quand aucun dataset de ce dernier ne contient de données au moment de l’exécution.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-norowsmessage-property-for-a-table-matrix-or-list"></a>Pour définir la propriété NoRowsMessage d'une table, matrice ou liste spécifique  
  
1.  En mode Conception, sur l'aire de conception, cliquez sur la table, la matrice, la région de données de type liste ou le sous-rapport souhaité pour sélectionner celle-ci / celui-ci. Le volet Propriétés affiche les propriétés de l'élément que vous venez de sélectionner.  
  
2.  Dans le volet Propriétés, tapez le texte à afficher comme message dans le champ de la propriété **NoRowsMessage** .  
  
     Vous pouvez également cliquer sur l’option **Expression** de la liste déroulante pour ouvrir la boîte de dialogue **Expression** et créer l’expression souhaitée.  
  
### <a name="to-set-the-nodatamessage-property-for-a-chart"></a>Pour définir la propriété NoDataMessage d'un graphique  
  
1.  En mode Conception, sur l'aire de conception, cliquez sur le graphique souhaité pour le sélectionner. Le volet Propriétés affiche les propriétés de l'élément que vous venez de sélectionner.  
  
2.  Dans le volet Propriétés, développez le nœud correspondant à **NoDataMessage**.  
  
3.  Dans la zone **Légende**, tapez le texte à afficher comme message dans le champ de propriété **NoDataMessage** .  
  
     Vous pouvez également cliquer sur l’option **Expression** de la liste déroulante pour ouvrir la boîte de dialogue **Expression** et créer l’expression souhaitée.  
  
### <a name="to-set-the-norowsmessage-for-a-subreport"></a>Pour définir la propriété NoRowsMessage d'un sous-rapport  
  
1.  En mode Conception, sur l'aire de conception, cliquez sur le sous-rapport souhaité pour le sélectionner. Le volet Propriétés affiche les propriétés de l'élément que vous venez de sélectionner.  
  
2.  Dans le volet Propriétés, tapez le texte à afficher comme message dans le champ de la propriété **NoRowsMessage** .  
  
     Vous pouvez également cliquer sur l’option **Expression** de la liste déroulante pour ouvrir la boîte de dialogue **Expression** et créer l’expression souhaitée.  
  
### <a name="to-set-the-nodatatext-property-for-a-color-scale-for-a-map"></a>Pour définir la propriété NoDataText de l'échelle de couleurs d'une carte  
  
1.  En mode Conception, cliquez sur l'échelle de couleurs de la carte pour la sélectionner. Le volet Propriétés affiche les propriétés de l'élément que vous venez de sélectionner.  
  
2.  Dans le volet Propriétés, dans **NoDataText**, tapez le texte que vous souhaitez afficher sous forme d'étiquette pour les couleurs qui n'ont pas de valeur de données.  
  
     Vous pouvez également cliquer sur l’option **Expression** de la liste déroulante pour ouvrir la boîte de dialogue **Expression** et créer l’expression souhaitée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sous-rapports &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/subreports-report-builder-and-ssrs.md)   
 [Tables, matrices et listes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Cartes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/maps-report-builder-and-ssrs.md)   
 [Sous-rapports &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/subreports-report-builder-and-ssrs.md)  
  
  
