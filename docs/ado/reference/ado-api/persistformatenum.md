---
title: PersistFormatEnum | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4d0c825f6f1cd8f1d6040e1752f21a4a10f48f42
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
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
 [Save, méthode](../../../ado/reference/ado-api/save-method.md)
