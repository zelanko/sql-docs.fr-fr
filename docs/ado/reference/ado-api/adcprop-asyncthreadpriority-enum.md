---
description: ADCPROP_ASYNCTHREADPRIORITY_ENUM
title: ADCPROP_ASYNCTHREADPRIORITY_ENUM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
author: rothja
ms.author: jroth
ms.openlocfilehash: 446a220868a2cf0b0a518bde95897b9d1f41a3b3
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88760274"
---
# <a name="adcprop_asyncthreadpriority_enum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Pour un objet [Recordset](./recordset-object-ado.md) RDS, spécifie la priorité d’exécution du thread asynchrone qui récupère les données.  
  
 Utilisez ces constantes avec la propriété dynamique «**priorité des threads d’arrière-plan**» du **jeu d’enregistrements** , qui est référencée dans l’index de propriété dynamique ADO-to-OLE DB et documentée dans la documentation du [Service de curseur Microsoft pour OLE DB](../../guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) .  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adPriorityAboveNormal**|4|Définit la priorité entre le paramètre normal et le niveau le plus élevé.|  
|**adPriorityBelowNormal**|2|Définit la priorité entre le niveau le plus bas et le niveau normal.|  
|**adPriorityHighest**|5|Définit la priorité sur la valeur la plus élevée possible.|  
|**AdPriorityLowest**|1|Définit la priorité sur la valeur la plus faible possible.|  
|**adPriorityNormal**|3|Définit la priorité sur normal.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constante|  
|--------------|  
|AdoEnums.AdcPropAsyncThreadPriority.ABOVENORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.BELOWNORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.HIGHEST|  
|AdoEnums.AdcPropAsyncThreadPriority.LOWEST|  
|AdoEnums.AdcPropAsyncThreadPriority.NORMAL|