---
title: Vue de source de données (onglet structure de dimension, concepteur de dimensions) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.datasourcepane.f1
ms.assetid: c4bd3c5e-8986-448f-b9db-3551f50f0696
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 38d61436f6245024dcc477d39b7b2589234658ee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66082345"
---
# <a name="data-source-view-dimension-structure-tab-dimension-designer-analysis-services---multidimensional-data"></a>Vue de source de données (onglet Structure de dimension, Concepteur de dimensions) (Analysis Services - Données multidimensionnelles)
  Utilisez le volet **Vue de source de données** pour afficher les tables et les colonnes associées à la dimension sélectionnée. Ce volet sert à créer des attributs, des propriétés de membres, des hiérarchies et des niveaux. Pour cela, faites glisser des colonnes du volet **Vue de source de données** dans le volet **Attributs** ou **Hiérarchies et niveaux** .  
  
## <a name="options"></a>Options  
 **Vue de source de données**  
 Affiche la vue de source de données associée à la dimension sélectionnée.  
  
 **(Déplacer le point de vue)**  
 Cliquez dans le coin inférieur droit du volet, entre les barres de défilement, pour sélectionner une zone du volet **Vue de source de données** à afficher.  
  
## <a name="diagram-context-menu"></a>Menu contextuel Diagramme  
 Les options répertoriées dans le tableau suivant sont disponibles dans le menu contextuel qui s’affiche en cliquant avec le bouton droit sur l’arrière-plan du schéma du volet **Vue de source de données** .  
  
 **Afficher les tables**  
 Affiche la boîte de dialogue **Afficher la table**. Pour plus d’informations sur la boîte de dialogue **Afficher la table**, consultez [Boîte de dialogue Afficher la table &#40;Analysis Services – Données multidimensionnelles&#41;](show-table-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Afficher toutes les tables**  
 Affiche dans le volet toutes les tables figurant dans la vue de source de données associées à la dimension.  
  
 **Afficher seulement les tables utilisées**  
 Affiche dans le volet toutes les tables utilisées par la dimension à partir de la vue de source de données associée.  
  
 **Afficher les noms conviviaux**  
 Sélectionnez cette option pour afficher les noms conviviaux des objets du volet.  
  
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
 Affiche le **Concepteur de vue de source de données** pour la vue de source de données associée à la dimension. Pour plus d’informations sur le **Concepteur de vue de source de données**, consultez [Concepteur de vue de source de données &#40;Analysis Services – Données multidimensionnelles&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).  
  
 **Afficher vue de source de données dans**  
 Sélectionnez une des options suivantes pour faire passer le volet **Vue de source de données** entre les modes suivants :  
  
-   Diagramme  
  
     Affiche un diagramme des tables et des colonnes associées à la dimension active.  
  
-   Arborescence  
  
     Affiche une arborescence des tables et des colonnes associées à la dimension active.  
  
 **Copier le schéma à partir de**  
 Sélectionnez un des diagrammes de la vue de source de données associée à la dimension pour l’afficher dans le volet **Vue de source de données** .  
  
 **Zoom**  
 Sélectionnez une option de zoom disponible.  
  
 **Propriétés**  
 Affiche la fenêtre **Propriétés** dans **SQL Server Data Tools** pour la vue de source de données associée à la dimension.  
  
## <a name="table-context-menu"></a>Menu contextuel Table  
 Les options répertoriées dans le tableau suivant sont disponibles dans le menu contextuel qui s’affiche en cliquant le bouton droit sur le nom d’une table ou d’une vue dans le volet **Vue de source de données** .  
  
 **Afficher les tables associées**  
 Affiche dans le volet les tables relatives à la table sélectionnée dans la vue de source de données.  
  
 **Masquer la table**  
 Supprime la table du volet.  
  
 **Explorer les données**  
 Ouvre la boîte de dialogue **Explorer les données** pour la table sélectionnée.  
  
 **Modifier la vue de source de données**  
 Affiche le **Concepteur de vue de source** de données pour la vue de source de données qui contient la table sélectionnée. Pour plus d’informations sur le **Concepteur de vue de source de données**, consultez [Concepteur de vue de source de données &#40;Analysis Services – Données multidimensionnelles&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).  
  
 **Propriétés**  
 Affiche la fenêtre **Propriétés** dans **SQL Server Data Tools** pour la table sélectionnée.  
  
## <a name="column-context-menu"></a>Menu contextuel Colonne  
 Les options répertoriées dans le tableau suivant sont disponibles dans le menu contextuel qui s’affiche en cliquant avec le bouton droit sur le nom de la colonne d’une table ou d’une vue dans le volet **Vue de source de données** .  
  
 **Nouvel attribut de colonne**  
 Affiche dans le volet les tables relatives à la table sélectionnée dans la vue de source de données.  
  
 **Explorer les données**  
 Affiche la boîte de dialogue **Explorer les données** pour la table contenant la colonne sélectionnée.  
  
 **Modifier la vue de source de données**  
 Affiche le **Concepteur de vue de source** de données pour la vue de source de données qui contient la colonne sélectionnée. Pour plus d’informations sur le **Concepteur de vue de source de données**, consultez [Concepteur de vue de source de données &#40;Analysis Services – Données multidimensionnelles&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).  
  
 **Propriétés**  
 Affiche la fenêtre **Propriétés** dans **SQL Server Data Tools** pour la colonne sélectionnée.  
  
## <a name="relationship-context-menu"></a>Menu contextuel Relation  
 Les options répertoriées dans le tableau suivant sont disponibles dans le menu contextuel qui s’affiche en cliquant avec le bouton droit sur une relation dans le volet **Vue de source de données** .  
  
 **Modifier la vue de source de données**  
 Affiche le **Concepteur de vue de source** de données pour la vue de source de données qui contient la relation sélectionnée. Pour plus d’informations sur le **Concepteur de vue de source de données**, consultez [Concepteur de vue de source de données &#40;Analysis Services – Données multidimensionnelles&#41;](data-source-view-designer-analysis-services-multidimensional-data.md).  
  
 **Propriétés**  
 Affiche la fenêtre **Propriétés** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour la relation sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Structure de dimension &#40;concepteur de dimensions&#41; &#40;Analysis Services-données multidimensionnelles&#41;](dimension-structure-dimension-designer-analysis-services-multidimensional-data.md)   
 [Barre d’outils &#40;onglet structure de dimension, concepteur de dimensions&#41; &#40;Analysis Services-données multidimensionnelles&#41;](toolbar-dimension-structure-designer-analysis-services-multidimensional-data.md)   
 [Attributs &#40;onglet structure de dimension, concepteur de dimensions&#41; &#40;Analysis Services-données multidimensionnelles&#41;](attributes-dimension-designer-analysis-services-multidimensional-data.md)   
 [Hiérarchies &#40;onglet structure de dimension, concepteur de dimensions&#41; &#40;Analysis Services-données multidimensionnelles&#41;](hierarchies-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
