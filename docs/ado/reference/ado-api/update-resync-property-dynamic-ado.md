---
description: Update Resync, propriété dynamique (ADO)
title: Update Resync, propriété dynamique (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Update Resync property [ADO]
ms.assetid: 8a3bb608-66d7-4128-a3ef-84cb0556de0d
author: rothja
ms.author: jroth
ms.openlocfilehash: 52884baca793ae9f5cb7b849c9f50d2399f0cf5e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777008"
---
# <a name="update-resync-property-dynamic-ado"></a>Update Resync, propriété dynamique (ADO)
Spécifie si la méthode [UpdateBatch](./updatebatch-method.md) est suivie d’une opération de méthode de [resynchronisation](./resync-method.md) implicite et, le cas échéant, de l’étendue de cette opération.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une ou plusieurs des valeurs [ADCPROP_UPDATERESYNC_ENUM](./adcprop-updateresync-enum.md) .  
  
## <a name="remarks"></a>Notes  
 Les valeurs de ADCPROP_UPDATERESYNC_ENUM peuvent être combinées, à l’exception de adResyncAll qui représente déjà la combinaison du reste des valeurs.  
  
 La constante **adResyncConflicts** stocke les valeurs de resynchronisation comme valeurs sous-jacentes, mais ne remplace pas les modifications en attente.  
  
 **Update Resync** est une propriété dynamique ajoutée à la collection de [Propriétés](./properties-collection-ado.md) de l’objet [Recordset](./recordset-object-ado.md) lorsque la propriété [CursorLocation](./cursorlocation-property-ado.md) a la valeur **adUseClient**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](./recordset-object-ado.md)