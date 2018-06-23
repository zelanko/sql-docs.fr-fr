---
title: Fusionner des cellules dans une région de données (Générateur de rapports et SSRS)| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43551300-89b2-4f4e-af09-69084324afaf
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 31dcb2ef4f2d4881bd2e4ffb94865c9a9d71faad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152492"
---
# <a name="merge-cells-in-a-data-region-report-builder-and-ssrs"></a>Fusionner des cellules dans une région de données (Générateur de rapports et SSRS)
  Vous pouvez fusionner des cellules dans une région de données pour les combiner, améliorer l'apparence de la région de données ou fournir des étiquettes étendues pour les groupes de colonnes et de lignes.  
  
> [!NOTE]  
>  Les cellules peuvent uniquement être fusionnées à l'intérieur de chaque zone d'une région de données : angle, en-têtes de colonne, définition de groupe (ou en-têtes de ligne) et corps. Vous ne pouvez pas fusionner de cellules dépassant les limites de la zone. Vous ne pouvez par exemple pas fusionner une cellule située dans la zone d'angle de la région de données avec une cellule située dans la zone de groupe de lignes. Pour plus d’informations sur les zones de tableau matriciel, consultez [répertorie &#40;le Générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-merge-cells-in-a-data-region"></a>Pour fusionner des cellules dans une région de données  
  
1.  Dans la région de données sur l'aire de conception du rapport, cliquez sur la première cellule à fusionner. Tout en maintenant le bouton gauche de la souris enfoncé, faites glisser verticalement ou horizontalement la souris pour sélectionner des cellules adjacentes. Les cellules sélectionnées sont mises en surbrillance.  
  
2.  Cliquez avec le bouton droit sur les cellules sélectionnées, puis sélectionnez **Fusionner les cellules**. Les cellules sélectionnées sont combinées en une seule cellule.  
  
3.  Répétez les étapes 1 et 2 pour fusionner d'autres cellules adjacentes dans une région de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tables &#40;Générateur de rapports et SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrices &#40;Générateur de rapports et SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Listes &#40;Générateur de rapports et SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Listes &#40;Générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  