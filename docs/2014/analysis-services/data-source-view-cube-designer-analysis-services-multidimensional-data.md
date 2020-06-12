---
title: Vue de source de données (onglet structure de cube, concepteur de cube) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilder.datasourcepane.f1
ms.assetid: 1e39c910-5c10-4624-be27-ca02a461b46b
author: minewiskan
ms.author: owend
ms.openlocfilehash: a922f23cf667068ff51c315563b8fc3b35fceefe
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528989"
---
# <a name="data-source-view-cube-structure-tab-cube-designer-analysis-services---multidimensional-data"></a>Vue de source de données (onglet Structure de cube, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Le volet **Vue de source de données** permet d'afficher les tables et colonnes de la vue de source de données associée au cube sélectionné. Il sert à créer des groupes de mesures et des mesures en faisant glisser les colonnes du volet **Vue de source de données** vers le volet **Mesures** .  
  
## <a name="options"></a>Options  
 **Vue de source de données**  
 Affiche la vue de source de données associée au cube sélectionné.  
  
 **(Déplacer le point de vue)**  
 Cliquez dans le coin inférieur droit du volet, entre les barres de défilement, pour sélectionner une zone du volet **Vue de source de données** à afficher.  
  
## <a name="diagram-context-menu"></a>Menu contextuel Diagramme  
 Les options suivantes sont disponibles dans le menu contextuel qui s’affiche quand vous cliquez avec le bouton droit sur l’arrière-plan du diagramme du volet **Vue de source de données** :  
  
 **Afficher les tables**  
 Affiche la boîte de dialogue **Afficher la table**. Pour plus d’informations sur la boîte de dialogue **Afficher la table**, consultez [Boîte de dialogue Afficher la table &#40;Analysis Services – Données multidimensionnelles&#41;](show-table-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Afficher toutes les tables**  
 Affiche, dans le volet, toutes les tables incluses dans la vue de source de données associée au cube.  
  
 **Afficher seulement les tables utilisées**  
 Affiche, dans le volet, uniquement les tables utilisées par le cube et appartenant à la vue de source de données associée.  
  
 **Afficher les noms conviviaux**  
 Permet d'afficher les noms conviviaux des objets dans le volet.  
  
 **Sélectionner tout**  
 Sélectionne tous les objets se trouvant dans le volet.  
  
 **Rechercher une table**  
 Affiche la boîte de dialogue **Rechercher une table**. Pour plus d’informations sur la boîte de dialogue **Rechercher une table**, consultez [Boîte de dialogue Rechercher une table &#40;Analysis Services – Données multidimensionnelles&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Réorganiser les tables**  
 Organise les objets du volet en fonction de la disposition page spécifiée en sélectionnant **Basculer en présentation diagonale** ou **Basculer en présentation rectangulaire**.  
  
 **Basculer en présentation diagonale**  
 Sélectionnez cette option pour disposer les objets en diagonale.  
  
> [!NOTE]  
>  Cette option s’affiche seulement si **Basculer en présentation rectangulaire** est sélectionné.  
  
 **Basculer en présentation rectangulaire**  
 Sélectionnez cette option pour disposer les objets en rectangle.  
  
> [!NOTE]  
>  Cette option s’affiche seulement si **Basculer en présentation diagonale** est sélectionné.  
  
 **Modifier la vue de source de données**  
 Affiche le concepteur de vue de source de données pour la vue associée à l'objet. Pour plus d’informations sur le Concepteur de vue de source de données, consultez [Concepteur de vue de source de données &#40;Analysis Services – Données multidimensionnelles&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).  
  
 **Afficher vue de source de données dans**  
 Sélectionnez une des options suivantes pour faire passer le volet **Vue de source de données** entre les modes suivants :  
  
-   Diagramme  
  
     Affiche un diagramme des tables et colonnes associées au cube actif.  
  
-   Arborescence  
  
     Affiche une arborescence contenant les tables et colonnes associées au cube actif.  
  
 **Copier le schéma à partir de**  
 Sélectionnez l’un des diagrammes inclus dans la vue de source de données associée au cube afin de l’afficher dans le volet **Vue de source de données** .  
  
 **Zoom**  
 Sélectionnez une option de zoom disponible.  
  
 **Propriétés**  
 Affiche la fenêtre **Propriétés** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour la vue de source de données associée au cube.  
  
## <a name="table-context-menu"></a>Menu contextuel Table  
 Les options suivantes sont disponibles dans le menu contextuel qui s’affiche quand vous cliquez avec le bouton droit sur le nom d’une table ou d’une vue dans le volet **Vue de source de données** :  
  
 **Afficher les tables associées**  
 Affiche dans le volet les tables relatives à la table sélectionnée dans la vue de source de données.  
  
 **Masquer la table**  
 Supprime la table du volet.  
  
 **Explorer les données**  
 Ouvre la boîte de dialogue **Explorer les données** se rapportant à la table sélectionnée.  
  
 **Modifier la vue de source de données**  
 Affiche le Concepteur de vue de source de données de la vue qui contient la table sélectionnée. Pour plus d’informations sur le Concepteur de vue de source de données, consultez [Concepteur de vue de source de données &#40;Analysis Services – Données multidimensionnelles&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).  
  
 **Nouveau groupe de mesures à partir de la table**  
 Définit un nouveau groupe de mesures dans le volet **Mesures** en fonction de la table sélectionnée.  
  
> [!NOTE]  
>  Cette option est active uniquement si la table n’est pas encore référencée par un groupe de mesures dans le volet **Mesures** .  
  
 **Propriétés**  
 Affiche la fenêtre **Propriétés** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour la table sélectionnée.  
  
## <a name="column-context-menu"></a>Menu contextuel Colonne  
 Les options suivantes sont disponibles dans le menu contextuel qui s’affiche quand vous cliquez avec le bouton droit sur le nom d’une colonne ou d’une vue dans le volet **Vue de source de données** :  
  
 **Nouvelle mesure de la colonne**  
 Définit une nouvelle mesure dans le volet **Mesures** en fonction de la colonne sélectionnée.  
  
 **Explorer les données**  
 Affiche la boîte de dialogue **Explorer les données** pour la table contenant la colonne sélectionnée.  
  
 **Modifier la vue de source de données**  
 Affiche le Concepteur de vue de source de données de la vue qui contient la colonne sélectionnée. Pour plus d’informations sur le Concepteur de vue de source de données, consultez [Concepteur de vue de source de données &#40;Analysis Services – Données multidimensionnelles&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).  
  
 **Propriétés**  
 Affiche la fenêtre **Propriétés** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour la colonne sélectionnée.  
  
## <a name="relationship-context-menu"></a>Menu contextuel Relation  
 Les options suivantes sont disponibles dans le menu contextuel qui s’affiche quand vous cliquez avec le bouton droit sur une relation dans le volet **Vue de source de données** :  
  
 **Modifier la vue de source de données**  
 Affiche le concepteur de vue de source de données pour la vue qui contient la relation sélectionnée. Pour plus d’informations sur le Concepteur de vue de source de données, consultez [Concepteur de vue de source de données &#40;Analysis Services – Données multidimensionnelles&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).  
  
 **Propriétés**  
 Affiche la fenêtre **Propriétés** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour la relation sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Barre d’outils &#40;onglet structure de cube, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](toolbar-cube-structure-cube-designer-analysis-services-multidimensional-data.md)   
 [Mesures &#40;onglet structure de cube, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](measures-cube-structure-cube-designer-analysis-services-multidimensional-data.md)   
 [Dimensions &#40;onglet structure de cube, concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](dimensions-cube-structure-cube-designer-analysis-services-multidimensional-data.md)   
 [Structure de cube &#40;concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md)  
  
  
