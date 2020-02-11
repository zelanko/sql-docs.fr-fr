---
title: Outils de calcul (onglet calculs, concepteur de cube) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.calculationtoolspane.f1
ms.assetid: b1aa8a1a-6532-45d2-8f53-d3e211d7197a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ff0f13ec91ef1e8796ed5ebd5ccf3cc37ff2f354
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088280"
---
# <a name="calculation-tools-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a>Outils de calcul (onglet Calculs, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Utilisez le volet **Outils de calcul** de l'onglet **Calculs** accessible dans le Concepteur de cube pour explorer les métadonnées, les fonctions et les modèles disponibles en vue de leur utilisation dans les calculs.  
  
## <a name="options"></a>Options  
 **Métadonnées**  
 Affiche les métadonnées du cube sélectionné.  
  
 Faites glisser un élément sélectionné dans le volet Éditeur de script, Éditeur de formulaire de membre calculé ou Éditeur de formulaire de jeu nommé pour inclure la syntaxe MDX (Multidimensional Expressions) de cet élément à l'emplacement sélectionné dans le volet.  
  
 **Fonctions**  
 Affiche les fonctions disponibles pour les expressions et les conditions.  
  
 Faites glisser un élément sélectionné dans le volet **Éditeur de script**, **Éditeur de formulaire de membre calculé**ou **Éditeur de formulaire de jeu nommé** pour inclure la syntaxe MDX de cet élément à l'emplacement sélectionné dans le volet.  
  
> [!NOTE]  
>  En mode projet, la boîte de dialogue **Outils de calcul** lit les informations de cette option dans un fichier XML nommé MDXFunctions.xml inclus dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. En mode en ligne, les informations de cette option sont récupérées de l'ensemble de lignes du schéma MDSCHEMA_FUNCTIONS pour l'instance.  
  
 **Ceux**  
 Permet d'afficher les modèles prédéfinis disponibles aux membres calculés, aux jeux nommés et aux commandes de script.  
  
 Faites glisser un élément sélectionné dans le volet **Éditeur de script**, **Éditeur de formulaire de membre calculé**ou **Éditeur de formulaire de jeu nommé** pour inclure la syntaxe MDX de cet élément à l'emplacement sélectionné dans le volet.  
  
## <a name="context-menu"></a>Menu contextuel  
 Le menu contextuel propose les options suivantes. Vous y accédez en cliquant avec le bouton droit sur un élément du volet **Outils de calcul** :  
  
 **Copy**  
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
  
 **Ajouter un Modèle**  
 Permet d’ajouter un nouveau membre calculé, un nouveau jeu nommé ou une nouvelle commande de script sur la base du modèle sélectionné au script du cube, et d’afficher **l’Éditeur de script**, **l’Éditeur de formulaire de membre calculé**ou **l’Éditeur de formulaire de jeu nommé** selon la commande (en mode Formulaire), ou de faire défiler le contenu du volet **Éditeur de script** jusqu’à l’emplacement de la commande dans le script du cube (en mode Script).  
  
> [!NOTE]  
>  Cette option s'affiche uniquement si **Métadonnées** est sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur de cube &#40;Analysis Services-données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Toolbar &#40;onglet calculs, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Organisateur de script &#40;onglet calculs, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de formulaire de membre calculé &#40;onglet calculs, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de formulaire de jeu nommé &#40;onglet calculs, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de script &#40;onglet calculs, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)   
 [Calculs &#40;concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
