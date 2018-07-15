---
title: Sélectionnez les attributs de Dimension (Assistant Dimension) | Microsoft Docs
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
- sql12.asvs.dimensionwizard.dimensionattributes.f1
ms.assetid: f58a3e14-ab27-44d3-8c26-f5c9ee7583b0
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 08e54b933094b86c68af60277ff73b701bb5e4f6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263445"
---
# <a name="select-dimension-attributes-dimension-wizard"></a>Sélectionner les attributs de la dimension (Assistant Dimension)
  Utilisez la page **Sélectionner les attributs de la dimension** pour sélectionner et modifier les attributs de la dimension à créer.  
  
> [!NOTE]  
>  Si vous avez des difficultés à lire les valeurs d'une colonne, agrandissez la fenêtre de l'Assistant et modifiez la largeur de chaque en-tête de colonne jusqu'à ce que les valeurs soient lisibles.  
  
 **Pour ouvrir l’Assistant Dimension**  
  
-   Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **Dimensions** pour un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis cliquez sur **Nouvelle dimension**.  
  
## <a name="options"></a>Options  
 (Colonne avec cases à cocher)  
 Sélectionnez cette option pour inclure un attribut dans la dimension.  
  
 Pour inclure un attribut particulier, activez la case à cocher de cet attribut.  
  
 Pour inclure tous les attributs, activez la case à cocher dans l'en-tête de la colonne.  
  
> [!NOTE]  
>  La case à cocher de l'attribut de clé ne peut pas être désactivée.  
  
 **Nom de l’attribut**  
 Répertorie les attributs disponibles.  
  
 Pour modifier le nom d'un attribut, cliquez sur son nom, puis tapez un nouveau nom.  
  
 **Activer la navigation**  
 Sélectionnez cette option pour permettre à l'utilisateur final de parcourir et de filtrer les attributs. L'option**Permettre la navigation** doit être sélectionnée pour l'attribut de clé. Pour les attributs non-clés, l’option **Permettre la navigation** n’est pas sélectionnée par défaut, ce qui implique que les attributs non-clés sont affichés uniquement comme propriétés de membre.  
  
 Dans la plupart des cas, l’attribut est activée ou non disponible pour la navigation en définissant le `AttributeHierarchyEnabled` propriété `True` ou `False`, respectivement. Toutefois, l'Assistant utilise des paramètres différents dans les trois cas suivants.  
  
|Cas|Paramètres|  
|----------|--------------|  
|Une dimension contient une hiérarchie parent-enfant et l’option **Permettre la navigation** n’est pas sélectionnée.|L’Assistant conserve la `AttributeHierarchyEnabled` propriété définie sur `True`et définit le `AttributeHierarchyVisible` attribut `False` pour l’attribut clé.|  
|Une table dans une dimension contient une clé étrangère à une table qui n'est pas dans la dimension|L'Assistant sélectionne la clé étrangère comme attribut à inclure, mais ne sélectionne pas **Permettre la navigation**. Si vous conservez ces paramètres, la propriété `AttributeHiearchyEnabled` de l'attribut aura la valeur `True` et la propriété `AttributeHieararchyVisible` aura la valeur `False`.|  
|Une dimension contient des tables en flocon accessibles via des colonnes clés étrangères qui acceptent la valeur NULL<br /><br /> —et—<br /><br /> L'option Permettre la navigation n'est pas sélectionnée pour l'attribut qui est basé sur la clé de la table en flocon|L’Assistant va créer le nouvel attribut qui a le `AttributeHiearchyEnabled` propriété définie sur `True`et le `AttributeHieararchyVisible` propriété définie sur `False`.|  
  
 **Type d’attribut**  
 (Facultatif) Définissez le type de l'attribut. La valeur par défaut est **Regular**. Le type d'attribut apporte aux applications clientes des indications sur les informations que l'attribut peut contenir.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
