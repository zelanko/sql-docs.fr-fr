---
title: Boîte de dialogue de Dimension de Cube (Analysis Services - données multidimensionnelles) ajouter | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.addcubedimensiondialog.f1
helpviewer_keywords:
- Add Cube Dimension dialog box
ms.assetid: 625a3b1f-183b-445f-9bb7-96945c324767
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ff89f880df12126f173f1f5ad47d1841e532262d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154295"
---
# <a name="add-cube-dimension-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Ajouter une dimension de cube (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Ajouter une dimension de cube** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour ajouter une référence à une dimension de base de données à un cube. Vous pouvez afficher la boîte de dialogue **Ajouter une dimension de cube** en exécutant l'une des opérations suivantes :  
  
-   Cliquez sur **Ajouter une dimension de cube** dans le volet **Barre d'outils** de l'onglet **Structure de cube** ou **Utilisation de la dimension** du Concepteur de cube.  
  
-   Cliquez avec le bouton droit dans le volet **Dimensions** de l’onglet **Structure de cube** du Concepteur de cube et sélectionnez **Ajouter une dimension de cube** dans le menu contextuel.  
  
-   Cliquez avec le bouton droit dans le volet **Grille** de l’onglet **Utilisation de la dimension** du Concepteur de cube et sélectionnez **Ajouter une dimension de cube** dans le menu contextuel.  
  
> [!NOTE]  
>  Chaque dimension de cube ne peut avoir qu'une seule relation avec un groupe de mesures. Toutefois, vous pouvez créer plusieurs dimensions de cube et les ajouter au cube si la dimension de base de données sur laquelle la dimension de cube repose est associée à des groupes de mesures via plusieurs relations dans la vue de source de données. Ces dimensions s'appellent des dimensions de rôle actif et sont généralement utilisées avec les dimensions de temps.  
  
## <a name="options"></a>Options  
 **Sélectionner une dimension**  
 Sélectionnez une dimension de base de données existante pour ajouter une dimension de cube basée sur la dimension de base de données au cube sélectionné. Plusieurs dimensions de cube peuvent être définies depuis une même dimension de base de données.  
  
> [!NOTE]  
>  Si vous ajoutez à un cube plusieurs dimensions de cube basées sur la même dimension de base de données, les dimensions de cube supplémentaires s'appellent des dimensions de rôle actif.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  