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
ms.openlocfilehash: c379ca2a3f68b195c0020d0e89009d2715da5850
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442251"
---
# <a name="resyncenum"></a>ResyncEnum
Spécifie si les valeurs sous-jacentes sont remplacées par un appel à [Resync](../../../ado/reference/ado-api/resync-method.md).  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|Par défaut. Remplace les données, et les mises à jour en attente sont annulées.|  
|**adResyncUnderlyingValues**|1|Ne remplace pas les données et les mises à jour en attente ne sont pas annulées.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constante|  
|--------------|  
|AdoEnums.Resync.ALLVALUES|  
|AdoEnums.Resync.UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>S'applique à  
 [Resync, méthode](../../../ado/reference/ado-api/resync-method.md)
