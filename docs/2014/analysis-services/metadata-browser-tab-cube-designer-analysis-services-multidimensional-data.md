---
title: Métadonnées (onglet navigateur, Concepteur de Cube) (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.metadatapane.f1
ms.assetid: a1ace545-488d-4645-8330-56408a5e8abd
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a3d3c2c707e42204fe3ae3eb75ea90b28525f2b1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241689"
---
# <a name="metadata-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Métadonnées (onglet Explorateur, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Utilisez le volet **Métadonnées** de l’onglet **Navigateur** dans le Concepteur de cube pour parcourir la structure du cube, afficher les mesures associées et afficher et créer des dimensions. Vous pouvez explorer les hiérarchies, afficher la liste des mesures et des indicateurs de performance clés disponibles et copier les noms complets des objets.  
  
 Vous pouvez également faire glisser les objets et les hiérarchies du volet **Métadonnées** vers la zone de génération des requêtes pour créer des requêtes ou exporter des données pour les parcourir dans Excel.  
  
## <a name="options"></a>Options  
 **Métadonnées**  
 Affiche les métadonnées disponibles dans la vue actuelle. Vous pouvez modifier la vue (autrement dit, la perspective ou le cube sélectionné) en cliquant sur l’icône du cube, puis en utilisant la boîte de dialogue **Sélection de cube** pour choisir un nouveau cube ou une nouvelle perspective. Vous pouvez également cliquer sur **Groupe de mesures**, puis sélectionner un nouveau groupe de mesures dans la liste déroulante pour filtrer les objets qui sont disponibles dans le volet **Métadonnées** .  
  
 Faites glisser les éléments sélectionnés sur la zone du filtre, des données, des lignes ou des colonnes du contrôle [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 11.0 PivotTable dans le volet **Rapport** afin d’afficher les données de l’élément sélectionné.  
  
 **Fonctions**  
 Affiche la liste de toutes les fonctions, de tous les opérateurs et de toutes les constantes qui peuvent être utilisés pour créer des requêtes ou des vues de données dans le **Navigateur**. Pour utiliser une fonction, recherchez celle de votre choix, puis faites-la glisser dans la zone de requête. La définition de la syntaxe est ajoutée au texte.  
  
> [!WARNING]  
>  La liste **Fonction** est disponible quand vous travaillez en mode de création graphique.  
  
 Lorsque vous utilisez un modèle tabulaire, la liste des fonctions inclut les fonctions MDX et les fonctions DAX. Sinon, la liste inclut uniquement MDX. Un modèle multidimensionnel ne peut pas utiliser les fonctions DAX directement, bien qu'une expression DAX puisse être incluse dans le cadre d'une définition d'objet.  
  
 Conseil : les dossiers qui contiennent des fonctions DAX sont répertoriés en lettres majuscules. Tous les autres dossiers contiennent des fonctions MDX. Par exemple, il existe deux dossiers pour les fonctions statistiques : **STATISTICAL** contient les fonctions DAX connexes.  
  
## <a name="context-menu"></a>Menu contextuel  
 Les options suivantes sont disponibles dans le menu contextuel qui s’affiche quand vous cliquez avec le bouton droit sur un élément se trouvant dans le volet **Métadonnées** :  
  
|Option|Description|  
|------------|-----------------|  
|**Ajouter à la requête**|Cliquez pour ajouter l'objet sélectionné dans le volet inférieur de la zone de génération de la requête.|  
|**Ajouter au filtre**|Permet d’ajouter la dimension, l’attribut, la hiérarchie ou le niveau sélectionné à la zone de filtre du **Navigateur**.<br /><br /> Remarque : cette option n’est active que si une dimension, un attribut, une hiérarchie ou un niveau est sélectionné.|  
|**Copier**|Permet d'ajouter l'élément sélectionné dans le Presse-papiers.<br /><br /> Remarque : cette option copie le nom complet de l’objet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Barre d’outils &#40;onglet navigateur, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Analyser dans Excel &#40;onglet navigateur, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Interroger et filtrer &#40;onglet navigateur, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Navigateur &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
