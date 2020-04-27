---
title: Choisir des améliorations (Assistant Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.bienhancement.f1
ms.assetid: 39e2f36c-2c02-4a71-af8f-5dbd373190dc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 687f7fb96ee5a2b96d80562c20d536eeeb308379
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66088116"
---
# <a name="choose-enhancement-business-intelligence-wizard"></a>Choisir des améliorations (Assistant Business Intelligence)
  Utilisez la page **Choisir des améliorations** pour choisir l'amélioration Business Intelligence à ajouter au cube ou à la dimension.  
  
## <a name="options"></a>Options  
 **Améliorations disponibles**  
 Sélectionnez l'amélioration Business Intelligence à ajouter. Le tableau ci-après répertorie les améliorations disponibles.  
  
|Amélioration|Description|  
|-----------------|-----------------|  
|**Définir en fonction du temps**|Ajoute des vues de temps pour une hiérarchie sélectionnée. Ces vues sont de type période-à-date, moyenne tournante et période-à-période.<br /><br /> Remarque : cette option est disponible uniquement pour les cubes.|  
|**Définir l'intelligence comptable**|Affecte des classifications de comptabilité standard, telles que bénéfices et dépenses, pour les membres d'un attribut de compte.<br /><br /> Si la fonction d’agrégation de la mesure a la valeur *ByAccount*, l’instance [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise les classifications de comptabilité pour agréger une mesure dans les membres d’un attribut de compte dans le temps.|  
|**Définir l'intelligence des dimensions**|Utilisez l'intelligence des dimensions pour définir un type d'entreprise standard et des types valides pour les attributs de dimension. Les applications clientes peuvent utiliser ces spécifications de type lors de l'analyse de données.|  
|**Spécifier un opérateur unaire**|Définissez un opérateur unaire pour remplacer l'agrégation par défaut qui est associée aux membres d'une hiérarchie parent-enfant d'un cube.<br /><br /> Remarque : cette option est disponible uniquement pour les cubes.|  
|**Créer une formule de membre personnalisée**|Créez une formule de membre personnalisée pour remplacer l'agrégation par défaut associée à un membre de dimension par un opérateur différent.|  
|**Spécifier l'ordre des attributs**|Définissez l'ordre des membres d'un attribut sélectionné. Les membres peuvent être triés en fonction du nom ou de la clé d'un attribut sélectionné, ou en fonction du nom ou de la clé d'un attribut associé à l'attribut sélectionné. Par défaut, les membres sont triés en fonction du nom de l'attribut sélectionné.|  
|**Activer l'écriture différée de la dimension**|Active l'écriture différée de la structure de dimension. Les mises à jour dans une dimension activée en écriture sont enregistrées directement dans la table de la dimension.|  
|**Définir le comportement semi-additif**|Définissez manuellement la méthode d'agrégation des mesures ou des membres individuels d'un attribut de type de compte. Si le cube contient une dimension de compte, vous pouvez utiliser l’option **Définir l’intelligence comptable** pour définir automatiquement le comportement semi-additif en fonction du type de compte.<br /><br /> Remarque : cette option est disponible uniquement pour les cubes.|  
|**Définir la conversion monétaire**|Définissez les règles de conversion et d'analyse des données multinationales du cube. Les règles de conversion sont appliquées dans le cube à l'aide d'un script MDX (Multidimensional Expressions) généré par l'Assistant Business Intelligence.<br /><br /> Remarque : cette option est disponible uniquement pour les cubes.|  
  
 **Description**  
 Fournit une brève description de l'amélioration Business Intelligence sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant Business Intelligence](business-intelligence-wizard-f1-help.md)   
 [Concepteur de cube &#40;Analysis Services-données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Concepteur de dimensions &#40;Analysis Services-données multidimensionnelles&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
