---
title: Ajouter un rectangle ou un conteneur (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10061"
- sql12.rtp.rptdesigner.rectangleproperties.general.f1
ms.assetid: f905c35f-754d-4d02-80f3-85e29ddda826
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: d1cac8525b9343cc2719cd38d278f55b89839bbf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139742"
---
# <a name="add-a-rectangle-or-container-report-builder-and-ssrs"></a>Ajouter un rectangle ou un conteneur (Générateur de rapports et SSRS)
  Ajoutez un rectangle à votre rapport lorsque vous souhaitez qu'un élément graphique sépare des zones du rapport, accentue des zones d'un rapport ou fournisse un arrière-plan pour un ou plusieurs éléments de rapport. Les rectangles sont également utilisés comme conteneurs qui aident à contrôler la façon dont les régions de données sont rendues dans un rapport. Vous pouvez personnaliser l'apparence d'un rectangle en modifiant ses propriétés, telles que les couleurs d'arrière-plan et de bordure. Pour plus d’informations sur l’utilisation d’un rectangle comme conteneur, consultez [Rectangles et lignes &#40;Générateur de rapports et SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) et [Afficher les mêmes données dans une matrice et sur un graphique &#40;Générateur de rapports&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-rectangle"></a>Pour ajouter un rectangle  
  
1.  Sous l'onglet **Insérer** , dans le groupe **Éléments de rapport** , cliquez sur **Rectangle**.  
  
2.  Dans l'aire de conception, cliquez sur l'endroit où doit venir se positionner le coin supérieur gauche du rectangle, puis faites glisser la souris jusqu'à l'endroit où doit venir se positionner son coin supérieur droit.  
  
     Notez qu'à mesure que vous déplacez le curseur, des lignes d'alignement apparaissent lorsque le curseur est aligné avec d'autres objets dans l'aire de conception. Ces lignes d'alignement vous aident à aligner des objets.  
  
### <a name="to-create-a-container"></a>Pour créer un conteneur  
  
1.  Ajoutez un élément de rapport de type rectangle au rapport.  
  
2.  Faites glisser d'autres éléments de rapport dans le rectangle.  
  
    > [!NOTE]  
    >  Un rectangle est uniquement un conteneur pour les éléments que vous créez dans le rectangle ou que vous faites glisser dans le rectangle. Si vous dessinez un rectangle autour d'un élément qui existe déjà dans l'aire de conception, le rectangle n'agit pas comme son conteneur.  
  
### <a name="to-change-rectangle-properties-such-as-color-style-or-weight"></a>Pour modifier les propriétés d'un rectangle, telles que la couleur, le style ou l'épaisseur  
  
1.  Sélectionnez le rectangle, puis cliquez sur les options de couleur, de style ou d'épaisseur de ligne dans la section **Bordure** de l'onglet Accueil.  
  
2.  Cliquez sur la flèche en regard du bouton **Bordure** pour déterminer les côtés du rectangle à modifier.  
  
    > [!NOTE]  
    >  Si vous définissez le style de ligne à **Double** et la largeur de ligne est 1, 1/2 pt ou plus étroite, la ligne ne peut pas apparaître deux fois lorsque vous exécutez le rapport dans le Générateur de rapports, le Concepteur de rapports ou le Gestionnaire de rapports. Elle apparaît en double lorsque vous exportez le rapport sous d'autres formats, tels que Microsoft Word et Acrobat PDF.  
  
## <a name="see-also"></a>Voir aussi  
 [Rectangles et lignes &#40;rapport Générateur et SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)   
 [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)  
  
  