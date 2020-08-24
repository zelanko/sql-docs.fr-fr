---
description: Status, propriété (objet Recordset ADO)
title: Status, propriété (objet Recordset ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetStatus
- Recordset15::Status
helpviewer_keywords:
- Status property [ADO Recordset]
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
author: rothja
ms.author: jroth
ms.openlocfilehash: cea09babfd2dacf35705adc71cddcdee99aad544
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777298"
---
# <a name="status-property-ado-recordset"></a>Status, propriété (objet Recordset ADO)
Indique l’état de l’enregistrement en cours par rapport aux mises à jour par lots ou à d’autres opérations en bloc.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne la somme d’une ou plusieurs valeurs [RecordStatusEnum](./recordstatusenum.md) .  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **Status** pour voir les modifications en attente pour les enregistrements modifiés lors de la mise à jour par lot. Vous pouvez également utiliser la propriété **Status** pour afficher l’état des enregistrements qui échouent pendant les opérations en bloc, par exemple lorsque vous appelez les méthodes [Resync](./resync-method.md), [UpdateBatch](./updatebatch-method.md)ou [CancelBatch](./cancelbatch-method-ado.md) sur un objet [Recordset](./recordset-object-ado.md) , ou lorsque vous affectez à la propriété [Filter](./filter-property.md) d’un objet **Recordset** la valeur d’un tableau de signets. Avec cette propriété, vous pouvez déterminer le mode d’échec d’un enregistrement donné et le résoudre en conséquence.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Status, exemple de propriété (Recordset) (VB)](./status-property-example-recordset-vb.md)   
 [Status, exemple de propriété (VC++)](./status-property-example-vc.md)