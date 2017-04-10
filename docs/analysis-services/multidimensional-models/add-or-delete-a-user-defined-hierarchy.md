---
title: "Ajouter ou supprimer une hi&#233;rarchie d&#233;finie par l&#39;utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "hiérarchies [Analysis Services], ajout"
  - "suppression de hiérarchies"
  - "ajout de hiérarchies"
  - "élimination de hiérarchies"
  - "hiérarchies [Analysis Services], suppression"
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
caps.latest.revision: 51
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Ajouter ou supprimer une hi&#233;rarchie d&#233;finie par l&#39;utilisateur
  Vous pouvez ajouter ou supprimer une hiérarchie définie par l’utilisateur dans une dimension sous l’onglet **Structure de dimension** du Concepteur de dimensions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Quand vous ajoutez une hiérarchie définie par l’utilisateur, elle ne devient accessible aux utilisateurs qu’à partir du moment où elle est instanciée dans une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et que la dimension est traitée. Pour plus d’informations, consultez [Bases de données de modèle multidimensionnel &#40;SSAS&#41;](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md) et [Traitement d’un modèle multidimensionnel &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### Pour ajouter une hiérarchie définie par l'utilisateur à une dimension  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] approprié, puis ouvrez la dimension avec laquelle vous souhaitez travailler.  
  
     La dimension s’ouvre dans le Concepteur de dimensions sous l’onglet **Structure de dimension**.  
  
2.  Dans le volet **Attributs**, faites glisser l’attribut que vous souhaitez utiliser dans la hiérarchie définie par l’utilisateur vers le volet **Hiérarchies**.  
  
3.  Faites glisser des attributs supplémentaires pour former des niveaux dans la hiérarchie définie par l'utilisateur.  
  
     L'ordre dans lequel les attributs sont classés dans la hiérarchie est important. Par exemple, dans une hiérarchie de temps, les années doivent apparaître plus haut que les jours dans la hiérarchie.  
  
4.  Vous pouvez éventuellement réordonner les niveaux dans la nouvelle hiérarchie définie par l'utilisateur en les faisant glisser vers les positions appropriées.  
  
5.  Vous pouvez éventuellement modifier les propriétés de la hiérarchie définie par l'utilisateur ou de ses niveaux.  
  
     Par exemple, vous pouvez spécifier un nom pour la hiérarchie définie par l'utilisateur, renommer un ou plusieurs de ses niveaux et définir un nom personnalisé pour le niveau Tous. Pour plus d’informations, consultez [Propriétés de la hiérarchie définie par l’utilisateur](../Topic/User%20Hierarchy%20Properties.md) et [Propriétés de niveau - hiérarchies utilisateur](../Topic/Level%20Properties%20-%20user%20hierarchies.md).  
  
    > [!NOTE]  
    >  Par défaut, une hiérarchie définie par l'utilisateur est un simple chemin d'accès qui permet aux utilisateurs de rechercher des informations. Cependant, s'il existe des relations entre les niveaux, vous pouvez augmenter les performances des requêtes en configurant ces relations d'attributs entre les niveaux. Pour plus d’informations, consultez [Relations d’attributs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) et [Définir des relations d’attributs](../../analysis-services/multidimensional-models/define-attribute-relationships.md).  
  
### Pour supprimer une hiérarchie définie par l'utilisateur d'une dimension  
  
-   Sous l’onglet **Structure de dimension**, cliquez sur la hiérarchie définie par l’utilisateur que vous souhaitez supprimer dans le volet **Hiérarchies**. Dans la barre d’outils, cliquez sur **Supprimer**.  
  
     — ou —  
  
-   Cliquez avec le bouton droit sur la hiérarchie définie par l’utilisateur que vous souhaitez supprimer dans le volet **Hiérarchies**, puis cliquez sur **Supprimer**.  
  
     — ou —  
  
-   Faites glisser la hiérarchie définie par l'utilisateur hors de l'aire de conception.  
  
## Voir aussi  
 [Hiérarchies utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)   
 [Créer des hiérarchies définies par l'utilisateur](../../analysis-services/multidimensional-models/create-user-defined-hierarchies.md)  
  
  