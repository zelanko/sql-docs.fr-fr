---
title: Niveau et membres (onglet navigateur, concepteur de dimensions) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.browsertab.levelsandmembers.f1
ms.assetid: 3f61e384-5b4e-4480-a7ed-b408de2fdea7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ad602710cab83e2be25a03a4da6cce0c3407493e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078109"
---
# <a name="level-and-members-browser-tab-dimension-designer-analysis-services---multidimensional-data"></a>Niveau et membres (onglet Navigateur, Concepteur de dimensions) (Analysis Services - Données multidimensionnelles)
  Utilisez ce volet pour parcourir les membres correspondant à la hiérarchie et à la langue sélectionnée. Pour sélectionner une hiérarchie ou une langue à consulter, utilisez les options **Hiérarchie** et **Langue** du volet **Barre d'outils** . Pour plus d’informations sur le volet Barre d’outils, consultez [Toolbar &#40;Browser Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md).  
  
## <a name="writeback-mode"></a>Mode Écriture différée  
 La fonctionnalité de ce volet change si vous activez le mode d'écriture différé. L'écriture doit être activée sur la dimension sélectionnée (en d'autres termes, la propriété `WriteEnabled` de la dimension doit être affectée de la valeur true) et la dimension doit être déployée sur une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour pouvoir activer le mode d'écriture différée.  
  
 Pour activer le mode d’écriture différée, vous pouvez sélectionner **Écriture différée** dans le volet **Barre d’outils** ou cliquer avec le bouton droit sur le volet **Niveau et membres** et sélectionner **Écriture différée** dans le menu contextuel.  
  
 Si le mode d'écriture différée est activé, vous pouvez exécuter les actions supplémentaires suivantes dans le volet **Niveau et membres** :  
  
|Opération|Action|  
|-----------|-------------|  
|Créer des membres frères et enfants dans la hiérarchie sélectionnée|Cliquez avec le bouton droit sur le membre sélectionné et sélectionnez **Créer frères**pour créer un membre frère, ou sur **Créer enfant**pour créer un membre enfant à partir du menu contextuel.|  
|Remonter ou descendre un membre sélectionné dans la hiérarchie|Faites glisser le membre sélectionné vers le membre parent ou enfant approprié, ou cliquez sur **Augmenter le retrait** ou sur **Réduire le retrait** dans le volet **Barre d'outils** pour monter ou descendre le membre sélectionné dans les niveaux de la hiérarchie.|  
|Renommer un membre sélectionné|Cliquez avec le bouton droit sur le membre sélectionné et sélectionnez **Renommer**ou cliquez sur un membre déjà sélectionné.|  
|Modifier les valeurs des propriétés du membre|Double-cliquez sur la valeur dans la propriété du membre sélectionné pour modifier la valeur.|  
  
## <a name="options"></a>Options  
 **Niveau actuel**  
 Affiche le niveau auquel appartient le membre sélectionné dans **Arborescence** .  
  
 **Arbres**  
 Affiche les membres correspondant à la hiérarchie et à la langue sélectionnées.  
  
 Si les propriétés du membre sont sélectionnées depuis l'option **Propriétés de membre** du volet Barre d'outils, chaque propriété du membre s'affiche dans une colonne.  
  
 Si le mode d'écriture différée est activé, une colonne s'affiche pour chaque colonne clé associée à l'attribut de clé dans la dimension.  
  
## <a name="context-menu"></a>Menu contextuel  
 Les options suivantes sont disponibles dans le menu contextuel qui s’affiche en cliquant avec le bouton droit sur n’importe quelle partie du volet **Niveau et membres** du membre sélectionné :  
  
 **Créer frères**  
 Crée un membre au même niveau que le membre sélectionné.  
  
> [!NOTE]  
>  Cette option est activée uniquement si un membre est sélectionné dans un niveau autre que le niveau (Tout).  
  
> [!NOTE]  
>  Cette option n'est disponible que si le mode d'écriture différée est activé.  
  
 **Créer enfant**  
 Crée un membre enfant dans le niveau inférieur suivant du membre sélectionné.  
  
> [!NOTE]  
>  Cette option est activée uniquement si un membre est sélectionné dans un niveau autre que le niveau le plus bas.  
  
> [!NOTE]  
>  Cette option n'est disponible que si le mode d'écriture différée est activé.  
  
 **Couper**  
 Copie les membres sélectionnés vers le Presse-papiers et les supprime de la hiérarchie.  
  
> [!NOTE]  
>  Cette option est activée uniquement si un membre est sélectionné dans un niveau autre que le membre Tout.  
  
> [!NOTE]  
>  Cette option n'est disponible que si le mode d'écriture différée est activé.  
  
 **Coller**  
 Colle les membres supprimés avec **Couper** , immédiatement après le membre sélectionné.  
  
> [!NOTE]  
>  Cette option n'est disponible que si le mode d'écriture différée est activé.  
  
 **Supprimer**  
 Supprime les membres sélectionnés de la hiérarchie.  
  
> [!NOTE]  
>  Cette option est activée uniquement si un membre est sélectionné dans un niveau autre que le membre Tout.  
  
> [!NOTE]  
>  Cette option n'est disponible que si le mode d'écriture différée est activé.  
  
 **Renommer**  
 Sélectionnez cette option pour modifier le nom du membre sélectionné.  
  
> [!NOTE]  
>  Cette option est activée uniquement si un membre est sélectionné dans un niveau autre que le membre Tout.  
  
> [!NOTE]  
>  Cette option n'est disponible que si le mode d'écriture différée est activé.  
  
 **Filtrer les membres**  
 Affiche la boîte de dialogue **Filtrer les membres** pour filtrer les membres figurant dans **Niveau et membres** pour la hiérarchie sélectionnée. Pour plus d’informations sur la boîte de dialogue **Filtrer les membres**, consultez [Boîte de dialogue Filtrer les membres &#40;Analysis Services - Données multidimensionnelles&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Développer tout**  
 Développe tous les membres dans **Arborescence**.  
  
> [!NOTE]  
>  Cette option est activée uniquement si un membre est sélectionné dans un niveau autre que le niveau le plus bas.  
  
 **Réduire tout**  
 Réduit tous les membres dans **Arborescence**.  
  
 **Développer le membre**  
 Développe le membre sélectionné dans **Arborescence**.  
  
 **Réduire le membre**  
 Réduit le membre sélectionné dans **Arborescence**.  
  
 **Transcription**  
 Sélectionnez cette option pour activer le mode d'écriture différée.  
  
## <a name="see-also"></a>Voir aussi  
 [Barre d’outils &#40;onglet navigateur, concepteur de dimensions&#41; &#40;Analysis Services-données multidimensionnelles&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md)   
 [Navigateur &#40;concepteur de dimensions&#41; &#40;Analysis Services-données multidimensionnelles&#41;](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
