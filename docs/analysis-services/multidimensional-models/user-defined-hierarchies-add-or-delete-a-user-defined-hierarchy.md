---
title: "Ajouter ou supprimer une hiérarchie définie par l’utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies [Analysis Services], adding
- removing hierarchies
- adding hierarchies
- deleting hierarchies
- hierarchies [Analysis Services], removing
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
caps.latest.revision: "51"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8d3dd17b2c4b0203164438becdb9aacba9042e92
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="user-defined-hierarchies---add-or-delete-a-user-defined-hierarchy"></a>Hiérarchies définies par l’utilisateur - Ajouter ou supprimer une hiérarchie définie par l’utilisateur
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Ajouter une hiérarchie définie par l’utilisateur ou de supprimer une hiérarchie définie par l’utilisateur d’une dimension sur le **Structure de Dimension** onglet dans le Concepteur de dimensions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Quand vous ajoutez une hiérarchie définie par l’utilisateur, elle ne devient accessible aux utilisateurs qu’à partir du moment où elle est instanciée dans une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et que la dimension est traitée. Pour plus d’informations, consultez [Bases de données de modèle multidimensionnel &#40;SSAS&#41;](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md) et [Traitement d’un modèle multidimensionnel &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-add-a-user-defined-hierarchy-to-a-dimension"></a>Pour ajouter une hiérarchie définie par l'utilisateur à une dimension  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] approprié, puis ouvrez la dimension avec laquelle vous souhaitez travailler.  
  
     La dimension s’ouvre dans le Concepteur de dimensions sous l’onglet **Structure de dimension** .  
  
2.  Dans le volet **Attributs** , faites glisser l’attribut que vous souhaitez utiliser dans la hiérarchie définie par l’utilisateur vers le volet **Hiérarchies** .  
  
3.  Faites glisser des attributs supplémentaires pour former des niveaux dans la hiérarchie définie par l'utilisateur.  
  
     L'ordre dans lequel les attributs sont classés dans la hiérarchie est important. Par exemple, dans une hiérarchie de temps, les années doivent apparaître plus haut que les jours dans la hiérarchie.  
  
4.  Vous pouvez éventuellement réordonner les niveaux dans la nouvelle hiérarchie définie par l'utilisateur en les faisant glisser vers les positions appropriées.  
  
5.  Vous pouvez éventuellement modifier les propriétés de la hiérarchie définie par l'utilisateur ou de ses niveaux.  
  
     Par exemple, vous pouvez spécifier un nom pour la hiérarchie définie par l'utilisateur, renommer un ou plusieurs de ses niveaux et définir un nom personnalisé pour le niveau Tous. Pour plus d’informations, consultez [Propriétés de la hiérarchie définie par l’utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)et [Propriétés de niveau - hiérarchies utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md).  
  
    > [!NOTE]  
    >  Par défaut, une hiérarchie définie par l'utilisateur est un simple chemin d'accès qui permet aux utilisateurs de rechercher des informations. Cependant, s'il existe des relations entre les niveaux, vous pouvez augmenter les performances des requêtes en configurant ces relations d'attributs entre les niveaux. Pour plus d’informations, consultez [Relations d’attributs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) et [Définir des relations d’attributs](../../analysis-services/multidimensional-models/attribute-relationships-define.md).  
  
### <a name="to-remove-a-user-defined-hierarchy-from-a-dimension"></a>Pour supprimer une hiérarchie définie par l'utilisateur d'une dimension  
  
-   Sous l’onglet **Structure de dimension** , cliquez sur la hiérarchie définie par l’utilisateur que vous souhaitez supprimer dans le volet **Hiérarchies** . Dans la barre d’outils, cliquez sur **Supprimer**.  
  
     — ou —  
  
-   Cliquez avec le bouton droit sur la hiérarchie définie par l’utilisateur que vous souhaitez supprimer dans le volet **Hiérarchies** , puis cliquez sur **Supprimer**.  
  
     — ou —  
  
-   Faites glisser la hiérarchie définie par l'utilisateur hors de l'aire de conception.  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Créer des hiérarchies définies par l'utilisateur](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)  
  
  
