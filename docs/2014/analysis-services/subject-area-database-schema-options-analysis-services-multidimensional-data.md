---
title: Objet d’Options de schéma de base de données de zone (Assistant génération de schéma) (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.subjectareaschemaopts.f1
ms.assetid: 4c109bb8-e19d-412b-908f-bfdd7f872439
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e608f6ca210f1d86a58b469145a9840f7c25ba2b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62758498"
---
# <a name="subject-area-database-schema-options-schema-generation-wizard-analysis-services---multidimensional-data"></a>Options du schéma de la base de données de la zone de sujet (Assistant Génération de schéma) (Analysis Services - Données multidimensionnelles)
  Utilisez la page **Options du schéma de la base de données de la zone de sujet** pour contrôler la génération du schéma et définir la préservation des données.  
  
## <a name="options"></a>Options  
 **Schéma propriétaire**  
 Définit le nom du schéma dans la nouvelle base de données de la zone de sujet.  
  
 **Créer des clés primaires sur les tables de dimension**  
 Crée des clés primaires dans les tables de dimension dans le schéma généré. Aucun index n'est généré si vous ne sélectionnez pas cette option.  
  
> [!NOTE]  
>  Si vous ne sélectionnez pas cette option, l'intégrité référentielle est améliorée.  
  
 **Créer des index**  
 Crée des index dans les colonnes clés étrangères dans le schéma généré.  
  
 **Appliquer l’intégrité référentielle**  
 Applique l'intégrité référentielle dans le schéma généré. Si vous ne sélectionnez pas cette option, les relations sont créées, mais pas appliquées.  
  
 **Préserver les données lors de la régénération**  
 Conserve les données dans base de données de la zone de sujet lorsque l'Assistant termine son exécution. Si vous ne sélectionnez pas cette option, toutes les données de la base de données de la zone de sujet peuvent être effacées sans avertissement.  
  
 **Remplir une ou plusieurs tables de temps**  
 Définit la manière dont l'Assistant remplit les tables de temps. Le tableau suivant répertorie les valeurs possibles de cette option.  
  
> [!NOTE]  
>  Cette option est activée uniquement si l’Assistant Génération de schéma est ouvert depuis un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en utilisant [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] en mode projet.  
  
|Value|Description|  
|-----------|-----------------|  
|Remplir|Les tables de temps de la zone de sujet sont remplies.|  
|Ne pas remplir|Les tables de temps de la zone de sujet ne sont pas remplies.|  
|Remplir uniquement si la table est vide|Les tables de temps de la zone de sujet sont remplies uniquement si elles sont vides.|  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 d’Assistant génération de schéma &#40;Analysis Services - données multidimensionnelles&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md)  
  
  
