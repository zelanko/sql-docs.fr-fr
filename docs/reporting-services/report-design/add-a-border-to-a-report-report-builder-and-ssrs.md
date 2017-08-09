---
title: "Ajouter une bordure à un rapport (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81412f94-2991-4e58-bc05-5ccc0cbf2a75
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 824ca565b87a77add1c547aafb264345a9a63dab
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="add-a-border-to-a-report-report-builder-and-ssrs"></a>Ajouter une bordure à un rapport (Générateur de rapports et SSRS)
  Vous pouvez entourer un rapport paginé [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] d’une bordure en plaçant celle-ci dans les en-têtes, les pieds de page et le corps du rapport, sans ajouter de lignes ou de rectangles.    
    
 Si vous ajoutez une bordure de rapport apparaissant dans l'en-tête et le pied de page, ne supprimez pas l'en-tête et le pied de page des première et dernière pages du rapport. Sans cela, la bordure pourra être coupée partiellement, en haut et en bas des première et dernières pages du rapport. Pour plus d’informations, consultez [En-têtes et pieds de page &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md).    
    
## <a name="to-add-a-border-to-a-report"></a>Pour ajouter une bordure à un rapport    
    
1.  Cliquez avec le bouton droit dans l’en-tête en dehors de tout élément de l’en-tête, puis cliquez sur **Propriétés d’en-tête**. Sous l'onglet **Bordure** , ajoutez une bordure gauche, supérieure et droite avec le style souhaité.    
    
    > [!NOTE]    
    >  Si votre rapport n’a pas d’en-têtes, vous pouvez placer des bordures uniquement autour du corps du rapport ; sinon, vous pouvez ajouter des en-têtes à partir de l’onglet **Insérer** .    
    
2.  Cliquez avec le bouton droit dans le corps en dehors de tout élément de l’aire de conception, puis cliquez sur **Propriétés du corps**. Sous l'onglet **Bordure** , ajoutez une bordure gauche et droite avec le style souhaité.    
    
3.  Cliquez avec le bouton droit dans le pied de page en dehors de tout élément du pied de page, puis cliquez sur **Propriétés du pied de page**. Sous l'onglet **Bordure** , ajoutez une bordure gauche, inférieure et droite avec le style souhaité.    
    
## <a name="see-also"></a>Voir aussi    
 [Rectangles et lignes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/rectangles-and-lines-report-builder-and-ssrs.md)    
    
  
