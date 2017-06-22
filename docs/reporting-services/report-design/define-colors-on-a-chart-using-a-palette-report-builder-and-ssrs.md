---
title: "Définir les couleurs d’un graphique à l’aide d’une Palette (Générateur de rapports et SSRS) | Documents Microsoft"
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
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c244f75603ae96dad15c98411bffe223b2857b56
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs"></a>Définir les couleurs d'un graphique à l'aide d'une palette (Générateur de rapports et SSRS)
  Vous pouvez modifier la palette de couleurs d'un graphique en sélectionnant une palette prédéfinie ou en définissant une palette personnalisée. Les palettes personnalisées sont spécifiques au rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-colors-on-the-chart-using-a-built-in-color-palette"></a>Pour modifier les couleurs sur le graphique à l'aide d'une palette de couleurs prédéfinie  
  
1.  Ouvrez le volet Propriétés.  
  
2.  Dans l'aire de conception, cliquez sur le graphique. Les propriétés de l'objet graphique sont affichées dans le volet Propriétés.  
  
     Le nom de l’objet (**Chart1** par défaut) apparaît dans la liste déroulante en haut du volet Propriétés.  
  
3.  Dans la section **Chart** , sélectionnez une nouvelle palette dans la liste déroulante pour la propriété Palette.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas modifier les couleurs ou l'ordre dans une palette prédéfinie.  
  
### <a name="to-define-your-own-colors-on-the-chart-using-a-custom-color-palette"></a>Pour définir vos propres couleurs sur le graphique à l'aide d'une palette de couleurs personnalisée  
  
1.  Ouvrez le volet Propriétés.  
  
2.  Dans l'aire de conception, cliquez sur le graphique. Les propriétés de l'objet graphique sont affichées dans le volet Propriétés.  
  
3.  Dans la section **Graphique** , pour la propriété **Palette** , sélectionnez **Personnalisée**.  
  
4.  Dans la propriété CustomPaletteColors, cliquez sur le bouton Modifier la collection (**…**). L' **Éditeur de collection ReportColorExpression** s'ouvre.  
  
5.  Cliquez sur **Ajouter** pour ajouter une couleur. Sélectionnez une couleur dans la liste déroulante ou sélectionnez Expression et spécifiez une valeur hexadécimale correspondant à une couleur spécifique, par exemple ff6600 pour l'orange.  
  
     Pour plus d'informations sur les valeurs hexadécimales, consultez la [table des couleurs](http://go.microsoft.com/fwlink/?linkid=9258) (en anglais) sur MSDN.  
  
6.  Cliquez sur **Ajouter** pour ajouter d'autres couleurs à la palette.  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
 Si vous utilisez une palette personnalisée, vous pouvez modifier l'ordre des couleurs pour modifier la couleur de différentes séries dans le graphique.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des couleurs des séries sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Spécifier des couleurs cohérentes pour plusieurs graphiques à base de formes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs.md)  
  
  
