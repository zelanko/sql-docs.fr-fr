---
title: Définir un message d’absence de données pour une région de données (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f2660582b03a121a81976d6bbc12afc1213877c3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107085"
---
# <a name="set-a-no-data-message-for-a-data-region-report-builder-and-ssrs"></a>Définir un message d'absence de données pour une région de données (Générateur de rapports et SSRS)
  Quand vous souhaitez qu’un texte s’affiche dans le rapport rendu à la place d’une région de données ne contenant pas de données, vous devez définir la propriété NoRowsMessage de la région de données de table, de matrice ou de liste souhaitée, la propriété NoDataMessage de la région de données de graphique et la propriété NoDataText de l’échelle de couleurs de la carte. Au moment de l'exécution, le processeur de rapports exécute la requête pour chaque dataset d'un rapport et la requête de dataset peut ne produire aucun jeu de résultats. Pour une région de données liée à un dataset vide, vous pouvez spécifier le texte à afficher à la place de la région de données vide. Vous pouvez également définir la propriété NoRowsMessage pour un sous-rapport quand aucun dataset de ce dernier ne contient de données au moment de l’exécution.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-norowsmessage-property-for-a-table-matrix-or-list"></a>Pour définir la propriété NoRowsMessage d'une table, matrice ou liste spécifique  
  
1.  En mode Conception, sur l'aire de conception, cliquez sur la table, la matrice, la région de données de type liste ou le sous-rapport souhaité pour sélectionner celle-ci / celui-ci. Le volet Propriétés affiche les propriétés de l'élément que vous venez de sélectionner.  
  
2.  Dans le volet Propriétés, tapez le texte que vous souhaitez afficher en tant que message dans `NoRowsMessage` le champ de propriété.  
  
     Vous pouvez également cliquer sur l’option **Expression** de la liste déroulante pour ouvrir la boîte de dialogue **Expression** et créer l’expression souhaitée.  
  
### <a name="to-set-the-nodatamessage-property-for-a-chart"></a>Pour définir la propriété NoDataMessage d'un graphique  
  
1.  En mode Conception, sur l'aire de conception, cliquez sur le graphique souhaité pour le sélectionner. Le volet Propriétés affiche les propriétés de l'élément que vous venez de sélectionner.  
  
2.  Dans le volet Propriétés, développez le nœud `NoDataMessage`pour.  
  
3.  Dans **légende**, tapez le texte que vous souhaitez afficher en tant que message dans `NoDataMessage` le champ de propriété.  
  
     Vous pouvez également cliquer sur l’option **Expression** de la liste déroulante pour ouvrir la boîte de dialogue **Expression** et créer l’expression souhaitée.  
  
### <a name="to-set-the-norowsmessage-for-a-subreport"></a>Pour définir la propriété NoRowsMessage d'un sous-rapport  
  
1.  En mode Conception, sur l'aire de conception, cliquez sur le sous-rapport souhaité pour le sélectionner. Le volet Propriétés affiche les propriétés de l'élément que vous venez de sélectionner.  
  
2.  Dans le volet Propriétés, tapez le texte que vous souhaitez afficher en tant que message dans `NoRowsMessage` le champ de propriété.  
  
     Vous pouvez également cliquer sur l’option **Expression** de la liste déroulante pour ouvrir la boîte de dialogue **Expression** et créer l’expression souhaitée.  
  
### <a name="to-set-the-nodatatext-property-for-a-color-scale-for-a-map"></a>Pour définir la propriété NoDataText de l'échelle de couleurs d'une carte  
  
1.  En mode Conception, cliquez sur l'échelle de couleurs de la carte pour la sélectionner. Le volet Propriétés affiche les propriétés de l'élément que vous venez de sélectionner.  
  
2.  Dans le volet Propriétés, dans `NoDataText`, tapez le texte que vous souhaitez afficher en tant qu’étiquette pour les couleurs sans valeur de données.  
  
     Vous pouvez également cliquer sur l’option **Expression** de la liste déroulante pour ouvrir la boîte de dialogue **Expression** et créer l’expression souhaitée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sous-rapports &#40;Générateur de rapports et SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md)   
 [Tables, matrices et listes &#40;Générateur de rapports et SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md)   
 [Cartes &#40;Générateur de rapports et SSRS&#41;](../report-design/maps-report-builder-and-ssrs.md)   
 [Sous-rapports &#40;Générateur de rapports et SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md)  
  
  
