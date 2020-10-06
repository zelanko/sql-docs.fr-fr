---
description: Présentation de l'instruction DMX Select
title: Fonctionnement de l’instruction DMX Select | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 14e4c99cd907a5f9a18dd11d77988d728557c4bd
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726060"
---
# <a name="understanding-the-dmx-select-statement"></a>Présentation de l'instruction DMX Select
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  L’instruction [Select](../dmx/select-dmx.md) est la base de la plupart des requêtes que vous créez avec les extensions DMX (Data Mining Extensions) dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Elle peut effectuer une grande diversité de tâches, par exemple la navigation et la prévision dans les modèles d'exploration de données.  
  
 Voici les tâches que vous pouvez effectuer à l’aide de l’instruction **Select** :  
  
-   Explorer un modèle d'exploration de données. L'ensemble de lignes du schéma définit la structure d'un modèle.  
  
-   Découvrir les valeurs possibles de la colonne d'un modèle d'exploration de données.  
  
-   Explorer les cas qui sont affectés aux nœuds d'un modèle d'exploration de données, ou obtenir un cas représentatif.  
  
-   Créer des prédictions à l'aide de diverses entrées.  
  
-   Copier des modèles d'exploration de données.  
  
 Chacune de ces tâches utilise un ensemble de données différent, que nous appellerons un *domaine de données*. Vous définissez le domaine de données dans la clause **from** de l’instruction.  
  
-   Vous recherchez les objets dans le modèle d'exploration de données lui-même, par exemple la règle définissant un jeu de données, ou une formule utilisée pour faire des prédictions.  
  
     Dans ce cas, vous devez examiner les métadonnées stockées dans le modèle lui-même. Par conséquent, votre domaine de données correspond aux colonnes de l'ensemble de lignes de schéma d'exploration de données.  
  
-   Vous obtenez des informations détaillées à partir des cas utilisés pour générer le modèle.  
  
     Dans ce cas, vous devez extraire la structure d'exploration de données, qui est votre domaine de données, puis rechercher les lignes individuelles dans les colonnes telles que Gender, Bike Buyer, et ainsi de suite.  
  
 **Important :** Tout ce qui est inclus dans la liste d’expressions ou dans la clause **Where** doit provenir du domaine de données défini par la clause **from** . Vous ne pouvez pas mélanger des domaines de données.  
  
##  <a name="select-types"></a><a name="Select_Types"></a> SÉLECTIONNER les types  
 La syntaxe de l’instruction **Select** prend en charge de nombreuses tâches différentes. Utilisez les modèles suivants pour effectuer ces tâches :  
  
-   [Prédiction](#Predicting)  
  
-   [Navigation](#Browsing)  
  
-   [Destination](#Copying)  
  
-   [Extraction](#Drillthrough)  
  
###  <a name="predicting"></a><a name="Predicting"></a> Prédiction  
 Vous effectuez des prévisions sur la base d'un modèle d'exploration de données en utilisant les types de requêtes suivants.  
  
 Vous pouvez inclure l’une des instructions **Select** de navigation ou de prédiction dans les clauses **from** et **Where** d’une instruction PREDICTION JOIN **Select** .  
  
|Type de requête|Description|  
|----------------|-----------------|  
|SELECT FROM [NATURAL] PREDICTION JOIN|Retourne une prévision qui est créée en joignant les colonnes du modèle d'exploration de données aux colonnes d'une source de données interne.<br /><br /> Le domaine de ce type de requête sont les colonnes prédictibles du modèle et les colonnes de la source de données d'entrée.<br /><br /> [Sélectionnez un modèle de &#60;&#62; &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)<br /><br /> [Requêtes de prédiction &#40;Exploration de données&#41;](/analysis-services/data-mining/prediction-queries-data-mining)|  
|SÉLECTIONNER DANS *\<model>*|Retourne l'état le plus probable de la colonne prédictible, uniquement sur la base du modèle d'exploration de données. Ce type de requête est un raccourci pour créer une prévision avec une jointure de prévision vide.<br /><br /> Le domaine de ce type de requête sont les colonnes prédictibles du modèle.<br /><br /> [Sélectionnez un modèle de &#60;&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md)<br /><br /> [Requêtes de prédiction &#40;Exploration de données&#41;](/analysis-services/data-mining/prediction-queries-data-mining)|  
  
 [Retour à Types SELECT](#Select_Types)  
  
###  <a name="browsing"></a><a name="Browsing"></a> Recherches  
 Vous pouvez naviguer dans le contenu d'un modèle d'exploration de données en utilisant les types de requêtes suivants.  
  
|Type de requête|Description|  
|----------------|-----------------|  
|SELECT DISTINCT FROM *\<model>*|Retourne toutes les valeurs d'état provenant du modèle d'exploration de données pour la colonne spécifiée.<br /><br /> Le domaine de données pour ce type de requête est le modèle d'exploration de données.<br /><br /> [SELECT DISTINCT FROM &#60;modèle &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)<br /><br /> [Requêtes de contenu &#40;Exploration de données&#41;](/analysis-services/data-mining/content-queries-data-mining)|  
|Sélectionnez à partir de *\<model>* . HUMIDITÉ|Retourne le contenu décrivant le modèle d'exploration de données.<br /><br /> Le domaine de données pour ce type de requête est l'ensemble de lignes du contenu.<br /><br /> [Sélectionnez &#60;&#62; de modèle. &#40;DE CONTENU DMX&#41;](../dmx/select-from-model-content-dmx.md)<br /><br /> [Requêtes de contenu &#40;Exploration de données&#41;](/analysis-services/data-mining/content-queries-data-mining)|  
|Sélectionnez à partir de *\<model>* . DIMENSION_CONTENT|Retourne le contenu décrivant le modèle d'exploration de données.<br /><br /> Le domaine de données pour ce type de requête est l'ensemble de lignes du contenu.<br /><br /> [Sélectionnez &#60;&#62; de modèle.&#41;DIMENSION_CONTENT &#40;DMX ](../dmx/select-from-model-dimension-content-dmx.md)|  
|Sélectionnez à partir de *\<model>* . PMML|Retourne la représentation PMML (Predictive Model Markup Language) du modèle d'exploration de données, pour les algorithmes qui prennent en charge cette fonctionnalité.<br /><br /> Le domaine pour ce type de requête est l'ensemble de lignes du schéma PMML.<br /><br /> [Ensemble de lignes DMSCHEMA_MINING_MODEL_CONTENT_PMML](/previous-versions/sql/sql-server-2012/ms126283(v=sql.110))|  
  
 [Retour à Types SELECT](#Select_Types)  
  
###  <a name="copying"></a><a name="Copying"></a> Destination  
 Vous pouvez copier un modèle d'exploration de données et sa structure d'exploration de données associée dans un nouveau modèle, puis renommer le modèle dans l'instruction.  
  
|Type de requête|Description|  
|----------------|-----------------|  
|SÉLECTIONNER DANS *\<new model>*|Crée une copie du modèle d'exploration de données.<br /><br /> Le domaine pour ce type de requête est le modèle d'exploration de données.<br /><br /> [SÉLECTIONNER DANS &#40;&#41;DMX ](../dmx/select-into-dmx.md)|  
  
 [Retour à Types SELECT](#Select_Types)  
  
###  <a name="drillthrough"></a><a name="Drillthrough"></a> D’extraction  
 Vous pouvez naviguer dans les cas, ou dans une représentation des cas, qui ont servi à l'apprentissage du modèle, en utilisant les types de requêtes suivants.  
  
|Type de requête|Description|  
|----------------|-----------------|  
|Sélectionnez à partir de *\<model>* . PARFOIS|Retourne les cas utilisés pour l'apprentissage du modèle d'exploration de données.<br /><br /> Le domaine pour ce type de requête est le modèle d'exploration de données.<br /><br /> [Sélectionnez &#60;&#62; de modèle. CAS &#40;&#41;DMX ](../dmx/select-from-model-cases-dmx.md)<br /><br /> [Créer des requêtes d'extraction à l'aide de DMX](/analysis-services/data-mining/create-drillthrough-queries-using-dmx)|  
|Sélectionnez à partir de *\<model>* . SAMPLE_CASES|Retourne un exemple de cas, qui représente les cas utilisés pour l'apprentissage du modèle d'exploration de données.<br /><br /> Le domaine pour ce type de requête est le modèle d'exploration de données.<br /><br /> [Sélectionnez &#60;&#62; de modèle.&#41;SAMPLE_CASES &#40;DMX ](../dmx/select-from-model-sample-cases-dmx.md)|  
|Sélectionnez à partir de *\<structure>* . PARFOIS|Retourne des lignes de données détaillées de la structure d'exploration de données sous-jacente, même si certains détails n'ont pas été utilisés dans l'apprentissage du modèle d'exploration de données.<br /><br /> [Sélectionnez &#60;&#62; de structure. PARFOIS](../dmx/select-from-structure-cases.md)<br /><br /> [Requêtes d’extraction &#40;exploration de données&#41;](/analysis-services/data-mining/drillthrough-queries-data-mining)|  
  
 [Retour à Types SELECT](#Select_Types)  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)  
  
