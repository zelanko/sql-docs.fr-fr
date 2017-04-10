---
title: "&#201;diteur de destination de traitement de partition (page Avanc&#233;) | Microsoft Docs"
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
  - "sql13.dts.designer.partprocessingtransformation.advanced.f1"
helpviewer_keywords: 
  - "Éditeur de destination de traitement de partition"
ms.assetid: 2039ee0f-069d-479d-90b2-2a12481b1162
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# &#201;diteur de destination de traitement de partition (page Avanc&#233;)
  Utilisez la page **Avancé** de la boîte de dialogue **Éditeur de destination de traitement de partition** pour configurer la gestion des erreurs.  
  
 Pour en savoir plus sur la destination de traitement de partition, consultez [Partition Processing Destination](../../integration-services/data-flow/partition-processing-destination.md).  
  
> [!NOTE]  
>  Les tâches décrites ici ne s’appliquent pas aux modèles tabulaires Analysis Services.  Vous ne pouvez pas mapper des colonnes d’entrée aux colonnes de partition pour les modèles tabulaires. Vous pouvez en revanche utiliser la tâche DDL d'exécution [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) d'Analysis Services pour traiter la partition.  
  
## Options  
 **Utiliser la configuration d'erreur par défaut**  
 Indiquez si vous voulez utiliser la gestion des erreurs par défaut d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Par défaut, cette valeur est définie sur **True**.  
  
 **Action pour l'erreur de clé**  
 Indiquez comment traiter les enregistrements dont les valeurs de clé ne sont pas acceptables.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**ConvertToUnknown**|Convertir la valeur de clé non acceptable en valeur inconnue (Unknown).|  
|**DiscardRecord**|Ignorer l'enregistrement.|  
  
 **Ignorer les erreurs**  
 Spécifiez que les erreurs doivent être ignorées.  
  
 **Arrêter en cas d'erreur**  
 Spécifiez que le traitement doit s'arrêter lorsqu'une erreur se produit.  
  
 **Nombre d'erreurs**  
 Spécifiez le nombre maximal d’erreurs au-delà duquel le traitement doit s’arrêter, si vous avez sélectionné **Arrêter en cas d’erreur**.  
  
 **Action pour l'erreur**  
 Indiquez l’action à appliquer lorsque le nombre maximal d’erreurs est atteint, si vous avez sélectionné **Arrêter en cas d’erreur**.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**StopProcessing**|Arrêter le traitement.|  
|**StopLogging**|Arrêter d'enregistrer les erreurs.|  
  
 **Clé introuvable**  
 Indiquez l'action à appliquer en cas d'erreur de clé introuvable. Par défaut, cette valeur est définie sur **ReportAndContinue**.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignorer l'erreur et continuer le traitement.|  
|**ReportAndContinue**|Signaler l'erreur et continuer le traitement.|  
|**ReportAndStop**|Signaler l'erreur et arrêter le traitement.|  
  
 **Clé dupliquée**  
 Indiquez l'action à appliquer en cas d'erreur de clé dupliquée. Par défaut, cette valeur est définie sur **IgnoreError**.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignorer l'erreur et continuer le traitement.|  
|**ReportAndContinue**|Signaler l'erreur et continuer le traitement.|  
|**ReportAndStop**|Signaler l'erreur et arrêter le traitement.|  
  
 **Clé NULL convertie en clé inconnue**  
 Indiquez l'action à appliquer lorsqu'une clé NULL a été convertie en clé inconnue (Unknown). Par défaut, cette valeur est définie sur **IgnoreError**.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignorer l'erreur et continuer le traitement.|  
|**ReportAndContinue**|Signaler l'erreur et continuer le traitement.|  
|**ReportAndStop**|Signaler l'erreur et arrêter le traitement.|  
  
 **Clé NULL non autorisée**  
 Indiquez l'action à appliquer si une clé NULL est trouvée alors que les clés NULL ne sont pas autorisées. Par défaut, cette valeur est définie sur **ReportAndContinue**.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignorer l'erreur et continuer le traitement.|  
|**ReportAndContinue**|Signaler l'erreur et continuer le traitement.|  
|**ReportAndStop**|Signaler l'erreur et arrêter le traitement.|  
  
 **Chemin d'accès du journal des erreurs**  
 Tapez le chemin du journal des erreurs ou sélectionnez une destination à l’aide du bouton Parcourir **(...)**.  
  
 **Parcourir (...)**  
 Sélectionnez le chemin d'accès du journal des erreurs.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de destination de traitement de partition &#40;page Mappages&#41;](../../integration-services/data-flow/partition-processing-destination-editor-mappings-page.md)  
  
  