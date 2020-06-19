---
title: Combiner des données (Complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f5d939f21c4ebcf3ca7fc9870d4930e2be52e7b5
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84961409"
---
# <a name="combine-data-mds-add-in-for-excel"></a>Combiner des données (Complément MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], combinez les données de deux feuilles de calcul lorsque vous souhaitez comparer les données avant la publication. Dans cette procédure, vous combinez les données de deux feuilles de calcul en une seule. Vous pouvez ensuite réaliser d'autres comparaisons et déterminer les données, le cas échéant, à publier dans le référentiel MDS.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Vous devez disposer d'une feuille de calcul qui contient des données gérées par MDS. Pour plus d’informations, consultez [charger des données à partir de MDS dans Excel](export-data-to-excel-from-master-data-services.md).  
  
-   Vous devez disposer d'une feuille de calcul qui contient les données que vous souhaitez combiner avec les données managées MDS. Cette feuille doit avoir une ligne d'en-tête.  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a>Pour combiner des données non managées dans une feuille managée MDS  
  
1.  Sur la feuille qui contient les données managées MDS, dans le groupe **Publier et valider** , cliquez sur **Combiner des données**.  
  
2.  Dans la boîte de dialogue **Combiner des données** , en regard de la zone de texte **Plage à combiner avec les données MDS** , cliquez sur l'icône. La boîte de dialogue se réduit.  
  
3.  Cliquez sur la feuille contenant les données que vous souhaitez combiner.  
  
4.  Mettez en surbrillance toutes les cellules de la feuille que vous souhaitez combiner, notamment la ligne d'en-tête.  
  
5.  Dans la boîte de dialogue **Combiner des données** , cliquez sur l'icône. La boîte de dialogue se développe.  
  
6.  Pour une colonne répertoriée pour l'entité MDS, sélectionnez une colonne sous **Colonne correspondante**. Toutes les colonnes MDS n'ont pas besoin de colonnes correspondantes.  
  
7.  Cliquez sur **Combiner**. Une colonne **SOURCE** s'affiche, laquelle indique si les données proviennent de MDS ou d'une source externe.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Pour rechercher des similitudes entre les données managées MDS et les données externes, consultez [Mettre en correspondance les données similaires &#40;Complément MDS pour Excel&#41;](match-similar-data-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Chargement de données &#40;Complément MDS pour Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Mise en correspondance de la qualité des données dans le complément MDS pour Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  
