---
title: Charger des données à partir de MDS dans Excel | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: bbe1188773d0770ff345cd54ea47e03a3c05555f
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65482713"
---
# <a name="load-data-from-mds-into-excel"></a>Charger des données MDS dans Excel
  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous devez charger des données à partir du référentiel MDS afin des pour manipuler.  
  
 Si vous souhaitez filtrer le dataset avant le chargement, consultez [filtrer les données avant le chargement &#40;complément MDS pour Excel&#41; ](filter-data-before-exporting-mds-add-in-for-excel.md) à la place.  
  
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
 [Publier des données à partir d’Excel dans MDS &#40;complément MDS pour Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Le chargement des données &#40;complément MDS pour Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Boîte de dialogue Filtrer &#40;Complément MDS pour Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md)   
 [Publication de données &#40;complément MDS pour Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
