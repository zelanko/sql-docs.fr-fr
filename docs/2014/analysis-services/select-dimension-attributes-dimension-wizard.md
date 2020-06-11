---
title: Sélectionner les attributs de la dimension (Assistant Dimension) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionattributes.f1
ms.assetid: f58a3e14-ab27-44d3-8c26-f5c9ee7583b0
author: minewiskan
ms.author: owend
ms.openlocfilehash: dcaf18ea2df3bbd3b227c8948d2fb15f54828853
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84537921"
---
# <a name="select-dimension-attributes-dimension-wizard"></a>Sélectionner les attributs de la dimension (Assistant Dimension)
  Utilisez la page **Sélectionner les attributs de la dimension** pour sélectionner et modifier les attributs de la dimension à créer.  
  
> [!NOTE]  
>  Si vous avez des difficultés à lire les valeurs d'une colonne, agrandissez la fenêtre de l'Assistant et modifiez la largeur de chaque en-tête de colonne jusqu'à ce que les valeurs soient lisibles.  
  
 **Pour ouvrir l'Assistant Dimension**  
  
-   Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **Dimensions** pour un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis cliquez sur **Nouvelle dimension**.  
  
## <a name="options"></a>Options  
 (Colonne avec cases à cocher)  
 Sélectionnez cette option pour inclure un attribut dans la dimension.  
  
 Pour inclure un attribut particulier, activez la case à cocher de cet attribut.  
  
 Pour inclure tous les attributs, activez la case à cocher dans l'en-tête de la colonne.  
  
> [!NOTE]  
>  La case à cocher de l'attribut de clé ne peut pas être désactivée.  
  
 **Nom de l'attribut**  
 Répertorie les attributs disponibles.  
  
 Pour modifier le nom d'un attribut, cliquez sur son nom, puis tapez un nouveau nom.  
  
 **Permettre la navigation**  
 Sélectionnez cette option pour permettre à l'utilisateur final de parcourir et de filtrer les attributs. L'option**Permettre la navigation** doit être sélectionnée pour l'attribut de clé. Pour les attributs non-clés, l’option **Permettre la navigation** n’est pas sélectionnée par défaut, ce qui implique que les attributs non-clés sont affichés uniquement comme propriétés de membre.  
  
 Dans la plupart des cas, la navigation dans les attributs est activée ou désactivée en affectant respectivement la valeur `AttributeHierarchyEnabled` ou `True` à la propriété `False`. Toutefois, l'Assistant utilise des paramètres différents dans les trois cas suivants.  
  
|Cas|Paramètres|  
|----------|--------------|  
|Une dimension contient une hiérarchie parent-enfant et l’option **Permettre la navigation** n’est pas sélectionnée.|L'Assistant conserve la valeur `AttributeHierarchyEnabled` pour la propriété `True` et affecte la valeur `AttributeHierarchyVisible` à l'attribut `False` pour l'attribut de clé.|  
|Une table dans une dimension contient une clé étrangère à une table qui n'est pas dans la dimension|L'Assistant sélectionne la clé étrangère comme attribut à inclure, mais ne sélectionne pas **Permettre la navigation**. Si vous conservez ces paramètres, la propriété `AttributeHiearchyEnabled` de l'attribut aura la valeur `True` et la propriété `AttributeHierarchyVisible` aura la valeur `False`.|  
|Une dimension contient des tables en flocon accessibles via des colonnes clés étrangères qui acceptent la valeur NULL<br /><br /> -et-<br /><br /> L'option Permettre la navigation n'est pas sélectionnée pour l'attribut qui est basé sur la clé de la table en flocon|L'Assistant créera le nouvel attribut dont la propriété `AttributeHiearchyEnabled` a la valeur `True` et dont la propriété `AttributeHierarchyVisible` a la valeur `False`.|  
  
 **Type d’attribut**  
 (Facultatif) Définissez le type de l'attribut. La valeur par défaut est **Regular**. Le type d'attribut apporte aux applications clientes des indications sur les informations que l'attribut peut contenir.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services-données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
