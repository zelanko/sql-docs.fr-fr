---
title: Filtrer les données avant le chargement (complément MDS pour Excel) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 98cb43795b68a35aeb4b57dc3a70ab001ffbaf8a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155273"
---
# <a name="filter-data-before-loading-mds-add-in-for-excel"></a>Filtrer les données avant le chargement (Complément MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], filtrer les données lorsque vous souhaitez limiter la taille ou l’étendue des données que vous chargez dans Excel.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
### <a name="to-filter-data-before-loading"></a>Pour filtrer les données avant le chargement  
  
1.  Ouvrez Excel et accédez à l'onglet **Données de référence** , puis connectez-vous à un référentiel MDS. Pour plus d’informations, consultez [Se connecter à un référentiel MDS &#40;complément MDS pour Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Dans le volet **Explorateur de données de référence** , sélectionnez un modèle et une version. La liste des entités est remplie.  
  
    -   Si le volet **Explorateur de données de référence** n'est pas visible, dans le groupe **Se connecter et charger** , cliquez sur **Afficher l'Explorateur**.  
  
    -   Si le volet **Explorateur de données de référence** est désactivé, cela signifie que la feuille de calcul existante contient déjà des données managées MDS. Pour activer le volet, ouvrez une nouvelle feuille de calcul.  
  
3.  Dans le volet **Explorateur de données de référence** , dans la liste des entités, cliquez sur l'entité à filtrer.  
  
4.  Sur le ruban, dans le groupe **Se connecter et charger** , cliquez sur **Filtre**.  
  
5.  Remplissez la boîte de dialogue **Filtrer** en sélectionnant les attributs (colonnes) à afficher, en définissant l'ordre des colonnes, et si nécessaire, en filtrant les données afin de retourner moins de lignes. Affichez le volet **Résumé** pour connaître le volume des données qui seront retournées. Pour plus d’informations, consultez [Boîte de dialogue Filtrer &#40;Complément MDS pour Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Cliquez sur **Charger les données**. La feuille est renseignée avec les données managées MDS.  
  
    > [!NOTE]  
    >  -   Seul le premier million de membres est chargé dans Excel.  
    > -   Dans les colonnes qui représentent des listes contraintes (attributs basés sur un domaine), seules les 1 000 premières valeurs sont chargés.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Publier des données à partir d’Excel vers MDS &#40;complément MDS pour Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Le chargement des données &#40;complément MDS pour Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Boîte de dialogue Filtrer &#40;Complément MDS pour Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md)   
 [Réorganiser les colonnes &#40;complément MDS pour Excel&#41;](reorder-columns-mds-add-in-for-excel.md)  
  
  