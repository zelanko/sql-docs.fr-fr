---
title: Propriété Status (objet Recordset ADO) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d57767cb50382f676aec2e11eaef77a8cdab9a87
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711009"
---
# <a name="status-property-ado-recordset"></a>Status, propriété (objet Recordset ADO)
Indique l’état de l’enregistrement actif en ce qui concerne les mises à jour du lot ou d’autres opérations en bloc.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une somme d’une ou plusieurs [RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md) valeurs.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **état** propriété pour connaître les modifications en attente pour les enregistrements modifiés lors de la mise à jour par lots. Vous pouvez également utiliser le **état** propriété pour afficher l’état des enregistrements qui échouent lors des opérations en bloc, comme lorsque vous appelez le [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), ou [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) méthodes sur un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) de l’objet, ou définir le [filtre](../../../ado/reference/ado-api/filter-property.md) propriété sur un **Recordset** objet en un tableau de signets. Avec cette propriété, vous pouvez déterminer comment un enregistrement donné a échoué et résolvez-le en conséquence.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Status, exemple de propriété (objet Recordset) (VB)](../../../ado/reference/ado-api/status-property-example-recordset-vb.md)   
 [Status, exemple de propriété (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
