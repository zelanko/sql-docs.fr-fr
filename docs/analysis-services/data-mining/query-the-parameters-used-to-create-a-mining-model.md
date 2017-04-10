---
title: "Interroger les param&#232;tres utilis&#233;s pour cr&#233;er un mod&#232;le d&#39;exploration de donn&#233;es | Microsoft Docs"
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
  - "requêtes de contenu [DMX]"
ms.assetid: ce7719e0-6127-4d9c-a753-0e0a3db065e1
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 13
---
# Interroger les param&#232;tres utilis&#233;s pour cr&#233;er un mod&#232;le d&#39;exploration de donn&#233;es
  La composition d'un modèle d'exploration de données est affecté non seulement par les cas d'apprentissage, mais aussi par les paramètres définis lors de la création du modèle. Par conséquent, il peut s'avérer utile d'extraire les paramètres d'un modèle existant pour mieux comprendre le comportement du modèle. La récupération des paramètres peut aussi servir à documenter une version particulière de ce modèle.  
  
 Pour rechercher les paramètres qui ont été utilisés lors de la création du modèle, vous créez une requête sur l'un des ensembles de lignes de schéma de modèle d'exploration de données. Dans [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], ces ensembles de lignes de schéma sont exposés sous la forme d’un ensemble de vues système que vous pouvez interroger facilement en utilisant la syntaxe Transact-SQL. Cette procédure décrit comment créer une requête qui retourne les paramètres qui ont été utilisés pour créer le modèle d'exploration de données spécifié.  
  
### Pour ouvrir une fenêtre Requête pour une requête d'ensemble de lignes de schéma  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient le modèle à interroger.  
  
2.  Cliquez avec le bouton droit sur le nom de l’instance, sélectionnez **Nouvelle requête**, puis sélectionnez **DMX**.  
  
    > [!NOTE]  
    >  Vous pouvez également créer une requête sur un modèle d’exploration de données en utilisant le modèle **MDX**.  
  
3.  Si l'instance contient plusieurs bases de données, sélectionnez la base de données contenant le modèle à interroger dans la liste **Bases de données disponibles** dans la barre d'outils.  
  
### Pour retourner les paramètres de modèle pour un modèle d'exploration de données existant  
  
1.  Dans le volet Requête DMX, tapez ou collez le texte suivant :  
  
    ```  
    SELECT MINING_PARAMETERS  
    FROM $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = ''  
    ```  
  
2.  Dans l'Explorateur d'objets, sélectionnez le modèle d'exploration de données désiré, puis faites-le glisser dans le volet Requête DMX entre les guillemets simples.  
  
3.  Appuyez sur F5 ou cliquez sur **Exécuter**.  
  
## Exemple  
 Le code suivant retourne la liste des paramètres utilisés pour créer le modèle d'exploration de données dans le [Didacticiel sur l'exploration de données de base](../Topic/Basic%20Data%20Mining%20Tutorial.md). Ces paramètres incluent les valeurs explicites des options par défaut utilisées par les services d'exploration de données disponibles à partir des fournisseurs sur le serveur.  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
 L'exemple de code retourne les paramètres suivants pour le modèle de clustering :  
  
 Résultats de l'exemple :  
  
 MINING_PARAMETERS  
  
 CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10  
  
## Voir aussi  
 [Tâches de requête d'exploration de données et procédures](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)   
 [Requêtes d'exploration de données](../../analysis-services/data-mining/data-mining-queries.md)  
  
  