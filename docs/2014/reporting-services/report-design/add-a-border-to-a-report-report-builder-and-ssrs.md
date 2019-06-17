---
title: Ajouter une bordure à un rapport (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81412f94-2991-4e58-bc05-5ccc0cbf2a75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5c1cf33c00dc9bf0b2fbf588fea9793e0deabfc2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106880"
---
# <a name="add-a-border-to-a-report-report-builder-and-ssrs"></a>Ajouter une bordure à un rapport (Générateur de rapports et SSRS)
  Vous pouvez entourer un rapport d'une bordure en plaçant celle-ci dans les en-têtes, les pieds de page et le corps du rapport, sans ajouter de lignes ou de rectangles.  
  
 Si vous ajoutez une bordure de rapport apparaissant dans l'en-tête et le pied de page, ne supprimez pas l'en-tête et le pied de page des première et dernière pages du rapport. Sans cela, la bordure pourra être coupée partiellement, en haut et en bas des première et dernières pages du rapport. Pour plus d’informations, consultez [En-têtes et pieds de page &#40;Générateur de rapports et SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-border-to-a-report"></a>Pour ajouter une bordure à un rapport  
  
1.  Cliquez avec le bouton droit dans l’en-tête en dehors de tout élément de l’en-tête, puis cliquez sur **Propriétés d’en-tête**. Sous l'onglet **Bordure** , ajoutez une bordure gauche, supérieure et droite avec le style souhaité.  
  
    > [!NOTE]  
    >  Si vous n'utilisez pas d'en-têtes dans votre rapport, vous pouvez placer des bordures uniquement autour du corps du rapport ; sinon, vous pouvez ajouter des en-têtes à partir de l'onglet **Insérer** .  
  
2.  Cliquez avec le bouton droit dans le corps en dehors de tout élément de l'aire de conception, puis cliquez sur **Propriétés du corps**. Sous l'onglet **Bordure** , ajoutez une bordure gauche et droite avec le style souhaité.  
  
3.  Cliquez avec le bouton droit dans le pied de page en dehors de tout élément du pied de page, puis cliquez sur **Propriétés du pied de page**. Sous l'onglet **Bordure** , ajoutez une bordure gauche, inférieure et droite avec le style souhaité.  
  
## <a name="see-also"></a>Voir aussi  
 [Rectangles et lignes &#40;Générateur de rapports et SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)  
  
  
