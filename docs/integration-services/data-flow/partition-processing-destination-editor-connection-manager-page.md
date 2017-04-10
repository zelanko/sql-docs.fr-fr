---
title: "&#201;diteur de destination de traitement de partition (page Gestionnaire de connexions) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.partprocessingtransformation.connection.f1"
helpviewer_keywords: 
  - "Éditeur de destination de traitement de partition"
ms.assetid: 7add6f82-eed1-47fc-a5d7-7b91f3f24d34
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# &#201;diteur de destination de traitement de partition (page Gestionnaire de connexions)
  La page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination de traitement de partition** vous permet de spécifier une connexion à un projet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou à une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Pour en savoir plus sur la destination de traitement de partition, consultez [Partition Processing Destination](../../integration-services/data-flow/partition-processing-destination.md).  
  
> [!NOTE]  
>  Les tâches décrites ici ne s’appliquent pas aux modèles tabulaires Analysis Services.  Vous ne pouvez pas mapper des colonnes d’entrée aux colonnes de partition pour les modèles tabulaires. Vous pouvez en revanche utiliser la tâche DDL d'exécution [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) d'Analysis Services pour traiter la partition.  
  
## Options  
 **Gestionnaire de connexions**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une nouvelle connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez une connexion via la boîte de dialogue **Ajout d’un gestionnaire de connexions Analysis Services**.  
  
 **Liste des partitions disponibles**  
 Sélectionnez la partition à traiter.  
  
 **Méthode de traitement**  
 Sélectionnez la méthode de traitement. La valeur par défaut de cette option est **Complète**.  
  
|Value|Description|  
|-----------|-----------------|  
|Ajouter (incrémentiel)|Permet d'effectuer un traitement incrémentiel de la partition.|  
|Complet|Permet d'effectuer un traitement complet de la partition.|  
|Données seulement|Permet d'effectuer un traitement de mise à jour de la partition.|  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de destination de traitement de partition &#40;page Mappages&#41;](../../integration-services/data-flow/partition-processing-destination-editor-mappings-page.md)   
 [Éditeur de destination de traitement de partition &#40;page Avancé&#41;](../../integration-services/data-flow/partition-processing-destination-editor-advanced-page.md)  
  
  