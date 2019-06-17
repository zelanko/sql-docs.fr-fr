---
title: Définir l’orientation d’une zone de texte (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6acffc286e913d35846b2eeb156cf1980b42fab3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66104978"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>Définir l'orientation d'une zone de texte (Générateur de rapports et SSRS)
  Une zone de texte peut être orientée dans différentes directions : horizontalement, verticalement (texte lu de haut en bas) ou rotation de 270 degrés (texte lu de bas en haut). Étant donné que l'orientation concerne la zone de texte, et non le texte, elle s'applique à l'ensemble du texte dans la zone de texte. Vous ne pouvez pas spécifier d'orientations différentes pour certaines parties du texte. Dimensionnez manuellement la largeur de colonne et la hauteur de ligne pour les adapter au texte pivoté.  
  
 La propriété WritingMode, qui vous permet de spécifier l’orientation de texte, n’est pas disponible dans le **propriétés de la zone texte** boîte de dialogue. Vous devez ouvrir le volet Propriétés et y définir la propriété. Les valeurs disponibles pour la propriété WritingMode sont **Horizontal** (texte lu de gauche à droite), **Vertical** (texte lu de haut en bas), **Rotate270** (texte lu bas en haut). Vous devez dimensionner manuellement la largeur de colonne et la hauteur de ligne pour ajuster le texte.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a>Pour définir l'orientation du texte  
  
1.  Créez un rapport ou ouvrez-en un qui existe déjà.  
  
2.  Si le volet Propriétés n'est pas ouvert, cliquez sur l'onglet **Affichage** et activez la case à cocher **Propriétés** .  
  
3.  Cliquez sur la zone de texte pour laquelle vous souhaitez modifier l'orientation du texte.  
  
4.  Recherchez la valeur WritingMode propriété dans le volet Propriétés et dans la liste déroulante Sélectionner l’orientation du texte à appliquer à la zone de texte.  
  
    > [!NOTE]  
    >  Quand les propriétés du volet Propriétés sont organisées en catégories, WritingMode figure dans la catégorie **Localisation** .  
  
5.  Dans la zone de liste, sélectionnez **Horizontal**, **Vertical**ou **Rotate270**.  
  
## <a name="see-also"></a>Voir aussi  
 [Zones de texte &#40;Générateur de rapport et SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [Tutoriel : Mettre en forme du texte &#40;Générateur de rapports&#41;](../tutorial-format-text-report-builder.md)  
  
  
