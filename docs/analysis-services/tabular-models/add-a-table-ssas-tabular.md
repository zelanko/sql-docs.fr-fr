---
title: Ajouter une Table (SSAS tabulaire) | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d713c432-db99-4983-acc1-52b0fdd58bd6
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 95113c2053b0e37cc4ee3d94d2baf0ed64d71d57
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="add-a-table-ssas-tabular"></a>Ajouter une table (SSAS Tabulaire)
  Cette rubrique explique comment ajouter une table à partir d'une source de données dans laquelle vous avez précédemment importé des données dans votre modèle. Pour ajouter une table à partir de la même source de données, vous pouvez utiliser la connexion à la source de données existante. Il est recommandé d'utiliser toujours une connexion unique lorsque vous importez plusieurs tables à partir d'une source de données unique.  
  
### <a name="to-add-a-table-from-an-existing-data-source"></a>Pour ajouter une table à partir d'une source de données existante  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Connexions existantes**.  
  
2.  Dans la page **Connexions existantes** , sélectionnez la connexion à la source de données qui contient la table à ajouter, puis cliquez sur **Ouvrir**.  
  
3.  Dans la page **Sélectionner des tables et des vues** , sélectionnez la table à partir de la source de données à ajouter à votre modèle.  
  
    > [!NOTE]  
    >  La page **Sélectionner des tables et des vues** n’affiche pas les tables précédemment importées comme vérifiées.  Si vous sélectionnez une table qui a été précédemment importées au moyen de cette connexion, et si vous ne donnez pas à la table un nom convivial différent, un « 1 » sera ajouté au nom convivial. Vous n'avez pas besoin de resélectionner les tables qui ont été précédemment importées à l'aide de cette connexion.  
  
4.  Si nécessaire, utilisez **Afficher un aperçu et filtrer** pour sélectionner uniquement certaines colonnes ou appliquer des filtres aux données à importer.  
  
5.  Cliquez sur **Terminer** pour importer la nouvelle table.  
  
> [!NOTE]  
>  Lorsque vous importez plusieurs tables simultanément à partir d'une seule source de données, les relations entre ces tables à la source sont automatiquement créées dans le modèle. Si vous ajoutez une table ultérieurement, toutefois, vous devrez peut-être créer manuellement des relations dans le modèle entre les tables récemment ajoutées et les tables précédemment importées.  
  
## <a name="see-also"></a>Voir aussi  
 [Importer des données &#40;SSAS Tabulaire&#41;](http://msdn.microsoft.com/library/6617b2a2-9f69-433e-89e0-4c5dc92982cf)   
 [Supprimer une table &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/delete-a-table-ssas-tabular.md)  
  
  
