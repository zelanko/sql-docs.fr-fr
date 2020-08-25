---
description: PersistFormatEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: d4f83189a241b396cba613d9df0d6c0b1aa1328e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88773218"
---
# <a name="persistformatenum"></a>PersistFormatEnum
Spécifie le format d’enregistrement d’un [jeu d’enregistrements](./recordset-object-ado.md).  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Indique le format Microsoft Advanced Data TableGram (ADTG).|  
|**adPersistADO**|1|Indique que le format XML (XML) Extensible Markup Language est utilisé par ADO. Cette valeur est identique à adPersistXML et est incluse à des fins de compatibilité descendante.|  
|**adPersistXML**|1|Indique le format Extensible Markup Language (XML).|  
|**adPersistProviderSpecific**|2|Indique que le fournisseur conserve le **Recordset** à l’aide de son propre format.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>S'applique à  
 [Save, méthode](./save-method.md)