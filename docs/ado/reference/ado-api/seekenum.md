---
title: SeekEnum | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SeekEnum
helpviewer_keywords:
- SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f61e71b03a05a8e13c1b069e4880f362ff0985a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281588"
---
# <a name="seekenum"></a>SeekEnum
Spécifie le type de [recherche](../../../ado/reference/ado-api/seek-method.md) à exécuter.  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adSeekFirstEQ**| 1|Recherche la première clé égale à *KeyValues*.|  
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
