---
title: "Mettre à jour de resynchronisation propriété dynamique (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Update Resync property [ADO]
ms.assetid: 8a3bb608-66d7-4128-a3ef-84cb0556de0d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7c43bd5b60fef002d4fad9cc6fc6842d602d5673
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="update-resync-property-dynamic-ado"></a>Mise à jour Resync propriété dynamique (ADO)
Spécifie si le [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) méthode est suivie par implicite [Resync](../../../ado/reference/ado-api/resync-method.md) opération de la méthode et dans ce cas, la portée de cette opération.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou renvoie une ou plusieurs de la [ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md) valeurs.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de ADCPROP_UPDATERESYNC_ENUM peuvent être combinées à l’exception d’adResyncAll qui représente déjà la combinaison du reste des valeurs.  
  
 La constante **adResyncConflicts** stocke les valeurs de resynchronisation comme des valeurs sous-jacentes, mais ne remplace pas les modifications en attente.  
  
 **Mettre à jour de la resynchronisation** est une propriété dynamique ajoutée à la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection lorsque le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) est définie sur **adUseClient**.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
