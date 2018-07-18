---
title: Analysis Services à l’éditeur de tâche de traitement (Page Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.as.f1
helpviewer_keywords:
- Analysis Services Processing Task Editor
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a131a7a25e9539eac5d7090508e3b67aa79fd9a1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187186"
---
# <a name="analysis-services-processing-task-editor-analysis-services-page"></a>Éditeur de tâche de traitement d'Analysis Services (page Analysis Services)
  Utilisez la page **Analysis Services** de la boîte de dialogue **Éditeur de tâche de traitement d’Analysis Services** pour définir un gestionnaire de connexions Analysis Services, sélectionner les objets analytiques à traiter et définir les options de traitement et de gestion des erreurs.  
  
 Lors du traitement des modèles tabulaires, gardez à l'esprit les points suivants :  
  
1.  Vous ne pouvez pas effectuer d'analyse d'impact sur les modèles tabulaires.  
  
2.  Certaines options de traitement du mode tabulaire ne sont pas exposées, par exemple Traiter la défragmentation et Traiter le recalcul. Vous pouvez exécuter ces fonctions à l'aide de la tâche DDL d'exécution.  
  
3.  Certaines options de traitement fournies, par exemple le traitement des index, ne conviennent pas aux modèles tabulaires et ne doivent pas être utilisées.  
  
4.  Les paramètres de lot sont ignorés pour les modèles tabulaires.  
  
 Pour en savoir plus sur cette tâche, consultez [Tâche de traitement d’Analysis Services](control-flow/analysis-services-processing-task.md).  
  
## <a name="options"></a>Options  
 **Gestionnaire de connexions Analysis Services**  
 Sélectionnez un gestionnaire de connexions Analysis Services existant dans la liste ou cliquez sur **Nouveau** pour créer un nouveau gestionnaire de connexions.  
  
 **Nouveau**  
 Créez un nouveau gestionnaire de connexions Analysis Services.  
  
 **Rubriques connexes :** [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md), [Référence de l’interface utilisateur de la boîte de dialogue Ajout d’un gestionnaire de connexions Analysis Services](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 **Liste d'objets**  
 |Propriété|Description|  
|--------------|-----------------|  
|**Nom de l'objet**|Affiche la liste des noms d'objets définis.|  
|**Type**|Affiche la liste des types des objets définis.|  
|**Options de traitement**|Sélectionnez une option de traitement dans la liste.<br /><br /> **Rubriques connexes**: [traitement des objets de modèle multidimensionnel](../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)|  
|**Paramètres**|Affiche la liste des paramètres de traitement des objets définis.|  
  
 **Ajouter**  
 Ajoutez un objet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à la liste.  
  
 **Supprimer**  
 Sélectionnez un objet et cliquez sur **Supprimer**.  
  
 **Analyse d'impact**  
 Analyse l'impact sur l'objet sélectionné.  
  
 **Rubriques connexes :** [Boîte de dialogue Analyse d’impact &#40;Analysis Services - Données multidimensionnelles&#41;](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)  
  
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
  
 **Rubriques connexes :** [Boîte de dialogue Modifier les paramètres &#40;Analysis Services - Données multidimensionnelles&#41;](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de traitement de Analysis Services &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Tâche DDL d’exécution de SQL Server Analysis Services](control-flow/analysis-services-execute-ddl-task.md)  
  
  
