---
title: "Extraction sur des mod&#232;les d&#39;exploration de donn&#233;es | Microsoft Docs"
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
ms.assetid: f179a467-7d03-4d61-8e9a-6b5afb5fc2d5
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 8
---
# Extraction sur des mod&#232;les d&#39;exploration de donn&#233;es
  *L'extraction* désigne la capacité d'interroger un modèle d'exploration de données ou une structure d'exploration de données pour obtenir des informations détaillées qui ne sont pas exposées dans le modèle.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] fournit deux options différentes pour l'extraction des données de cas. Vous pouvez extraire les cas utilisés pour générer les données ou les cas de la structure d'exploration de données.  
  
## Extraction dans des cas de modèle et dans la structure  
 L'extraction dans des **cas de modèle** est utile pour rechercher des informations supplémentaires sur les règles, les modèles ou les clusters dans un modèle. Par exemple, vous n'utiliseriez pas les informations de contact client pour une analyse dans un modèle de clustering, même si les données étaient disponibles, mais à l'aide de l'extraction, vous pouvez accéder à ces informations à partir du modèle.  
  
 Par opposition, **l'extraction dans les données de la structure** est conçue pour fournir un accès aux informations qui n'ont pas été mises à disposition dans le modèle. Par exemple, certaines colonnes de structure peuvent avoir été exclues d'un modèle, car le type de données était incompatible ou les données ne présentaient aucune utilité pour l'analyse.  
  
## Activation de l'extraction sur un modèle  
 Pour utiliser l'extraction sur un modèle d'exploration de données, les conditions suivantes doivent être remplies :  
  
-   Il est possible de configurer l'extraction sur les cas du modèle uniquement et pas sur la structure d'exploration de données, mais pas vice versa.  En d'autres termes, l'extraction doit être activée sur le modèle d'exploration de données pour autoriser l'extraction à la structure d'exploration de données.  
  
-   L'extraction sur le modèle et la structure est désactivée par défaut. Si vous utilisez l'Assistant Exploration de données, l'option d'activation de l'extraction vers les cas de modèles figure sur la dernière page de l'Assistant.  
  
-   Vous pouvez ajouter la capacité d'extraire un modèle existant d'exploration de données, mais si vous procédez ainsi, le modèle doit être retraité avant que vous ne puissiez extraire les données.  
  
-   L'extraction ne fonctionnera pas à moins que le cache créé au cours du processus d'apprentissage n'ait été conservé. Pour plus d’informations sur les propriétés qui contrôlent la mise en cache, consultez [Extraction sur des structures d’exploration de données](../../analysis-services/data-mining/drillthrough-on-mining-structures.md).  
  
## Modèles qui prennent en charge l'extraction  
 Si un modèle d'exploration de données a été configuré pour autoriser l'extraction, et si vous disposez des autorisations appropriées, lorsque vous parcourez le modèle, vous pouvez cliquer sur un nœud dans la visionneuse appropriée et récupérer des informations détaillées sur les cas de ce nœud particulier.  
  
 Les modèles ne prennent pas tous en charge l'extraction ; cela dépend de l'algorithme qui a été utilisé pour créer le modèle. Le tableau suivant répertorie les types de modèles qui ne prennent pas en charge l'extraction, ou qui la prennent en charge sous certaines conditions. Si le type de modèle n'est pas répertorié ici, l'extraction est prise en charge.  
  
|**Nom de l'algorithme**|**Prise en charge de l’extraction**|  
|------------------------|----------------------------------|  
|Algorithme MNB (Microsoft Naive Bayes)|Non pris en charge.<br /><br /> Ces algorithmes n'assignent pas de cas aux nœuds spécifiques du contenu.|  
|Algorithme MNN (Microsoft Neural Network)|Non pris en charge.<br /><br /> Ces algorithmes n'assignent pas de cas aux nœuds spécifiques du contenu.|  
|Algorithme MLR (Microsoft Logistic Regression)|Non pris en charge.<br /><br /> Ces algorithmes n'assignent pas de cas aux nœuds spécifiques du contenu.|  
|Algorithme MLR (Microsoft Linear Regression)|Pris en charge.<br /><br /> Toutefois, comme le modèle crée un nœud unique, **All**, l'extraction retourne tous les cas d'apprentissage pour le modèle. Si le jeu d'apprentissage est volumineux, le chargement des résultats peut durer plusieurs minutes.|  
|Algorithme MTS (Microsoft Time Series)|Pris en charge.<br /><br /> Toutefois, vous ne pouvez pas extraire les données de structure ou de cas en utilisant la **Visionneuse de modèle d'exploration de données** dans le Concepteur de modèle d'exploration de données. Vous devez créer à la place une requête DMX.<br /><br /> De même, vous ne pouvez pas extraire des nœuds spécifiques ni écrire une requête DMX pour récupérer les cas de nœuds spécifiques d'un modèle de série chronologique. Vous pouvez récupérer les données de cas depuis le modèle ou la structure en utilisant d'autres critères, comme les valeurs de date ou d'attribut.<br /><br /> Si vous voulez consulter les détails des nœuds ARTXP et ARIMA créés par l’algorithme MTS (Microsoft Time Series), il vous sera peut-être plus simple d’utiliser la [Visionneuse de l’arborescence de contenu générique Microsoft &#40;exploration de données&#41;](../Topic/Microsoft%20Generic%20Content%20Tree%20Viewer%20\(Data%20Mining\).md).|  
  
## Tâches associées  
 Consultez les rubriques suivantes pour plus d'informations sur l'utilisation de l'extraction avec des modèles d'exploration de données.  
  
|Tâches|Liens|  
|-----------|-----------|  
|Utiliser l'extraction dans les visionneuses de modèle d'exploration de données|[Utiliser l'extraction des visionneuses de modèle](../../analysis-services/data-mining/use-drillthrough-from-the-model-viewers.md)|  
|Récupérer les données de cas pour un modèle à l'aide de l'extraction|[Extraire des données de cas à partir d'un modèle d'exploration de données](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)|  
|Activer l'extraction sur un modèle d'exploration de données existant|[Activer l'extraction pour un modèle d'exploration de données](../../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)|  
|Consulter les exemples de requêtes d'extraction pour les types de modèles spécifiques.|[Requêtes d'exploration de données](../../analysis-services/data-mining/data-mining-queries.md)|  
|Activer l'extraction dans l'Assistant Modèle d'exploration de données|[Fin de l’Assistant &#40;Assistant Exploration de données&#41;](../Topic/Completing%20the%20Wizard%20\(Data%20Mining%20Wizard\).md).|  
  
## Voir aussi  
 [Extraction sur des structures d'exploration de données](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  