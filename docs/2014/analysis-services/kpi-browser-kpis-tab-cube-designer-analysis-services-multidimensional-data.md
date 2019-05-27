---
title: Navigateur d’indicateur de performance clé (onglet des indicateurs de performance clés, Concepteur de Cube) (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.kpibrowserpane.f1
ms.assetid: 2f61bde6-e6ec-4511-8645-c272374014ad
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 41000c78c4ff3a68e1d3acd107ce57c221a16e28
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66079498"
---
# <a name="kpi-browser-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a>Navigateur d'indicateur de performance clé (onglet Indicateurs de performance clés, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Le volet **Navigateur d’indicateur de performance clé** de l’onglet **Indicateurs de performance clés** du Concepteur de cube permet d’afficher et de tester les résultats des indicateurs de performance clés (KPI). Vous devez d'abord déployer les indicateurs de performance clés sur une instance [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] avant d'exécuter le navigateur.  
  
> [!NOTE]  
>  Ce volet s'affiche uniquement en mode Navigateur.  
  
## <a name="options"></a>Options  
 **Grille sous-cube**  
 Permet de définir un sous-cube et de limiter les résultats des indicateurs de performance clés à afficher dans le volet **Résultats** . Cette grille comporte les colonnes suivantes :  
  
 **Dimension**  
 Sélectionnez la dimension à laquelle ce filtre s'applique.  
  
 **Hierarchy**  
 Sélectionnez la hiérarchie à laquelle ce filtre s'applique.  
  
 **Opérateur**  
 Sélectionnez l’opérateur qui définit comment l’expression dans **Expression de filtre** est appliquée à la hiérarchie sélectionnée. Le tableau suivant décrit les opérateurs disponibles.  
  
|Value|Description|  
|-----------|-----------------|  
|**égal**|Les résultats se limitent à l'ensemble défini dans **Expression de filtre**.|  
|**Non égal**|Les résultats se limitent aux membres n'appartenant pas à l'ensemble défini dans **Expression de filtre**.|  
|**Dans**|Les résultats se limitent à l'ensemble nommé choisi dans **Expression de filtre**.|  
|**Pas dans**|Les résultats se limitent aux membres n'appartenant pas à l'ensemble nommé choisi dans **Expression de filtre**.|  
|**Contient**|Les résultats se limitent aux membres dont le nom contient la chaîne de caractères figurant dans **Expression de filtre**.|  
|**Commence par**|Les résultats se limitent aux membres dont le nom commence par la chaîne de caractères figurant dans **Expression de filtre**.|  
|**Plage (limites incluses)**|Les résultats se limitent à la plage choisie dans **Expression de filtre**.|  
|**Plage (limites exclues)**|Les résultats se limitent aux membres n'appartenant pas à la plage choisie dans **Expression de filtre**.|  
|**MDX**|Les résultats se limitent aux expressions MDX (Multidimensional Expressions) définies dans **Expression de filtre**.|  
  
 **Expression de filtre**  
 Tapez l’expression que **Opérateur**doit évaluer, qui se limite aux résultats des indicateurs de performance clés à parcourir.  
  
> [!NOTE]  
>  Ce champ est un élément dynamique de saisie des données dont l'aspect change en fonction des types de données nécessaires à l'opérateur sélectionné.  
  
 **Grille de résultats**  
 Affiche la valeur évaluée, l’objectif, l’état et la tendance pour les indicateurs de performance clés, en fonction du filtre défini dans la **Grille de filtrage**. Cette grille comporte les colonnes suivantes :  
  
 **Structure d’affichage**  
 Affiche les indicateurs de performance clés contenus dans le cube. Ils sont organisés hiérarchiquement en fonction des valeurs **Afficher le dossier** ou **Indicateur de performance clé parent** pour chaque KPI.  
  
 **Valeur**  
 Affiche la valeur de l'indicateur de performance clé.  
  
 **Objectif**  
 Affiche l'objectif de l'indicateur de performance clé.  
  
 **État**  
 Affiche le graphique d'état de l'indicateur de performance clé.  
  
 **Trend**  
 Affiche le graphique de tendance de l'indicateur de performance clé.  
  
 **Weight**  
 Affiche le facteur poids de l'indicateur de performance clé.  
  
 **(Description)**  
 Affiche une icône d'information si l'indicateur de performance clé est associé à une description.  
  
 Placez le pointeur de la souris sur l'icône d'information afin d'afficher une info-bulle contenant la description de l'indicateur de performance clé.  
  
> [!NOTE]  
>  Si une erreur se produit lors du calcul d’un indicateur de performance clé sur l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , cette option affiche les informations relatives à l’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs de performance clés &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  
