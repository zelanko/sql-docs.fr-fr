---
title: Options de schéma de la base de données de la zone de sujet (Assistant génération de schéma) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.subjectareaschemaopts.f1
ms.assetid: 4c109bb8-e19d-412b-908f-bfdd7f872439
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7edc1fc89e9463c7482b47866aa3d12e1bc231a7
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940240"
---
# <a name="subject-area-database-schema-options-schema-generation-wizard-analysis-services---multidimensional-data"></a>Options du schéma de la base de données de la zone de sujet (Assistant Génération de schéma) (Analysis Services - Données multidimensionnelles)
  Utilisez la page **Options du schéma de la base de données de la zone de sujet** pour contrôler la génération du schéma et définir la préservation des données.  
  
## <a name="options"></a>Options  
 **Schéma propriétaire**  
 Définit le nom du schéma dans la nouvelle base de données de la zone de sujet.  
  
 **Créer des clés primaires sur les tables de la dimension**  
 Crée des clés primaires dans les tables de dimension dans le schéma généré. Aucun index n'est généré si vous ne sélectionnez pas cette option.  
  
> [!NOTE]  
>  Si vous ne sélectionnez pas cette option, l'intégrité référentielle est améliorée.  
  
 **Créer des index**  
 Crée des index dans les colonnes clés étrangères dans le schéma généré.  
  
 **Appliquer l'intégrité référentielle**  
 Applique l'intégrité référentielle dans le schéma généré. Si vous ne sélectionnez pas cette option, les relations sont créées, mais pas appliquées.  
  
 **Préserver les données lors de la régénération**  
 Conserve les données dans base de données de la zone de sujet lorsque l'Assistant termine son exécution. Si vous ne sélectionnez pas cette option, toutes les données de la base de données de la zone de sujet peuvent être effacées sans avertissement.  
  
 **Remplir la ou les tables de temps**  
 Définit la manière dont l'Assistant remplit les tables de temps. Le tableau suivant répertorie les valeurs possibles de cette option.  
  
> [!NOTE]  
>  Cette option est activée uniquement si l’Assistant Génération de schéma est ouvert depuis un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en utilisant [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] en mode projet.  
  
|Value|Description|  
|-----------|-----------------|  
|Remplir|Les tables de temps de la zone de sujet sont remplies.|  
|Ne pas remplir|Les tables de temps de la zone de sujet ne sont pas remplies.|  
|Remplir uniquement si la table est vide|Les tables de temps de la zone de sujet sont remplies uniquement si elles sont vides.|  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant génération de schéma &#40;Analysis Services-données multidimensionnelles&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md)  
  
  
