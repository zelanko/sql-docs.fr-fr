---
title: Combiner des données (Complément MDS pour Excel) | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d81fdef23f1d35997aaddce8d6e61e5ce51f76dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65488892"
---
# <a name="combine-data-mds-add-in-for-excel"></a>Combiner des données (Complément MDS pour Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], combinez les données de deux feuilles de calcul lorsque vous souhaitez comparer les données avant la publication. Dans cette procédure, vous combinez les données de deux feuilles de calcul en une seule. Vous pouvez ensuite réaliser d'autres comparaisons et déterminer les données, le cas échéant, à publier dans le référentiel MDS.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Vous devez disposer d'une feuille de calcul qui contient des données gérées par MDS. Pour plus d’informations, consultez [Exporter des données dans Excel depuis Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
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
  
-   Pour rechercher des similitudes entre les données managées MDS et les données externes, consultez [Mettre en correspondance les données similaires &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble : Exportation des données vers Excel &#40;complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Mise en correspondance de la qualité des données dans le complément MDS pour Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  
