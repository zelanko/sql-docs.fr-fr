---
title: Boîte de dialogue définir une relation (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.f1
helpviewer_keywords:
- Define Relationship dialog box
ms.assetid: 0fcee7f1-f138-4c2e-ae8c-245395ee0fe8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d80be1c4898ae00dfdbb88e22771c071636cf73c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66082099"
---
# <a name="define-relationship-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Définir une relation (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Définir une relation** pour définir une relation entre une dimension de cube et un groupe de mesures dans le Concepteur de cube. Pour afficher la boîte de dialogue **Définir une relation** , dans le Concepteur de cube, sous l’onglet **Utilisation de la dimension** , cliquez sur **...** dans une cellule dans le volet **Grille** .  
  
## <a name="options"></a>Options  
 **Sélectionnez un type de relation**  
 Sélectionnez le type de relation de dimension à créer entre la dimension de cube et le groupe de mesures. Cette action modifie le contenu du volet **Détail** .  
  
 Si vous sélectionnez l'option **Aucune relation** , aucune relation de dimension n'est créée.  
  
 **Detail**  
 Affiche les options disponibles pour le type de relation de dimension sélectionné dans **Sélectionnez un type de relation**.  
  
## <a name="detail-pane-options"></a>Options du volet d'informations  
 Les options suivantes apparaissent dans le volet **Détail** , selon le type de relation sélectionné dans **Sélectionnez un type de relation**:  
  
|Type de relation|Description|Option|  
|-----------------------|-----------------|------------|  
|**Aucune relation**|Aucune relation n'est définie et aucune option ne s'affiche dans le volet **Détail** .||  
|**Normal**|Spécifie une relation de dimension régulière. Les options suivantes s'affichent dans le volet **Détail** :|**Attribut de granularité** : <br />                      Sélectionnez l'attribut qui définit la granularité du groupe de mesures par rapport à la dimension. Cet attribut est généralement l'attribut clé de la dimension.|  
|||**Table de dimension** : affiche la table principale de la dimension.|  
|||**Table de groupe de mesures** : affiche la table de faits du groupe de mesures.|  
|||**Relation**: affiche une grille de colonnes de dimension et de colonnes de groupe de mesures dont dépend la relation. Cette grille comporte les colonnes suivantes :<br /><br /> **Colonnes de dimension** : affiche les colonnes associées à l’attribut de granularité sélectionné. Remarque : si la dimension n’a pas encore été générée, cette option est définie sur la valeur **Générer**.<br />**Colonnes de groupe de mesures** :<br />                              Sélectionnez les colonnes dans le groupe de mesures qui sont associées aux colonnes de dimension.|  
|||**Avancé** :<br />                      Cliquez sur ce bouton pour afficher la boîte de dialogue **Liaisons des groupes de mesures** et modifier les propriétés avancées, notamment le traitement NULL, sur les relations entre les attributs et les colonnes des groupes de mesures. Pour plus d’informations sur la boîte de dialogue **Liaisons des groupes de mesures**, consultez [Boîte de dialogue Liaisons des groupes de mesures &#40;Analysis Services - Données multidimensionnelles&#41;](measure-group-bindings-dialog-box-analysis-services-multidimensional-data.md).|  
|**Cela**|Spécifie une relation de dimension de faits. Les options suivantes s'affichent dans le volet **Détail** :|**Attribut de granularité** : sélectionnez l’attribut qui définit la granularité du groupe de mesures par rapport à la dimension. Cet attribut est généralement l'attribut clé de la dimension.|  
|||**Table de dimension** : affiche la table de dimension principale.|  
|||**Table de groupe de mesures**: <br />                      Affiche la table dont dépend le groupe de mesures.|  
|**Référencé**|Spécifie une relation de dimension référencée. Les options suivantes s'affichent dans le volet **Détail** :|**Dimension de référence**: <br />                      Affiche la dimension sélectionnée.|  
|||**Dimension intermédiaire** : <br />                      Sélectionnez la dimension intermédiaire.|  
|||**Attribut de dimension de référence**: <br />                      Sélectionnez l’attribut dans la dimension de référence qui est associé à l’attribut de dimension intermédiaire spécifié dans **Attribut de dimension intermédiaire**.|  
|||**Attribut de dimension intermédiaire**: <br />                      Sélectionnez l’attribut dans la dimension intermédiaire qui est associé à l’attribut de dimension de référence spécifié dans **Dimension de référence**.|  
|||**Matérialiser**: <br />                      Sélectionnez cette option pour stocker le membre d'attribut dans la dimension intermédiaire qui lie l'attribut dans la dimension de référence à la table de faits dans la structure MOLAP. La matérialisation des relations est un comportement par défaut qui permet d'optimiser les performances des requêtes, au détriment toutefois de la durée de traitement et de l'espace de stockage.|  
|**Plusieurs-à-plusieurs**|Spécifie une relation de dimension plusieurs à plusieurs. Les options suivantes s'affichent dans le volet **Détail** :|**Dimension** : affiche la dimension sélectionnée.|  
|||**Groupe de mesures intermédiaire** : <br />                      Sélectionnez le groupe de mesures intermédiaire correspondant.<br /><br /> Remarque : le groupe de mesures intermédiaire doit contenir au moins une dimension commune au groupe de mesures sélectionné. En outre, la granularité de la relation entre le groupe de mesures intermédiaire et la dimension commune doit être supérieure ou égale à la granularité entre la dimension commune et le groupe de mesures sélectionné.|  
|**Exploration de données**|Spécifie une relation de dimension d'exploration de données. Les options suivantes s'affichent dans le volet **Détail** :|**Dimension cible**: affiche la dimension d’exploration de données sélectionnée.<br /><br /> Remarque : vous devez sélectionner une dimension d’exploration de données pour créer une relation correspondante.|  
|||**Dimension source** : sélectionnez la dimension sur laquelle la dimension d’exploration de données fournit une analyse prédictive.|  
  
## <a name="see-also"></a>Voir aussi  
 [Relations de dimension](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Utilisation de la dimension &#40;le concepteur de cube&#41; &#40;Analysis Services-données multidimensionnelles&#41;](dimension-usage-cube-designer-analysis-services-multidimensional-data.md)   
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
