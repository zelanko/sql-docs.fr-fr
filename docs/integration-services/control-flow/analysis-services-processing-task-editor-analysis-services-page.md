---
title: "&#201;diteur de t&#226;che de traitement d&#39;Analysis Services (page Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.asprocessingtask.as.f1"
helpviewer_keywords: 
  - "Éditeur de tâche de traitement d'Analysis Services"
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# &#201;diteur de t&#226;che de traitement d&#39;Analysis Services (page Analysis Services)
  Utilisez la page **Analysis Services** de la boîte de dialogue **Éditeur de tâche de traitement d’Analysis Services** pour définir un gestionnaire de connexions Analysis Services, sélectionner les objets analytiques à traiter et définir les options de traitement et de gestion des erreurs.  
  
 Lors du traitement des modèles tabulaires, gardez à l'esprit les points suivants :  
  
1.  Vous ne pouvez pas effectuer d'analyse d'impact sur les modèles tabulaires.  
  
2.  Certaines options de traitement du mode tabulaire ne sont pas exposées, par exemple Traiter la défragmentation et Traiter le recalcul. Vous pouvez exécuter ces fonctions à l'aide de la tâche DDL d'exécution.  
  
3.  Certaines options de traitement fournies, par exemple le traitement des index, ne conviennent pas aux modèles tabulaires et ne doivent pas être utilisées.  
  
4.  Les paramètres de lot sont ignorés pour les modèles tabulaires.  
  
 Pour en savoir plus sur cette tâche, consultez [Tâche de traitement d’Analysis Services](../../integration-services/control-flow/analysis-services-processing-task.md).  
  
## Options  
 **Gestionnaire de connexions Analysis Services**  
 Sélectionnez un gestionnaire de connexions Analysis Services existant dans la liste ou cliquez sur **Nouveau** pour créer un nouveau gestionnaire de connexions.  
  
 **Nouveau**  
 Créez un nouveau gestionnaire de connexions Analysis Services.  
  
 **Rubriques connexes :** [Gestionnaire de connexions Analysis Services](../../integration-services/connection-manager/analysis-services-connection-manager.md), [Référence de l’interface utilisateur de la boîte de dialogue Ajout d’un gestionnaire de connexions Analysis Services](../../integration-services/connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 **Liste d'objets**  
 |Propriété|Description|  
|--------------|-----------------|  
|**Nom de l'objet**|Affiche la liste des noms d'objets définis.|  
|**Type**|Affiche la liste des types des objets définis.|  
|**Options de traitement**|Sélectionnez une option de traitement dans la liste.<br /><br /> **Rubriques connexes** : [Traitement d’un modèle multidimensionnel &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)|  
|**Paramètres**|Affiche la liste des paramètres de traitement des objets définis.|  
  
 **Ajouter**  
 Ajoutez un objet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à la liste.  
  
 **Supprimer**  
 Sélectionnez un objet et cliquez sur **Supprimer**.  
  
 **Analyse d'impact**  
 Analyse l'impact sur l'objet sélectionné.  
  
 **Rubriques connexes :** [Boîte de dialogue Analyse d’impact &#40;Analysis Services - Données multidimensionnelles&#41;](../Topic/Impact%20Analysis%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
 **Résumé des paramètres du traitement**  
 |Propriété|Description|  
|--------------|-----------------|  
|**Ordre de traitement**|Indique si les objets sont traités séquentiellement ou dans un traitement. Si le traitement parallèle est utilisé, indique le nombre d'objets à traiter simultanément.|  
|**Mode de transaction**|Indique le mode de transaction du traitement séquentiel.|  
|**Erreurs de la dimension**|Indique le comportement de la tâche lorsqu'une erreur se produit.|  
|**Chemin d'accès du journal des erreurs de clé de dimension**|Définit le chemin d'accès du fichier de consignation des erreurs.|  
|**Traiter les objets affectés**|Indique si les objets dépendants ou affectés sont également traités.|  
  
 **Modifier les paramètres**  
 Change les options de traitement et la gestion des erreurs dans les clés de dimension.  
  
 **Rubriques connexes :** [Boîte de dialogue Modifier les paramètres &#40;Analysis Services - Données multidimensionnelles&#41;](../Topic/Change%20Settings%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de traitement d’Analysis Services &#40;page Général&#41;](../../integration-services/control-flow/analysis-services-processing-task-editor-general-page.md)   
 [Tâche DDL d'exécution de SQL Server Analysis Services](../../integration-services/control-flow/analysis-services-execute-ddl-task.md)  
  
  