---
title: "Propri&#233;t&#233;s personnalis&#233;es de la destination de traitement de dimension | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
caps.latest.revision: 6
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 6
---
# Propri&#233;t&#233;s personnalis&#233;es de la destination de traitement de dimension
  La destination de traitement de dimension comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination de traitement de dimension. Toutes les propriétés sont en lecture/écriture.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|Chaîne|Chaîne de connexion d'une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les erreurs de clé en double. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **IgnoreError** (0).|  
|KeyErrorAction|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les erreurs de clé. Les valeurs possibles sont **ConvertToUnknown** (0) et **DiscardRecord** (1). La valeur par défaut de cette propriété est **ConvertToUnknown** (0).|  
|KeyErrorLimit|Entier|Quand UseDefaultConfiguration a la valeur **False**, limite supérieure des erreurs de clé activées.|  
|KeyErrorLimitAction|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique l’action à entreprendre quand la limite **KeyErrorLimit** est atteinte. Les valeurs possibles sont **StopLogging** (1) et **StopProcessing** (0). La valeur par défaut de cette propriété est **StopProcessing** (0).|  
|KeyErrorLogFile|Chaîne|Quand UseDefaultConfiguration a la valeur **False**, chemin et nom du fichier journal des erreurs.|  
|KeyNotFound|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les erreurs de clé manquante. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **IgnoreError** (0).|  
|NullKeyConvertedToUnknown|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les clés null converties en valeur inconnue. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **IgnoreError** (0).|  
|NullKeyNotAllowed|Integer (énumération)|Quand UseDefaultConfiguration a la valeur **False**, valeur qui indique comment gérer les clés null non autorisées. Les valeurs possibles sont **IgnoreError** (0), **ReportAndContinue** (1) et **ReportAndStop** (2). La valeur par défaut de cette propriété est **IgnoreError** (0).|  
|ProcessType|Integer (énumération)|Type de traitement de dimension que la transformation utilise. Les valeurs sont **ProcessAdd** (1) (incrémentiel), **ProcessFull** (0) et **ProcessUpdate** (2).|  
|UseDefaultConfiguration|Booléen|Valeur qui spécifie si la transformation utilise la configuration d'erreur par défaut. Si cette propriété a la valeur **False**, la transformation inclut des informations sur le traitement des erreurs.|  
  
 L'entrée et les colonnes d'entrée de la destination de traitement de dimension ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination de traitement de dimension](../../integration-services/data-flow/dimension-processing-destination.md).  
  
## Voir aussi  
 [Propriétés communes](../Topic/Common%20Properties.md)  
  
  