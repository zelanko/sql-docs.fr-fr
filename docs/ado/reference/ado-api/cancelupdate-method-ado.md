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
ms.openlocfilehash: fa9e680e1626311f2cc10aa7c79fb583841fbc38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920114"
---
# <a name="cancelupdate-method-ado"></a>CancelUpdate, méthode (ADO)
Annule toutes les modifications apportées à la ligne actuelle ou nouvelle d’un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) , ou à la collection [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) d’un objet [Record](../../../ado/reference/ado-api/record-object-ado.md) , avant d’appeler la méthode [Update](../../../ado/reference/ado-api/update-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.CancelUpdaterecord.Fields.CancelUpdate  
```  
  
## <a name="remarks"></a>Notes  
  
## <a name="recordset"></a>Ensemble d'enregistrements  
 Utilisez la méthode **CancelUpdate** pour annuler les modifications apportées à la ligne actuelle ou pour ignorer une ligne qui vient d’être ajoutée. Vous ne pouvez pas annuler les modifications apportées à la ligne actuelle ou à une nouvelle ligne après avoir appelé la méthode **Update** , à moins que les modifications ne fassent partie d’une transaction que vous pouvez restaurer avec la méthode [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) , ou faire partie d’une mise à jour par lot. Dans le cas d’une mise à jour par lot, vous pouvez annuler la **mise à jour** avec la méthode **CancelUpdate** ou [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) .  
  
 Si vous ajoutez une nouvelle ligne lorsque vous appelez la méthode **CancelUpdate** , la ligne active devient la ligne qui était en cours avant l’appel [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) .  
  
 Si vous êtes en mode édition et que vous souhaitez quitter l’enregistrement actif (par exemple, à l’aide des méthodes [Move](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)ou [Close](../../../ado/reference/ado-api/close-method-ado.md) ), vous pouvez utiliser **CancelUpdate** pour annuler les modifications en attente. Vous devrez peut-être effectuer cette opération si la mise à jour ne peut pas être publiée avec succès dans la source de données. Par exemple, une tentative de suppression qui échoue en raison de violations d’intégrité référentielle laisse le **Recordset** en mode édition après un appel à [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md).  
  
## <a name="record"></a>Enregistrement  
 La méthode **CancelUpdate** annule les insertions ou les suppressions en attente des objets [Field](../../../ado/reference/ado-api/field-object.md) , et annule les mises à jour en attente des champs existants et les restaure à leurs valeurs d’origine. La propriété [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) de tous les champs de la collection **Fields** a la valeur **adFieldOK**.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Fields, collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Update et CancelUpdate, exemple de méthodes (VB)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Update et CancelUpdate, exemple de méthodes (VC + +)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [AddNew, méthode (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Cancel, méthode (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Cancel, méthode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Méthode CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate, méthode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [EditMode, propriété](../../../ado/reference/ado-api/editmode-property.md)   
 [Update, méthode](../../../ado/reference/ado-api/update-method.md)
