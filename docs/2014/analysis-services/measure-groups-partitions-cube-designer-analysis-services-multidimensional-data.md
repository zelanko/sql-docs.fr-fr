---
title: Mesurer les groupes (onglet Partitions, Concepteur de Cube) (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionspane.measuregroupdetail.f1
ms.assetid: 58e44b24-cfcd-4908-b445-d4374b961b98
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7ffd5b3ff4eb98c96e1832e353e64f1953bd62e9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62727985"
---
# <a name="measure-groups-partitions-tab-cube-designer-analysis-services---multidimensional-data"></a>Groupes de mesures (onglet Partitions, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Le volet **Groupes de mesures** de l’onglet **Partitions** du Concepteur de cube permet de gérer les partitions associées à chaque groupe de mesures du cube.  
  
## <a name="options"></a>Options  
 **Partitions**  
 Affiche une grille contenant la liste des partitions qui prennent en charge le groupe de mesures sélectionné. Cette grille comporte les colonnes suivantes :  
  
 **(Ordinal)**  
 Affiche la position ordinale de la partition dans le groupe de mesures.  
  
 Cliquez pour sélectionner l'ensemble de la ligne de la partition.  
  
 **Nom de la partition**  
 Tapez le nom de la partition sélectionnée.  
  
 **Source**  
 Tapez le nom de la table (pour la liaison de table) ou la requête (pour la liaison de requête) qui fournit des données à la table de faits de la partition sélectionnée.  
  
 Cliquez sur le bouton représentant des points de suspension **...** pour afficher la boîte de dialogue **Source de la partition** et définir la source de la partition sélectionnée.  
  
 **Agrégation**  
 Affiche le mode d'agrégation et le mode de stockage de la partition. Le mode de stockage est affiché en premier : traitement ROLAP (Relational Online Analytical Processing), traitement MOLAP (Multidimensional Online Analytical Processing) ou traitement HOLAP (Hybrid Online Analytical Processing). Le mode d'agrégation est affiché sous la forme d'un pourcentage d'optimisation demandée, d'une mesure d'espace demandé ou utilisé ou du nombre d'agrégations créées. Cliquez sur le bouton représentant des points de suspension **...** pour afficher la boîte de dialogue **Assistant Conception d’agrégation** et définir la conception d’agrégation de la partition spécifiée.  
  
 **Description**  
 Tapez la description facultative de la partition.  
  
 **Nouvelle Partition...**  
 Cliquez pour afficher **l’Assistant Partition** et créer une partition dans le groupe de mesures sélectionné.  
  
 **Paramètres de stockage...**  
 Cliquez sur cette option pour afficher la boîte de dialogue **Paramètres de stockage** et définir les paramètres de mode de stockage, de mise en cache proactive et de notification pour la partition sélectionnée.  
  
> [!NOTE]  
>  Cette option est activée uniquement si une cellule d’une partition est sélectionnée dans la grille **Partitions** du groupe de mesures sélectionné.  
  
 **Paramètres d’écriture différée...**  
 Cliquez sur cette option pour afficher la boîte de dialogue **Activer/Désactiver l’écriture différée** et définir les paramètres d’écriture différée pour le groupe de mesures sélectionné.  
  
## <a name="context-menu"></a>Menu contextuel  
 Les options suivantes sont disponibles dans le menu contextuel qui s’affiche quand vous cliquez avec le bouton droit sur une ligne dans la grille **Partitions** d’un groupe de mesures sélectionné :  
  
|Option|Définition|  
|------------|----------------|  
|**Ajouter Business Intelligence**|Affiche l' **Assistant Business Intelligence** pour ajouter au cube des fonctionnalités d'aide à la décision. Pour plus d’informations sur **l’Assistant Business Intelligence**, consultez [Aide (F1) de l’Assistant Business Intelligence](business-intelligence-wizard-f1-help.md).|  
|**Nouvelle Partition**|Cliquez pour afficher **l’Assistant Partition** et créer une partition dans le groupe de mesures sélectionné.|  
|**Renommer la Partition**|Sélectionnez pour renommer la partition sélectionnée.|  
|**Supprimer**|Cliquez sur cette option pour afficher la boîte de dialogue **Supprimer les objets** et supprimer l’action sélectionnée.<br /><br /> Remarque : Cette option est désactivée si une partition avec écriture différée est sélectionnée.|  
|**Concevoir des agrégations**|Cliquez sur cette option pour afficher **l’Assistant Conception d’agrégation** et créer une conception d’agrégation pour la partition sélectionnée.<br /><br /> Remarque : Cette option est désactivée si une partition avec écriture différée est sélectionnée.|  
|**Paramètres de stockage**|Cliquez sur cette option pour afficher la boîte de dialogue **Paramètres de stockage** et définir les paramètres de mode de stockage, de mise en cache proactive et de notification pour la partition sélectionnée.|  
|**Paramètres d’écriture différée**|Cliquez sur cette option pour afficher la boîte de dialogue **Activer/Désactiver l’écriture différée** et définir les paramètres d’écriture différée pour le groupe de mesures contenant la partition sélectionnée.|  
|**L’optimisation basée sur l’utilisation**|Cliquez sur cette option pour afficher **l’Assistant Optimisation de l’utilisation** et créer une conception d’agrégation basée sur des modèles d’utilisation existants pour la partition sélectionnée.<br /><br /> Remarque : Cette option est désactivée si une partition avec écriture différée est sélectionnée.|  
|**Traiter**|Cliquez sur cette option pour afficher la boîte de dialogue **Traiter** et traiter la partition sélectionnée.|  
|**Copier**|Cette option est désactivée.|  
|**Coller**|Cette option est désactivée.|  
|**Propriétés**|Sélectionnez cette option pour afficher la fenêtre **Propriétés** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour la partition sélectionnée.|  
  
  
