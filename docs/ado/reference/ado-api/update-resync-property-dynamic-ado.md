---
title: Mettre à jour Resync, propriété dynamique (ADO) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ed0e3ad8027c31a351ddb4506d3b420aa3a1124d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938807"
---
# <a name="update-resync-property-dynamic-ado"></a>Update Resync, propriété dynamique (ADO)
Spécifie si le [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) méthode est suivie par implicite [Resync](../../../ado/reference/ado-api/resync-method.md) opération de la méthode et si tel est le cas, la portée de cette opération.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une ou plusieurs de la [ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md) valeurs.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de ADCPROP_UPDATERESYNC_ENUM peuvent être combinées à l’exception d’adResyncAll qui représente déjà la combinaison du reste des valeurs.  
  
 La constante **adResyncConflicts** stocke les valeurs de resynchronisation comme des valeurs sous-jacentes, mais ne remplace pas de modifications en attente.  
  
 **Mettre à jour de la resynchronisation** est une propriété dynamique ajoutée à la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection lorsque le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété est définie sur **adUseClient**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
