---
title: Interroger les paramètres utilisés pour créer un modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: ce7719e0-6127-4d9c-a753-0e0a3db065e1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b10717491672e0323afb39ada55aafff5c056caf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62733051"
---
# <a name="query-the-parameters-used-to-create-a-mining-model"></a>Interroger les paramètres utilisés pour créer un modèle d'exploration de données
  La composition d'un modèle d'exploration de données est affecté non seulement par les cas d'apprentissage, mais aussi par les paramètres définis lors de la création du modèle. Par conséquent, il peut s'avérer utile d'extraire les paramètres d'un modèle existant pour mieux comprendre le comportement du modèle. La récupération des paramètres peut aussi servir à documenter une version particulière de ce modèle.  
  
 Pour rechercher les paramètres qui ont été utilisés lors de la création du modèle, vous créez une requête sur l'un des ensembles de lignes de schéma de modèle d'exploration de données. Dans [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], ces ensembles de lignes de schéma sont exposés sous la forme d’un ensemble de vues système que vous pouvez interroger facilement en utilisant la syntaxe Transact-SQL. Cette procédure décrit comment créer une requête qui retourne les paramètres qui ont été utilisés pour créer le modèle d'exploration de données spécifié.  
  
### <a name="to-open-a-query-window-for-a-schema-rowset-query"></a>Pour ouvrir une fenêtre Requête pour une requête d'ensemble de lignes de schéma  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient le modèle à interroger.  
  
2.  Cliquez avec le bouton droit sur le nom de l’instance, sélectionnez **Nouvelle requête**, puis sélectionnez **DMX**.  
  
    > [!NOTE]  
    >  Vous pouvez également créer une requête sur un modèle d’exploration de données en utilisant le modèle **MDX** .  
  
3.  Si l'instance contient plusieurs bases de données, sélectionnez la base de données contenant le modèle à interroger dans la liste **Bases de données disponibles** dans la barre d'outils.  
  
### <a name="to-return-model-parameters-for-an-existing-mining-model"></a>Pour retourner les paramètres de modèle pour un modèle d'exploration de données existant  
  
1.  Dans le volet Requête DMX, tapez ou collez le texte suivant :  
  
    ```  
    SELECT MINING_PARAMETERS  
    FROM $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = ''  
    ```  
  
2.  Dans l'Explorateur d'objets, sélectionnez le modèle d'exploration de données désiré, puis faites-le glisser dans le volet Requête DMX entre les guillemets simples.  
  
3.  Appuyez sur F5 ou cliquez sur **Exécuter**.  
  
## <a name="example"></a>Exemple  
 Le code suivant retourne la liste des paramètres utilisés pour créer le modèle d'exploration de données dans le [Didacticiel sur l'exploration de données de base](../../tutorials/basic-data-mining-tutorial.md). Ces paramètres incluent les valeurs explicites des options par défaut utilisées par les services d'exploration de données disponibles à partir des fournisseurs sur le serveur.  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
 L'exemple de code retourne les paramètres suivants pour le modèle de clustering :  
  
 Résultats de l'exemple :  
  
 MINING_PARAMETERS  
  
 CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de requête d’exploration de données et procédures](data-mining-query-tasks-and-how-tos.md)   
 [Requêtes d’exploration de données](data-mining-queries.md)  
  
  
