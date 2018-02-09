---
title: SeekEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- SeekEnum
helpviewer_keywords:
- SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 40c15bd116b4e0a7ba13127dc48ec18421b5924b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="seekenum"></a>SeekEnum
Spécifie le type de [recherche](../../../ado/reference/ado-api/seek-method.md) à exécuter.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adSeekFirstEQ**|1|Recherche la première clé égale à *KeyValues*.|  
|**adSeekLastEQ**|2|Recherche la dernière clé égale à *KeyValues*.|  
|**adSeekAfterEQ**|4|Recherche soit une clé égale à *KeyValues* ou juste après l’où cette correspondance.|  
|**adSeekAfter**|8|Recherche une clé juste après l’emplacement où une correspondance avec *KeyValues* auraient eu lieu.|  
|**adSeekBeforeEQ**|16|Recherche soit une clé égale à *KeyValues*ou juste avant l’emplacement qui correspondent.|  
|**adSeekBefore**|32|Recherche une clé juste avant où une correspondance avec *KeyValues* auraient eu lieu.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.Seek.FIRSTEQ|  
|AdoEnums.Seek.LASTEQ|  
|AdoEnums.Seek.AFTEREQ|  
|AdoEnums.Seek.AFTER|  
|AdoEnums.Seek.BEFOREEQ|  
|AdoEnums.Seek.BEFORE|  
  
## <a name="applies-to"></a>S'applique à  
 [Seek, méthode](../../../ado/reference/ado-api/seek-method.md)
