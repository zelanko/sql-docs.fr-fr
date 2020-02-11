---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4a872ee5f4af49d9fbe97621a5d2549fd9472202
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931239"
---
# <a name="resyncenum"></a>ResyncEnum
Spécifie si les valeurs sous-jacentes sont remplacées par un appel à [Resync](../../../ado/reference/ado-api/resync-method.md).  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|valeur par défaut. Remplace les données, et les mises à jour en attente sont annulées.|  
|**adResyncUnderlyingValues**|1|Ne remplace pas les données et les mises à jour en attente ne sont pas annulées.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.Resync.ALLVALUES|  
|AdoEnums.Resync.UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>S'applique à  
 [Resync, méthode](../../../ado/reference/ado-api/resync-method.md)
