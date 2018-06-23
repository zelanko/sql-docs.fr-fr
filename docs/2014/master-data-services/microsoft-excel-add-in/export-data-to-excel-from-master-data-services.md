---
title: Charger des données à partir de MDS dans Excel | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8bee7252d1adfcce827eadbd62cb7d38416d7596
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051060"
---
# <a name="load-data-from-mds-into-excel"></a>Charger des données MDS dans Excel
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous devez charger les données à partir du référentiel MDS afin des pour manipuler.  
  
 Si vous souhaitez filtrer le dataset avant le chargement, consultez [avant le chargement des données de filtre &#40;complément MDS pour Excel&#41; ](filter-data-before-exporting-mds-add-in-for-excel.md) à la place.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
### <a name="to-load-data-from-mds-into-excel"></a>Pour charger des données MDS dans Excel  
  
1.  Ouvrez Excel et accédez à l'onglet **Données de référence** , puis connectez-vous à un référentiel MDS. Pour plus d’informations, consultez [Se connecter à un référentiel MDS &#40;complément MDS pour Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Dans le volet **Explorateur de données de référence** , sélectionnez un modèle et une version. La liste des entités est remplie.  
  
    -   Si le volet **Explorateur de données de référence** n'est pas visible, dans le groupe **Se connecter et charger** , cliquez sur **Afficher l'Explorateur**.  
  
    -   Si le volet **Explorateur de données de référence** est désactivé, cela signifie que la feuille de calcul existante contient déjà des données managées MDS. Pour activer le volet, ouvrez une nouvelle feuille de calcul.  
  
3.  Dans le volet **Explorateur de données de référence** , dans la liste des entités, double-cliquez sur l’entité à charger.  
  
    > [!NOTE]  
    >  -   Seul le premier million de membres est chargé dans Excel. Pour filtrer la liste avant le chargement, dans le ruban, dans le groupe **Se connecter et charger** , cliquez sur **Filtre**.  
    > -   Dans les colonnes qui représentent des listes contraintes (attributs basés sur un domaine), seules les 25 000 premières valeurs sont chargées. Vous pouvez modifier ce nombre dans la propriété MaximumDbaEntitySize du fichier excelusersettings.config situé sur l'ordinateur sur lequel Excel est installé. Ce fichier se trouve dans C:\Users\\< utilisateur\>\AppData\Local\Microsoft\Microsoft SQL Server\120\MasterDataServices\\.  
  
    > [!NOTE]  
    >  Quand vous chargez des données de texte délimitées à l’aide du complément pour Microsoft Excel avec Excel 32 bits et que les paramètres des propriétés **Nombre de cellules à charger** et **Nombre de cellules à publier** ont une valeur maximale de 1000, une erreur de mémoire insuffisante se produit. Vous devez utiliser Excel 64 bits pour utiliser les paramètres maximaux de **Nombre de cellules à charger** et **Nombre de cellules à publier**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Publier des données à partir d’Excel vers MDS &#40;complément MDS pour Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Le chargement des données &#40;complément MDS pour Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Boîte de dialogue Filtrer &#40;Complément MDS pour Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md)   
 [Publication de données &#40;complément MDS pour Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  