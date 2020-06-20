---
title: Éditeur de destination de traitement de dimension (page avancé) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.advanced.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 2b30835a-2680-4d98-89a4-4f17e29e3818
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 5bef21b424c401d77b9d8f3477de4061c3ff0f3d
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966956"
---
# <a name="dimension-processing-destination-editor-advanced-page"></a>Éditeur de destination de traitement de dimension (page Avancé)
  Utilisez la page **Avancé** de la boîte de dialogue **Éditeur de destination de traitement de dimension** pour configurer la gestion des erreurs.  
  
 Pour en savoir plus sur la destination de traitement de dimension, consultez [Dimension Processing Destination](data-flow/dimension-processing-destination.md).  
  
## <a name="options"></a>Options  
 **Utiliser la configuration d'erreur par défaut**  
 Indiquez si vous voulez utiliser la gestion des erreurs par défaut d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Par défaut, cette valeur est `True`.  
  
 **Action de l’erreur de clé**  
 Indiquez comment traiter les enregistrements dont les valeurs de clé ne sont pas acceptables.  
  
|Value|Description|  
|-----------|-----------------|  
|**ConvertToUnknown**|Convertir la valeur de clé non acceptable en valeur `UnknownMember`.|  
|**DiscardRecord**|Ignorer l'enregistrement.|  
  
 **Ignorer les erreurs**  
 Spécifiez que les erreurs doivent être ignorées.  
  
 **Arrêter en cas d’erreur**  
 Spécifiez que le traitement doit s'arrêter lorsqu'une erreur se produit.  
  
 **Nombre d’erreurs**  
 Spécifiez le seuil d’erreurs au-delà duquel le traitement doit s’arrêter, si vous avez sélectionné **Arrêter en cas d’erreur**.  
  
 **Action pour l'erreur**  
 Indiquez l’action à appliquer quand le seuil d’erreurs est atteint, si vous avez sélectionné **Arrêter en cas d’erreur**.  
  
|Value|Description|  
|-----------|-----------------|  
|**StopProcessing**|Arrêter le traitement.|  
|**StopLogging**|Arrêter d'enregistrer les erreurs.|  
  
 **Clé introuvable**  
 Indiquez l'action à appliquer en cas d'erreur de clé introuvable. Par défaut, cette valeur est définie sur **ReportAndContinue**.  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignorer l'erreur et continuer le traitement.|  
|**ReportAndContinue**|Signaler l'erreur et continuer le traitement.|  
|**ReportAndStop**|Signaler l'erreur et arrêter le traitement.|  
  
 **Clé dupliquée**  
 Indiquez l'action à appliquer en cas d'erreur de clé dupliquée. Par défaut, cette valeur est définie sur **IgnoreError**.  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignorer l'erreur et continuer le traitement.|  
|**ReportAndContinue**|Signaler l'erreur et continuer le traitement.|  
|**ReportAndStop**|Signaler l'erreur et arrêter le traitement.|  
  
 **Clé NULL convertie en clé inconnue**  
 Indiquez l'action à appliquer lorsqu'une clé NULL a été convertie en clé `UnknownMember`. Par défaut, cette valeur est définie sur **IgnoreError**.  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignorer l'erreur et continuer le traitement.|  
|**ReportAndContinue**|Signaler l'erreur et continuer le traitement.|  
|**ReportAndStop**|Signaler l'erreur et arrêter le traitement.|  
  
 **Clé NULL non autorisée**  
 Indiquez l'action à appliquer si une clé NULL est trouvée alors que les clés NULL ne sont pas autorisées. Par défaut, cette valeur est définie sur **ReportAndContinue**.  
  
|Value|Description|  
|-----------|-----------------|  
|**IgnoreError**|Ignorer l'erreur et continuer le traitement.|  
|**ReportAndContinue**|Signaler l'erreur et continuer le traitement.|  
|**ReportAndStop**|Signaler l'erreur et arrêter le traitement.|  
  
 **Chemin d'accès du journal des erreurs**  
 Tapez le chemin du journal des erreurs ou cliquez sur le bouton **Parcourir (...)** pour sélectionner une destination.  
  
 **Parcourir (...)**  
 Sélectionnez le chemin d'accès du journal des erreurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de destination de traitement de dimension &#40;page Gestionnaire de connexions&#41;](../../2014/integration-services/dimension-processing-destination-editor-connection-manager-page.md)   
 [Éditeur de destination de traitement de dimension &#40;page Mappages&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)  
  
  
