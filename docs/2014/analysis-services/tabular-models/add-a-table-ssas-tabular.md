---
title: Ajouter une Table (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: d713c432-db99-4983-acc1-52b0fdd58bd6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 065cec0c70d0b98131dc4cdc5b477b11115091f8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62757648"
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
 [Importer des données &#40;SSAS Tabulaire&#41;](../import-data-ssas-tabular.md)   
 [Supprimer une table &#40;SSAS Tabulaire&#41;](delete-a-table-ssas-tabular.md)  
  
  
