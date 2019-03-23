---
title: Propriétés personnalisées de la destination de traitement de partition | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3dbab24f756498d7427f9961e4176249daac8dfb
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385057"
---
# <a name="partition-processing-destination-custom-properties"></a>Propriétés personnalisées de la destination de traitement de partition
  La destination de traitement de partition comporte à la fois des propriétés personnalisées et les propriétés communes à l'ensemble des composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination de traitement de partition. Toutes les propriétés sont en lecture/écriture.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Chaîne de connexion d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou d'une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Integer (énumération)|Quand UseDefaultConfiguration a la valeur `False`, une valeur qui indique comment gérer les erreurs de clé dupliquée. Les valeurs possibles sont `IgnoreError` (0), `ReportAndContinue` (1) et `ReportAndStop` (2). La valeur par défaut de cette propriété est `IgnoreError` (0).|  
|KeyErrorAction|Integer (énumération)|Quand UseDefaultConfiguration a la valeur `False`, une valeur qui indique comment gérer les erreurs de clé. Les valeurs possibles sont `ConvertToUnknown` (0) et `DiscardRecord` (1). La valeur par défaut de cette propriété est `ConvertToUnknown` (0).|  
|KeyErrorLimit|Entier|Quand UseDefaultConfiguration a la valeur `False`, la limite supérieure des erreurs de clé sont autorisés.|  
|KeyErrorLimitAction|Integer (énumération)|Quand UseDefaultConfiguration a `False`, une valeur qui indique l’action à entreprendre lorsque `KeyErrorLimit` est atteinte. Les valeurs possibles sont `StopLogging` (1) et `StopProcessing` (0). La valeur par défaut de cette propriété est `StopProcessing` (0).|  
|KeyErrorLogFile|String|Quand UseDefaultConfiguration a la valeur `False`, le chemin d’accès et le nom de fichier de journal des erreurs.|  
|KeyNotFound|Integer (énumération)|Quand UseDefaultConfiguration a la valeur `False`, une valeur qui indique comment gérer des erreurs de clé manquant. Les valeurs possibles sont `IgnoreError` (0), `ReportAndContinue` (1) et `ReportAndStop` (2). La valeur par défaut de cette propriété est `ReportAndContinue` (1).|  
|NullKeyConvertedToUnknown|Integer (énumération)|Quand UseDefaultConfiguration a la valeur `False`, une valeur qui indique comment gérer les clés null converties en valeur inconnue. Les valeurs possibles sont `IgnoreError` (0), `ReportAndContinue` (1) et `ReportAndStop` (2). La valeur par défaut de cette propriété est `IgnoreError` (0).|  
|NullKeyNotAllowed|Integer (énumération)|Quand UseDefaultConfiguration a la valeur `False`, une valeur qui indique comment gérer les clés NULL. Les valeurs possibles sont `IgnoreError` (0), `ReportAndContinue` (1) et `ReportAndStop` (2). La valeur par défaut de cette propriété est `ReportAndContinue` (1).|  
|ProcessType|Integer (énumération)|Type de traitement de partition que la transformation utilise. Les valeurs possibles sont `ProcessAdd` (1) (incrémentiel), `ProcessFull` (0) et `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Booléen|Valeur qui spécifie si la transformation utilise la configuration d'erreur par défaut. Si cette propriété est `False`, la transformation utilise les valeurs des propriétés de la gestion des erreurs personnalisées répertoriées dans ce tableau, notamment KeyDuplicate, KeyErrorAction et ainsi de suite.|  
  
 L'entrée et les colonnes d'entrée de la destination de traitement de partition ne disposent pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination de traitement de partition](partition-processing-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](../common-properties.md)  
  
  
