---
title: PersistFormatEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9c981037637b85e23e6b871116291aa8eb607c99
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="persistformatenum"></a>PersistFormatEnum
Spécifie le format dans lequel enregistrer un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Indique le format Microsoft Advanced Data TableGram (ADTG).|  
|**adPersistADO**|1|Indique que le format Extensible Markup Language (XML) de d’ADO sera utilisé. Cette valeur est identique à adPersistXML et est inclus pour des raisons de compatibilité descendante.|  
|**adPersistXML**|1|Indique le format de langage XML (Extensible Markup).|  
|**adPersistProviderSpecific**|2|Indique que le fournisseur maintient la **Recordset** à l’aide de son propre format.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>S'applique à  
 [Save (méthode)](../../../ado/reference/ado-api/save-method.md)

