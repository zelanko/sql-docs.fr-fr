---
title: Définir les couleurs d’un graphique à l’aide d’une palette (Générateur de rapports et SSRS) | Microsoft Docs
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: f716dc0189ea509d48888c0dde25ea77e87f4a97
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50027388"
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
  
     Pour plus d'informations sur les valeurs hexadécimales, consultez la [table des couleurs](https://go.microsoft.com/fwlink/?linkid=9258) (en anglais) sur MSDN.  
  
6.  Cliquez sur **Ajouter** pour ajouter d'autres couleurs à la palette.  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
 Si vous utilisez une palette personnalisée, vous pouvez modifier l'ordre des couleurs pour modifier la couleur de différentes séries dans le graphique.  
  
## <a name="see-also"></a> Voir aussi  
 [Mise en forme des couleurs des séries sur un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Spécifier des couleurs cohérentes pour plusieurs graphiques à base de formes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs.md)  
  
  
