---
title: Outils de calcul (onglet Actions, Concepteur de Cube) (Analysis Services - données multidimensionnelles) | Documents Microsoft
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
- sql12.asvs.cubeeditor.actionsview.calculationtoolspane.f1
ms.assetid: a3370370-43cd-4cc2-bb9f-c0d988b96f05
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2a0fe659397a801fa69c2bb4ce2e26d7e087f9b5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143389"
---
# <a name="calculation-tools-actions-tab-cube-designer-analysis-services---multidimensional-data"></a>Outils de calcul (onglet Actions, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Utilisez le volet **Outils de calcul** sur l'onglet **Actions** du Concepteur de cube afin d'explorer les métadonnées, les fonctions et les modèles disponibles en vue de leur utilisation dans des actions, des actions d'extraction et des actions du rapport.  
  
## <a name="options"></a>Options  
 **Métadonnées**  
 Affiche les métadonnées du cube sélectionné.  
  
 Faites glisser un élément sélectionné dans le volet **Éditeur de formulaire d’action**, **Éditeur de formulaire d’action d’extraction**ou **Éditeur de formulaire d’action du rapport** pour inclure la syntaxe MDX (Multidimensional Expressions) de cet élément à l’emplacement sélectionné dans le volet.  
  
 **Fonctions**  
 Affiche les fonctions disponibles pour les expressions et les conditions.  
  
 Faites glisser un élément sélectionné dans le volet **Éditeur de formulaire d'action**, **Éditeur de formulaire d'action d'extraction**ou **Éditeur de formulaire d'action de rapport** pour inclure la syntaxe MDX de cet élément à l'emplacement sélectionné dans le volet.  
  
> [!NOTE]  
>  En mode projet, la boîte de dialogue **Outils de calcul** lit les informations de cette option dans un fichier XML nommé MDXFunctions.xml inclus dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. En mode en ligne, les informations de cette option sont récupérées de l'ensemble de lignes du schéma MDSCHEMA_FUNCTIONS pour l'instance.  
  
 **Modèles**  
 Permet d'afficher les modèles prédéfinis disponibles relatifs aux actions.  
  
 Faites glisser un élément sélectionné dans le volet **Éditeur de formulaire d'action**, **Éditeur de formulaire d'action d'extraction**ou **Éditeur de formulaire d'action de rapport** pour inclure la syntaxe MDX de cet élément à l'emplacement sélectionné dans le volet.  
  
## <a name="context-menu"></a>Menu contextuel  
 Le menu contextuel propose les options suivantes. Vous y accédez en cliquant avec le bouton droit sur un élément du volet **Outils de calcul** :  
  
|Option|Définition|  
|------------|----------------|  
|**Copier**|Sélectionnez cette option pour copier l'élément sélectionné dans **Métadonnées** ou **Fonctions** dans le Presse-papiers.<br /><br /> Notez que cette option ne s’affiche pas si **modèles** est sélectionnée. Notez également que cette option est désactivée si le membre sélectionné ne peut pas être copié, telles que la **jeux** dossier d’une dimension affichée dans **métadonnées** ou le dossier du groupe de fonctions affiché dans (fonction) **Fonctions**.|  
|**Filtrer les membres**|Sélectionnez cette option pour afficher la boîte de dialogue **Filtrer les membres** et filtrer les membres affichés pour l'élément sélectionné dans **Métadonnées**. Pour plus d’informations sur la boîte de dialogue **Filtrer les membres**, consultez [Boîte de dialogue Filtrer les membres &#40;Analysis Services - Données multidimensionnelles&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Notez que cette option s’affiche uniquement si **métadonnées** est sélectionnée. Notez également que cette option est activée uniquement si un niveau d’un attribut est sélectionné dans **métadonnées**.|  
|**Ajouter un modèle**|Permet d'ajouter au cube une nouvelle action, action d'extraction ou action de rapport s'appuyant sur le modèle sélectionné et d'afficher, selon le type d'action, l' **Éditeur de formulaire d'action**, l' **Éditeur de formulaire d'action d'extraction**ou l' **Éditeur de formulaire d'action de rapport**.<br /><br /> Remarque : Cette option s’affiche uniquement si **métadonnées** est sélectionnée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Notions de base des scripts MDX &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Actions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Barre d’outils &#40;sous l’onglet Actions, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Organisateur d’action &#40;sous l’onglet Actions, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de formulaire d’action &#40;sous l’onglet Actions, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de formulaire d’Action d’extraction &#40;sous l’onglet Actions, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de formulaire d’Action de rapport &#40;sous l’onglet Actions, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  