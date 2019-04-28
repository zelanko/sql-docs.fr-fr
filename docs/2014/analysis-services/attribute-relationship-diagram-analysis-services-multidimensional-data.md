---
title: Diagramme des relations (onglet Concepteur relations d’attributs, Concepteur de dimensions) d’attribut (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.ardesigner.ardiagram.f1
ms.assetid: 320989ad-bd95-43f4-a2e7-b262d66dbda7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1255cbcaffe114a47b4c7d251c37e5b3d50d6b2b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62650600"
---
# <a name="attribute-relationship-diagram-attribute-relationship-designer-tab-dimension-designer-analysis-services---multidimensional-data"></a>Diagramme des relations d'attributs (onglet Concepteur de relations d'attributs, Concepteur de dimensions) (Analysis Services - Données multidimensionnelles)
  Le volet situé immédiatement sous la barre d'outils dans l'onglet **Relations d'attribut** permet d'afficher le diagramme des relations d'attributs et de créer, modifier et supprimer des relations d'attributs.  
  
 **Pour afficher le volet qui contient le diagramme des relations d’attribut**  
  
-   Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans l’Explorateur de solutions, double-cliquez sur une dimension pour ouvrir le Concepteur de dimensions, puis cliquez sur l’onglet **Relation d’attribut** .  
  
## <a name="using-the-attribute-relationship-diagram"></a>Utilisation du diagramme des relations d'attributs  
 Utilisez le diagramme des relations d'attributs pour créer, modifier ou supprimer des relations d'attributs. Le diagramme des relations d'attributs mettra également en surbrillance les relations d'attributs problématiques et affichera une description du problème dans une info-bulle.  
  
 Trois menus contextuels différents sont disponibles dans le diagramme : le menu contextuel diagramme, le menu contextuel attribut et le menu contextuel relation.  
  
### <a name="diagram-shortcut-menu"></a>Menu contextuel diagramme  
 Pour ouvrir le menu contextuel du diagramme des relations d'attributs, cliquez avec le bouton droit sur l'arrière-plan du diagramme. Le menu contextuel diagramme dispose des commandes suivantes :  
  
 **Nouvelle relation d’attribut**  
 Ouvre la boîte de dialogue **Créer une relation d’attribut** dans laquelle vous pouvez définir une nouvelle relation d’attribut.  
  
 Pour plus d’informations, consultez [Boîtes de dialogue Créer une relation d’attribut et Modifier la relation d’attribut &#40;onglet Concepteur de relations d’attributs, Concepteur de dimensions&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) et [Définir des relations d’attributs](multidimensional-models/attribute-relationships-define.md).  
  
 **Organiser les formes**  
 Organise les formes d'après l'algorithme de disposition utilisé par le Concepteur de dimensions.  
  
 **Organiser automatiquement les formes**  
 Organise automatiquement les formes dans le diagramme d'après l'algorithme de disposition utilisé par le Concepteur de dimensions. Par défaut, l'option **Organiser automatiquement les formes** est activée.  
  
 **Afficher les affichages en liste**  
 Affiche ou masque les listes **Attributs** et **Relations d’attributs** . Ces listes apparaissent dans leurs propres volets immédiatement sous le volet qui contient le diagramme des relations d'attributs.  
  
 **Développer toutes les formes**  
 Affiche les attributs groupés qui sont associés aux attributs de niveau supérieur. Les attributs groupés sont visibles uniquement lorsque les formes dans le diagramme des relations d'attributs sont développées.  
  
> [!NOTE]  
>  Si vous cliquez sur cette option, les formes dans le diagramme des relations d'attributs reprendront la disposition par défaut utilisée par le Concepteur de dimensions.  
  
 **Réduire toutes les formes**  
 Masque les attributs groupés qui sont associés aux attributs de niveau supérieur.  
  
> [!NOTE]  
>  Si vous cliquez sur cette option, les formes dans le diagramme des relations d'attributs reprendront la disposition par défaut utilisée par le Concepteur de dimensions.  
  
 **Zoom**  
 Affiche la liste des options de zoom disponibles.  
  
### <a name="attribute-shortcut-menu"></a>Menu contextuel attribut  
 Pour ouvrir le menu contextuel attribut, cliquez avec le bouton droit sur un attribut dans le diagramme des relations d'attributs. Le menu contextuel attribut dispose des commandes suivantes :  
  
 **Nouvelle relation d’attribut**  
 Ouvre la boîte de dialogue **Créer une relation d’attribut** dans laquelle vous pouvez définir une nouvelle relation d’attribut.  
  
 Pour plus d’informations, consultez [Boîtes de dialogue Créer une relation d’attribut et Modifier la relation d’attribut &#40;onglet Concepteur de relations d’attributs, Concepteur de dimensions&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) et [Définir des relations d’attributs](multidimensional-models/attribute-relationships-define.md).  
  
 **Propriétés**  
 Affiche les propriétés de l’attribut dans la fenêtre **Propriétés** .  
  
### <a name="relationship-shortcut-menu"></a>Menu contextuel relation  
 Pour ouvrir le menu contextuel relation, cliquez avec le bouton droit sur la flèche qui identifie la relation entre deux attributs. Le menu contextuel relation dispose des commandes suivantes :  
  
 **Modifier la relation d’attribut**  
 Ouvre la boîte de dialogue **Modifier la relation d’attribut**, dans laquelle vous pouvez modifier la relation d’attribut.  
  
 Pour plus d’informations, consultez [Boîtes de dialogue Créer une relation d’attribut et Modifier la relation d’attribut &#40;onglet Concepteur de relations d’attributs, Concepteur de dimensions&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) et [Définir des relations d’attributs](multidimensional-models/attribute-relationships-define.md).  
  
 **Type de relation**  
 Affecte la valeur **Flexible** ou **Rigide**au type de relation. Dans une relation flexible, les relations entre les membres changent dans le temps. Dans une relation rigide, les relations entre les membres ne changent pas dans le temps.  
  
 **Supprimer**  
 Supprime la relation d'attribut.  
  
 **Propriétés**  
 Affiche les propriétés de la relation dans la fenêtre **Propriétés** .  
  
## <a name="see-also"></a>Voir aussi  
 [Relations d’attributs &#40;Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md)   
 [Barre d’outils &#40;onglet Concepteur de relations d’attributs, Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md)   
 [Attributs &#40;onglet Concepteur de relations d’attributs, Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](attributes-designer-tab-dimension-designer-analysis-services-multidimensional-data.md)   
 [Relations d’attributs &#40;onglet Concepteur de relations d’attributs, Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](attribute-relationships-designer-tab-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
