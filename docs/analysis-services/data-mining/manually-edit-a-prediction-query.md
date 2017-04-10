---
title: "Modifier manuellement une requ&#234;te de pr&#233;diction | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "requêtes de prédiction, modification"
  - "Prédiction de modèle d’exploration de données [Analysis Services], modification des requêtes de prédiction"
  - "modification manuelle d'une requête de prédiction [Analysis Services]"
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 17
---
# Modifier manuellement une requ&#234;te de pr&#233;diction
  Après avoir créé une requête en utilisant le Générateur de requêtes de prédiction, vous pouvez modifier la requête en activant le mode Texte de la requête sous l’onglet **Prédiction de modèle d’exploration de données** du Concepteur d’exploration de données. Un éditeur de texte apparaît au bas de l'écran pour afficher la requête créée par le Générateur de requêtes.  
  
 Le basculement vers le mode Texte de la requête est utile pour effectuer des ajouts à la requête. Par exemple, vous pouvez ajouter une clause WHERE ou une clause ORDER BY.  
  
 Utilisez la grille dans le Générateur de requêtes de prédiction pour insérer le nom des objets et des colonnes, ainsi que pour configurer la syntaxe de fonctions de prédiction individuelles, puis basculez vers le mode de modification manuelle pour modifier des valeurs de paramètres.  
  
> [!NOTE]  
>  Si vous repassez du mode **Texte de la requête** au mode **Conception**, toutes les modifications apportées en mode **Texte de la requête** sont perdues.  
  
### Modifier une requête  
  
1.  Sous l’onglet **Prédiction de modèle d’exploration de données** du Concepteur d’exploration de données de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur **SQL**.  
  
     La grille au bas de l'écran est remplacée par un éditeur de texte qui contient la requête. Vous pouvez modifier la requête dans cet éditeur.  
  
2.  Pour exécuter la requête, dans le menu **Modèle d’exploration de données**, sélectionnez **Résultat** ou cliquez sur le bouton pour passer aux résultats de la requête.  
  
    > [!NOTE]  
    >  Si la requête que vous avez créée n'est pas valide, la fenêtre Résultats n'affiche ni erreur ni résultats. Cliquez sur le bouton **Conception** ou sélectionnez **Conception** ou **Requête** dans le menu **Modèle d’exploration de données**pour résoudre le problème et réexécuter la requête.  
  
## Voir aussi  
 [Requêtes d'exploration de données](../../analysis-services/data-mining/data-mining-queries.md)   
 [Générateur de requêtes de prédiction &#40;exploration de données&#41;](../Topic/Prediction%20Query%20Builder%20\(Data%20Mining\).md)   
 [Leçon 6 : création et utilisation de prédictions &#40;Didacticiel sur l’exploration de données de base&#41;](../Topic/Lesson%206:%20Creating%20and%20Working%20with%20Predictions%20\(Basic%20Data%20Mining%20Tutorial\).md)  
  
  