---
description: SeekEnum
title: SeekEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SeekEnum
helpviewer_keywords:
- SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
author: rothja
ms.author: jroth
ms.openlocfilehash: e60bbc81f7b40dac7d1564a32f1e60eb8456c9bf
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777498"
---
# <a name="seekenum"></a>SeekEnum
Spécifie le type de [recherche](./seek-method.md) à exécuter.  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adSeekFirstEQ**|1|Recherche la première clé égale à *KeyValues*.|  
|**adSeekLastEQ**|2|Recherche la dernière clé égale à *KeyValues*.|  
|**adSeekAfterEQ**|4|Recherche une clé égale à *KeyValues* ou juste après l’emplacement où cette correspondance s’est produite.|  
|**adSeekAfter**|8|Recherche une clé juste après l’endroit où une correspondance avec *KeyValues* s’est produite.|  
|**adSeekBeforeEQ**|16|Recherche une clé égale à *KeyValues*ou juste avant l’emplacement où cette correspondance s’est produite.|  
|**adSeekBefore**|32|Recherche une clé juste avant l’endroit où une correspondance avec *KeyValues* s’est produite.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.Seek.FIRSTEQ|  
|AdoEnums.Seek.LASTEQ|  
|AdoEnums.Seek.AFTEREQ|  
|AdoEnums. Seek. après|  
|AdoEnums. Seek. BEFOREEQ|  
|AdoEnums.Seek.BEFORE|  
  
## <a name="applies-to"></a>S'applique à  
 [Seek, méthode](./seek-method.md)