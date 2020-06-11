---
title: Remplacer une table ou une requête nommée dans une vue de source de données (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- replacing tables
- data source views [Analysis Services], tables
- named queries [Analysis Services], replacing tables
- tables [Analysis Services], data source views
- partitions [Analysis Services], named queries
ms.assetid: 60c2a018-1299-4915-b60e-e73316524def
author: minewiskan
ms.author: owend
ms.openlocfilehash: b625081a4b7cafaab537e91f9c2730578d37efab
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545753"
---
# <a name="replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services"></a>Remplacer une table ou une requête nommée dans une vue de source de données (Analysis Services)
  Dans le Concepteur de vue de source de données, vous pouvez remplacer une table, une vue ou une requête nommée dans une vue de source de données (DSV) par une autre table ou vue provenant de la même source de données ou d'une source de données différente ou par une requête nommée définie dans la vue DSV. Quand vous remplacez une table, tous les autres objets qui figurent dans un projet ou une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et qui contiennent des références à la table continuent à faire référence à la table, car l’ID d’objet de la table reste le même dans la vue DSV. Toutes les relations qui continuent à être pertinentes (correspondance des noms et des types de colonne) sont conservées. Par contre, si vous supprimez une table et que vous en ajoutez une autre, les références et les relations sont supprimées et doivent être recréées.  
  
 Pour pouvoir remplacer une table par une autre table, vous devez disposer d'une connexion active avec les données sources du Concepteur de vue de source de données en mode projet.  
  
 La plupart du temps, vous remplacez une table de la vue de source de données par une autre table de la source de données. Cependant, vous pouvez également remplacer une requête nommée par une table. Par exemple, vous pouvez avoir remplacé une table par une requête nommée et vouloir maintenant revenir à une table.  
  
> [!IMPORTANT]  
>  Si vous renommez une table dans une source de données, suivez la procédure de remplacement d'une table et définissez la table renommée en tant que source de la table correspondante dans la vue DSV avant d'actualiser une vue DSV. Le fait de mettre fin au processus de remplacement et de changement de nom permet de conserver la table, les références de la table et les relations de la table dans la vue DSV. Sinon, lorsque vous actualisez la vue DSV, la table renommée dans la source de données est considérée comme supprimée. Pour plus d’informations, consultez [Actualiser le schéma dans une vue de source de données &#40;Analysis Services&#41;](refresh-the-schema-in-a-data-source-view-analysis-services.md).  
  
##  <a name="replace-a-table-with-a-named-query"></a><a name="bkmk_nq"></a> Remplacer une table par une requête nommée  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet ou connectez-vous à la base de données qui contient la vue de source de données dans laquelle vous souhaitez remplacer une table ou une requête nommée.  
  
2.  Dans l’Explorateur de solutions, développez le dossier **Vues des sources de données** , puis double-cliquez sur la vue de source de données.  
  
3.  Ouvrez la boîte de dialogue **Créer une requête nommée** . Dans le volet **Tables** ou **Diagramme** , cliquez avec le bouton droit sur la table que vous souhaitez remplacer, pointez sur **Remplacer la table** , puis cliquez sur **Par la nouvelle requête nommée**.  
  
4.  Dans la boîte de dialogue **Créer une requête nommée** , définissez la requête nommée, puis cliquez sur **OK**.  
  
5.  Enregistrez la vue de source de données modifiée.  
  
## <a name="replace-a-table-or-named-query-with-a-table"></a>Remplacer une table ou une requête nommée par une table  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet ou connectez-vous à la base de données qui contient la vue de source de données dans laquelle vous souhaitez remplacer une table ou une requête nommée.  
  
2.  Dans l’Explorateur de solutions, développez le dossier **Vues des sources de données** , puis double-cliquez sur la vue de source de données.  
  
3.  Ouvrez la boîte de dialogue **Remplacer la table par une autre table** . Dans le volet **Tables** ou **Diagramme** , cliquez avec le bouton droit sur la table ou la requête nommée que vous souhaitez remplacer, pointez sur **Remplacer la table** , puis cliquez sur **Par une autre table**.  
  
4.  Dans la boîte de dialogue **Remplacer la table par une autre table** :  
  
    1.  Dans la zone de liste déroulante **Source de données** , sélectionnez la source de données souhaitée.  
  
    2.  Sélectionnez la table par laquelle vous souhaitez remplacer la table ou la requête nommée  
  
5.  Cliquez sur **OK**.  
  
6.  Enregistrez la vue de source de données modifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md)  
  
  
