---
description: ResyncEnum
title: ResyncEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ResyncEnum
helpviewer_keywords:
- ResyncEnum enumeration [ADO]
ms.assetid: d3df2c90-e570-4c40-a79a-25b3448a009c
author: rothja
ms.author: jroth
ms.openlocfilehash: addaaa07b14b88ed7d72714ba8698da1f2ef2ac9
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777638"
---
# <a name="resyncenum"></a>ResyncEnum
Spécifie si les valeurs sous-jacentes sont remplacées par un appel à [Resync](./resync-method.md).  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|Par défaut. Remplace les données, et les mises à jour en attente sont annulées.|  
|**adResyncUnderlyingValues**|1|Ne remplace pas les données et les mises à jour en attente ne sont pas annulées.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.Resync.ALLVALUES|  
|AdoEnums.Resync.UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>S'applique à  
 [Resync, méthode](./resync-method.md)