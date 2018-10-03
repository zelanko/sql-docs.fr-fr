---
title: Interroger le volet (vue prévision de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.query.f1
ms.assetid: fdeec72e-d0bd-4453-9eaa-46436e4d6edc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 316b82f15c28a13a2a04bdd81683d2fdf83707bb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133229"
---
# <a name="query-pane-mining-model-prediction-view"></a>Volet Requête (vue Prévision de modèle d'exploration de données)
  Le volet **Requête** affiche les instructions DMX (Data Mining Extensions) créées par le Générateur de requêtes de prévisions. Vous pouvez modifier les instructions, puis cliquer sur le bouton **Basculer vers l'affichage du résultat de la requête** pour retourner les résultats. Si vous basculez de nouveau vers la vue **Conception**, les modifications éventuelles apportées à l'instruction seront perdues.  
  
 **Pour plus d’informations :** [Instructions de manipulations de données DMX &#40;Data Mining Extensions&#41;](/sql/dmx/dmx-statements-data-manipulation), [Créer une requête DMX dans SQL Server Management Studio](data-mining/create-a-dmx-query-in-sql-server-management-studio.md)  
  
## <a name="options"></a>Options  
 **Basculez vers l’affichage des résultats de requête**  
 Sélectionnez cette option pour basculer entre les volets **Conception**, **Requête**et **Résultat** . Lorsque vous basculez vers le volet **Résultat** , la requête est exécutée.  
  
 **Enregistrer le résultat de requête**  
 Ouvre la boîte de dialogue **Enregistrer le résultat de la requête d’exploration de données** .  
  
 **Requête singleton**  
 Permet de créer une requête singleton, dans laquelle vous fournissez les données d'entrée directement dans votre requête au lieu de fournir une référence à une table de valeur d'entrée. Le tableau **Sélectionner une ou plusieurs tables d’entrée** est remplacé par un tableau **Entrée de requête singleton** . La requête de prévision actuelle est perdue si vous basculez vers une requête singleton.  
  
 **Actualiser les résultats de requête**  
 Traite une nouvelle fois la requête de prévision. Cette option est activée uniquement dans le volet **Résultat** .  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de requête d’exploration de données](data-mining/data-mining-query-tools.md)   
 [Data Mining Extensions &#40;DMX&#41; référence des instructions](/sql/dmx/data-mining-extensions-dmx-statements)   
 [Générateur de requêtes de prédiction &#40;exploration de données&#41;](prediction-query-builder-data-mining.md)  
  
  
