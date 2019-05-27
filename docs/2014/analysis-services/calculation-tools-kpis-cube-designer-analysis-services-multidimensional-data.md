---
title: Outils de calcul (onglet des indicateurs de performance clés, Concepteur de Cube) (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpisview.calculationtoolspane.f1
ms.assetid: c030c725-7763-4c23-9988-4b274a88fc31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecd16965c81ccb091d70320bd91c56112d3c15a0
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66088271"
---
# <a name="calculation-tools-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a>Outils de calcul (onglet Indicateurs de performance clés, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Utilisez le volet **Outils de calcul** de l’onglet **Indicateurs de performance clés** du Concepteur de cube pour explorer les métadonnées, les fonctions et les modèles disponibles dans les indicateurs de performance clés (KPI).  
  
> [!NOTE]  
>  Ce volet s'affiche uniquement en mode Formulaire.  
  
## <a name="options"></a>Options  
 **Métadonnées**  
 Affiche les métadonnées du cube sélectionné.  
  
 Faites glisser un élément sélectionné dans le volet **Éditeur de formulaire d’indicateur de performance clé** pour inclure la syntaxe des expressions multidimensionnelles (MDX) de cet élément à l’emplacement sélectionné dans le volet.  
  
 **Fonctions**  
 Affiche les fonctions disponibles pour les expressions et les conditions.  
  
 Faites glisser un élément sélectionné dans le volet **Éditeur de formulaire d'indicateur de performance clé** pour inclure la syntaxe MDX de cet élément à l'emplacement sélectionné dans le volet.  
  
> [!NOTE]  
>  En mode projet, la boîte de dialogue **Outils de calcul** lit les informations de cette option dans un fichier XML nommé MDXFunctions.xml inclus dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. En mode en ligne, les informations de cette option sont récupérées de l'ensemble de lignes du schéma MDSCHEMA_FUNCTIONS pour l'instance.  
  
 **Modèles**  
 Affiche les modèles prédéfinis disponibles pour les indicateurs de performance clés (KPI).  
  
 Faites glisser un élément sélectionné dans le volet **Éditeur de formulaire d'indicateur de performance clé** pour inclure la syntaxe MDX de cet élément à l'emplacement sélectionné dans le volet.  
  
## <a name="context-menu"></a>Menu contextuel  
 Le menu contextuel propose les options suivantes. Vous y accédez en cliquant avec le bouton droit sur un élément du volet **Outils de calcul** :  
  
 **Copier**  
 Sélectionnez cette option pour copier l'élément sélectionné dans **Métadonnées** ou **Fonctions** dans le Presse-papiers.  
  
> [!NOTE]  
>  Cette option ne s'affiche pas si **Modèles** est sélectionné.  
  
> [!NOTE]  
>  Cette option est désactivée s'il n'est pas possible de copier le membre sélectionné (ex. le dossier **Ensembles** d'une dimension affichée dans **Métadonnées** ou le dossier de groupe de fonctions affiché dans **Fonctions**).  
  
 **Filtrer les membres**  
 Sélectionnez cette option pour afficher la boîte de dialogue **Filtrer les membres** et filtrer les membres affichés pour l'élément sélectionné dans **Métadonnées**. Pour plus d’informations sur la boîte de dialogue **Filtrer les membres**, consultez [Boîte de dialogue Filtrer les membres &#40;Analysis Services - Données multidimensionnelles&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).  
  
> [!NOTE]  
>  Cette option s'affiche uniquement si **Métadonnées** est sélectionné.  
  
> [!NOTE]  
>  Cette option est activée uniquement si le niveau d'un attribut est sélectionné dans **Métadonnées**.  
  
 **Ajouter un modèle**  
 Sélectionnez un nouveau membre calculé, un ensemble nommé ou un script de commandes d’après le modèle sélectionné vers le script du cube et affichez l’ **Éditeur de formulaire d’indicateur de performance clé** en mode formulaire.  
  
> [!NOTE]  
>  Cette option s'affiche uniquement si **Métadonnées** est sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur de cube &#40;Analysis Services - données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Indicateurs de performance clés &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md)   
 [Barre d’outils &#40;onglet des indicateurs de performance clés, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](toolbar-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Organisateur d’indicateur de performance clé &#40;onglet des indicateurs de performance clés, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](kpi-organizer-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de formulaire d’indicateur de performance clé &#40;onglet des indicateurs de performance clés, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](kpi-form-editor-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Navigateur d’indicateur de performance clé &#40;onglet des indicateurs de performance clés, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](kpi-browser-kpis-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
