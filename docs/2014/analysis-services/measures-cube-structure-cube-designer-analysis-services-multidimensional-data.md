---
title: Mesures (onglet structure de cube, concepteur de cube) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilder.measurespane.f1
ms.assetid: be70f63b-58f2-4eff-81bc-c86d8229e617
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cbd64cd4eb3ca686fdbdd1a59c9e84fa387e6a7f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66077921"
---
# <a name="measures-cube-structure-tab-cube-designer-analysis-services---multidimensional-data"></a>Mesures (onglet Structure de cube, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Utilisez le volet **Mesures** pour manipuler des groupes de mesures et des membres de l'onglet **Structure de cube** le Concepteur de cube.  
  
## <a name="options"></a>Options  
 mesures  
 Affiche les groupes de mesures et les mesures figurant dans le cube en fonction de la vue sélectionnée :  
  
 Arborescence  
 Affiche une arborescence des groupes de mesure, les mesures étant des nœuds enfants.  
  
 Développez les groupes de mesures pour afficher les mesures. Cliquez sur un groupe de mesures ou une mesure sélectionné pour renommer respectivement le groupe ou la mesure.  
  
 Grille  
 Affiche un tableau des mesures et de leurs propriétés les plus souvent sollicitées. Cliquez sur **Ajouter une nouvelle mesure** pour afficher la boîte de dialogue **Nouvelle mesure** et ajouter une nouvelle mesure au tableau.  
  
 Cette grille comporte les colonnes suivantes :  
  
 Measure  
 Tapez le nom de la mesure.  
  
 Groupe de mesures  
 Affiche le groupe qui contient la mesure.  
  
 Type de données  
 Sélectionnez le type de données de la mesure.  
  
 Agrégation  
 Sélectionnez le type d'agrégation de la mesure.  
  
## <a name="context-menu"></a>Menu contextuel  
 Le menu contextuel propose les options suivantes. Vous y accédez en cliquant avec le bouton droit dans le volet **Mesures** :  
  
 **Nouvelle mesure**  
 Sélectionnez cette option pour afficher la boîte de dialogue **Nouvelle mesure** et ajouter une nouvelle mesure au groupe actuellement sélectionné dans le volet **Mesures** .  
  
 **Nouveau groupe de mesures**  
 Sélectionnez cette option pour afficher la boîte de dialogue **Nouveau groupe de mesures** et ajouter un nouveau groupe dans le volet **Mesures** .  
  
 **Afficher les mesures dans**  
 Sélectionnez cette option pour parcourir les options suivantes ou en sélectionner une et modifier l’affichage du volet **Mesures** :  
  
|Option|Définition|  
|------------|----------------|  
|**Arbres**|Affiche les groupes et les mesures sous forme d'arborescence.|  
|**Grille**|Affiche les groupes et les mesures sous forme de tableau.|  
  
 **Renommer**  
 Sélectionnez cette option pour renommer la mesure ou le groupe de mesures sélectionné.  
  
 **Supprimer**  
 Sélectionnez cette option pour afficher la boîte de dialogue **Supprimer les objets** et supprimer les objets sélectionnés dans le volet **Mesures** .  
  
 **Monter**  
 Sélectionnez cette option pour remonter d'un échelon la mesure ou le groupe de mesures sélectionné.  
  
> [!NOTE]  
>  Cette option est désactivée s'il n'est pas possible de déplacer vers le haut l'élément sélectionné.  
  
 **Descendre**  
 Sélectionnez cette option pour faire descendre d'un échelon la mesure ou le groupe de mesures sélectionné.  
  
> [!NOTE]  
>  Cette option est désactivée s'il n'est pas possible de déplacer vers le bas l'élément sélectionné.  
  
 **Nouvel objet lié**  
 Cliquez pour afficher l' **Assistant Objet lié** et lier les groupes de mesures et les dimensions d'autres cubes et importer des actions, des indicateurs de performance clés (KPI) et des calculs dans le cube sélectionné.  
  
 **Propriétés**  
 Sélectionnez cette option pour afficher la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour la mesure ou le groupe de mesures sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés de mesure](multidimensional-models/configure-measure-properties.md)   
 [Mesures et groupes de mesures](multidimensional-models/measures-and-measure-groups.md)  
  
  
