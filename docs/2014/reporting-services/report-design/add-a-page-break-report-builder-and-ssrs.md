---
title: Ajouter un saut de page (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3846cd48-2787-47e9-b13b-7fc45a205f68
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: ef49e2d14953aabd281484fe4f19d814fc8c9793
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37266255"
---
# <a name="add-a-page-break-report-builder-and-ssrs"></a>Ajouter un saut de page (Générateur de rapports et SSRS)
  Vous pouvez ajouter un saut de page aux rectangles, régions de données ou groupes dans des régions de données pour contrôler la quantité d'informations sur chaque page. L'ajout de sauts de page peut améliorer les performances des rapports publiés, car seuls les éléments sur chaque page doivent être traités pendant que vous visualisez le rapport. Lorsque le rapport entier est une page unique, tous les éléments doivent être traités avant de pouvoir consulter le rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-break-to-a-data-region"></a>Pour ajouter un saut de page à une région de données  
  
1.  Dans l’aire de conception, cliquez avec le bouton droit sur la poignée d’angle de la région de données, puis cliquez sur **Propriétés du tableau matriciel**.  
  
2.  Sous l'onglet **Général** , sous **Options de saut de page**, sélectionnez l'une des options suivantes :  
  
    -   **Insérer un saut de page avant**. Sélectionnez cette option si vous souhaitez ajouter un saut de page avant le tableau.  
  
    -   **Insérer un saut de page après**. Sélectionnez cette option si vous souhaitez ajouter un saut de page après le tableau.  
  
    -   **Faire tenir le tableau sur une page si possible**. Sélectionnez cette option si vous souhaitez que les données restent sur une page.  
  
### <a name="to-add-a-page-break-to-a-rectangle"></a>Pour ajouter un saut de page à un rectangle  
  
1.  Sur l’aire de conception, cliquez avec le bouton droit sur le rectangle où vous souhaitez ajouter un saut de page, puis cliquez sur **Propriétés du rectangle**.  
  
2.  Sous l'onglet **Général** , sous **Options de saut de page**, sélectionnez l'une des options suivantes :  
  
    -   **Insérer un saut de page avant**. Sélectionnez cette option si vous souhaitez ajouter un saut de page avant le rectangle.  
  
    -   **Insérer un saut de page après**. Sélectionnez cette option si vous souhaitez ajouter un saut de page après le rectangle.  
  
    -   **Omettre la bordure sur le saut de page**. Sélectionnez cette option si vous ne souhaitez pas de bordure sur le saut de page.  
  
    -   **Conserver le contenu sur la même page, si possible**. Sélectionnez cette option lorsque vous souhaitez que le contenu à l'intérieur du rectangle reste sur une page.  
  
### <a name="to-add-a-page-break-to-a-row-group-in-a-table-matrix-or-list"></a>Pour ajouter un saut de page à un groupe de lignes dans un tableau, une matrice ou une liste  
  
1.  Dans le volet Regroupement, cliquez avec le bouton droit sur un groupe de lignes, puis cliquez sur **Propriétés du groupe**.  
  
    > [!NOTE]  
    >  Les sauts de page définis sur les groupes de colonnes sont ignorés.  
  
2.  Sous l'onglet **Sauts de page** , sélectionnez **Entre chaque instance d'un groupe** pour ajouter un saut de page entre chaque instance d'un groupe dans le tableau.  
  
3.  Si vous le souhaitez, sélectionnez **Au début d'un groupe également** ou **À la fin d'un groupe également** pour spécifier qu'un saut de page soit ajouté au début ou à la fin d'un groupe dans le tableau.  
  
## <a name="see-also"></a>Voir aussi  
 [Pagination dans Reporting Services &#40;Générateur de rapports et SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)   
 [En-têtes et pieds de page &#40;Générateur de rapports et SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)  
  
  
