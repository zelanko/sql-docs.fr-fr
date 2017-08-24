---
title: "Filtrer les données avant l’exportation (complément MDS pour Excel) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d3bc2b1200364c76321c127823c0b9a6161fe4d0
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="filter-data-before-exporting-mds-add-in-for-excel"></a>Filtrer les données avant l’exportation (complément MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], filtrer les données lorsque vous souhaitez limiter la taille ou l’étendue des données que vous exportez vers Excel.  
  
## <a name="prerequisites"></a>Configuration requise  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
### <a name="to-filter-data-before-exporting"></a>Pour filtrer les données avant l’exportation  
  
1.  Ouvrez Excel et accédez à l'onglet **Données de référence** , puis connectez-vous à un référentiel MDS. Pour plus d’informations, consultez [Se connecter à un référentiel MDS &#40;complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Dans le volet **Explorateur de données de référence** , sélectionnez un modèle et une version. La liste des entités est remplie.  
  
    -   Si le volet **Explorateur de données de référence** n'est pas visible, dans le groupe **Se connecter et charger** , cliquez sur **Afficher l'Explorateur**.  
  
    -   Si le volet **Explorateur de données de référence** est désactivé, cela signifie que la feuille de calcul existante contient déjà des données managées MDS. Pour activer le volet, ouvrez une nouvelle feuille de calcul.  
  
3.  Dans le volet **Explorateur de données de référence** , dans la liste des entités, cliquez sur l'entité à filtrer.  
  
4.  Sur le ruban, dans le groupe **Se connecter et charger** , cliquez sur **Filtre**.  
  
5.  Remplissez la boîte de dialogue **Filtrer** en sélectionnant les attributs (colonnes) à afficher, en définissant l'ordre des colonnes, et si nécessaire, en filtrant les données afin de retourner moins de lignes. Affichez le volet **Résumé** pour connaître le volume des données qui seront retournées. Pour plus d’informations, consultez [boîte de dialogue filtre &#40; Complément MDS pour Excel &#41; ](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Cliquez sur **Charger les données**. La feuille est renseignée avec les données managées MDS.  
  
    > [!NOTE]  
    >  -   Seul le premier million de membres est chargé dans Excel.  
    > -   Dans les colonnes qui représentent des listes contraintes (attributs basés sur un domaine), seules les 25 000 premières valeurs sont chargées par défaut.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Publier des données d’Excel dans Master Data Services &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble : exportation de données vers Excel &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Boîte de dialogue filtre &#40; Complément MDS pour Excel &#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Réorganiser des colonnes &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  
