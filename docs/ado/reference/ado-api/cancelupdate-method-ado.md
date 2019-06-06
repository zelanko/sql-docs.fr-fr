---
title: CancelUpdate, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::CancelUpdate
helpviewer_keywords:
- CancelUpdate method [ADO]
ms.assetid: eaa856cc-c786-462e-890c-c896261b1741
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b53fa2e9d69b39218d846b57070b78ae230d81cf
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698814"
---
# <a name="cancelupdate-method-ado"></a>CancelUpdate, méthode (ADO)
Annule toutes les modifications apportées à la ligne actuelle ou nouvelle d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet, ou le [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet, avant d’appeler le [mise à jour ](../../../ado/reference/ado-api/update-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.CancelUpdaterecord.Fields.CancelUpdate  
```  
  
## <a name="remarks"></a>Notes  
  
## <a name="recordset"></a>Ensemble d'enregistrements  
 Utilisez le **CancelUpdate** méthode pour annuler toutes les modifications apportées à la ligne actuelle ou ignorer une ligne ajoutée. Vous ne pouvez pas annuler les modifications apportées à la ligne actuelle ou une nouvelle ligne après avoir appelé la **mise à jour** (méthode), à moins que les modifications font partie d’une transaction que vous pouvez restaurer avec la [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) (méthode), ou une partie une mise à jour par lots. Dans le cas d’une mise à jour par lots, vous pouvez annuler la **mettre à jour** avec la **CancelUpdate** ou [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) (méthode).  
  
 Si vous ajoutez une nouvelle ligne lorsque vous appelez le **CancelUpdate** (méthode), la ligne actuelle devient la ligne qui était actuelle avant le [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) appeler.  
  
 Si vous êtes en mode édition et que vous souhaitez déplacer l’enregistrement en cours (par exemple, en utilisant le [déplacer](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md), ou [fermer](../../../ado/reference/ado-api/close-method-ado.md) méthodes), vous pouvez utiliser  **CancelUpdate** pour annuler les modifications en attente. Vous devrez peut-être effectuer cette opération si la mise à jour ne peut pas être publiée dans la source de données. Par exemple, une tentative de suppression qui échoue en raison de violations d’intégrité référentielle laisse le **Recordset** en mode édition après un appel à [supprimer](../../../ado/reference/ado-api/delete-method-ado-recordset.md).  
  
## <a name="record"></a>Enregistrement  
 Le **CancelUpdate** méthode annule tout en attente les insertions ou les suppressions de [champ](../../../ado/reference/ado-api/field-object.md) des objets et en attente de mises à jour des champs existants et rétablit leurs valeurs d’origine. Le [état](../../../ado/reference/ado-api/status-property-ado-recordset.md) propriété de tous les champs dans le **champs** collection a la valeur **adFieldOK**.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Fields, collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Update et CancelUpdate, exemple de méthodes (VB)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Update et CancelUpdate, exemple de méthodes (VC ++)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [AddNew, méthode (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Cancel, méthode (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Cancel, méthode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch, méthode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate, méthode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [EditMode, propriété](../../../ado/reference/ado-api/editmode-property.md)   
 [Update, méthode](../../../ado/reference/ado-api/update-method.md)
