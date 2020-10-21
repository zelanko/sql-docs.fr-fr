---
description: Propriétés personnalisées de la destination de traitement de dimension
title: Propriétés personnalisées de la destination de traitement de dimension | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7e6959edde524e2219573793b5becb34f5d63f1c
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92192719"
---
# <a name="dimension-processing-destination-custom-properies"></a>Propriétés personnalisées de la destination de traitement de dimension

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  La destination de traitement de dimension comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination de traitement de dimension. Toutes les propriétés sont en lecture/écriture.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Chaîne de connexion d'une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|KeyDuplicate|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les erreurs de clé en double. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **IgnoreError** (0).|  
|KeyErrorAction|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les erreurs de clé. Les valeurs possibles sont **ConvertToUnknown** (0) et **DiscardRecord** (1). La valeur par défaut de cette propriété est **ConvertToUnknown** (0).|  
|KeyErrorLimit|Integer|Quand UseDefaultConfiguration a la valeur **False**, limite supérieure des erreurs de clé activées.|  
|KeyErrorLimitAction|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique l’action à entreprendre quand la limite **KeyErrorLimit** est atteinte. Les valeurs possibles sont **StopLogging** (1) et **StopProcessing** (0). La valeur par défaut de cette propriété est **StopProcessing** (0).|  
|KeyErrorLogFile|String|Quand UseDefaultConfiguration a la valeur **False**, chemin et nom du fichier journal des erreurs.|  
|KeyNotFound|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les erreurs de clé manquante. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **IgnoreError** (0).|  
|NullKeyConvertedToUnknown|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les clés null converties en valeur inconnue. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **IgnoreError** (0).|  
|NullKeyNotAllowed|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les clés null non autorisées. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **IgnoreError** (0).|  
|ProcessType|Integer (énumération)|Type de traitement de dimension que la transformation utilise. Les valeurs sont **ProcessAdd** (1) (incrémentiel), **ProcessFull** (0) et **ProcessUpdate** (2).|  
|UseDefaultConfiguration|Booléen|Valeur qui spécifie si la transformation utilise la configuration d'erreur par défaut. Si cette propriété a la valeur **False**, la transformation inclut des informations sur le traitement des erreurs.|  
  
 L'entrée et les colonnes d'entrée de la destination de traitement de dimension ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination de traitement de dimension](../../integration-services/data-flow/dimension-processing-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](./set-the-properties-of-a-data-flow-component.md)  
  
