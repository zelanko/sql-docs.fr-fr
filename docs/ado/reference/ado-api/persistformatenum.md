---
title: PersistFormatEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 851106109d195ae6f5d6f66d3944e486d58504c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63027841"
---
# <a name="persistformatenum"></a>PersistFormatEnum
Spécifie le format dans lequel enregistrer un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Indique le format Microsoft Advanced Data TableGram (ADTG).|  
|**adPersistADO**|1|Indique que le format de langage XML (Extensible Markup) de ADO sera utilisé. Cette valeur est identique à adPersistXML et est inclus pour des raisons de compatibilité descendante.|  
|**adPersistXML**|1|Indique le format du langage XML (Extensible Markup).|  
|**adPersistProviderSpecific**|2|Indique que le fournisseur maintient la **Recordset** à l’aide de son propre format.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>S'applique à  
 [Save, méthode](../../../ado/reference/ado-api/save-method.md)
