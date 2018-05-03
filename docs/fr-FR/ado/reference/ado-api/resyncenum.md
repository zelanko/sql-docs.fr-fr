---
title: ResyncEnum | Documents Microsoft
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
- ResyncEnum
helpviewer_keywords:
- ResyncEnum enumeration [ADO]
ms.assetid: d3df2c90-e570-4c40-a79a-25b3448a009c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c755c31e055429c220742f35cef5f49ba8459870
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="resyncenum"></a>ResyncEnum
Indique si les valeurs sous-jacentes sont remplacées par un appel à [Resync](../../../ado/reference/ado-api/resync-method.md).  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|Valeur par défaut. Remplace les données et en attente de mises à jour sont annulées.|  
|**adResyncUnderlyingValues**|1|Ne remplace pas les données et en attente de mises à jour ne sont pas annulées.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.Resync.ALLVALUES|  
|AdoEnums.Resync.UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>S'applique à  
 [Resync, méthode](../../../ado/reference/ado-api/resync-method.md)
