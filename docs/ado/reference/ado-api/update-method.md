---
title: Méthode de mise à jour | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Update
helpviewer_keywords:
- Update method [ADO]
ms.assetid: 6b2a9c31-1a7e-40db-8a53-30720d0f6cc1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae2645057670ba65a33bb8b5da238c7e01790ae9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713787"
---
# <a name="update-method"></a>Update, méthode
Enregistre les modifications apportées à la ligne actuelle d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet, ou le [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.Update Fields, Values  
record.Fields.Update  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Fields*  
 Facultatif. Un **Variant** qui représente un nom unique, ou un **Variant** tableau qui représente les noms ou les positions ordinales du ou les champs que vous souhaitez modifier.  
  
 *Valeurs*  
 Facultatif. Un **Variant** qui représente une valeur unique, ou un **Variant** tableau qui représente les valeurs pour les champs dans le nouvel enregistrement.  
  
## <a name="remarks"></a>Notes  
  
## <a name="recordset"></a>Ensemble d'enregistrements  
 Utilisez le **mise à jour** méthode pour enregistrer les modifications apportées à l’enregistrement en cours d’un **Recordset** objet depuis l’appel la [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) (méthode) ou parce que la modification des valeurs des champs d’un enregistrement existant. Le **Recordset** objet doit prendre en charge les mises à jour.  
  
 Pour définir les valeurs de champ, effectuez l’une des opérations suivantes :  
  
-   Affecter des valeurs à un [champ](../../../ado/reference/ado-api/field-object.md) l’objet [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété et appelez le **mise à jour** (méthode).  
  
-   Passez un nom de champ et une valeur comme arguments avec le **mise à jour** appeler.  
  
-   Passez un tableau de noms de champs et un tableau de valeurs avec le **mise à jour** appeler.  
  
 Lorsque vous utilisez des tableaux de valeurs et les champs, il doit y avoir un nombre égal d’éléments dans les deux tableaux. En outre, l’ordre des noms de champ doit correspondre à l’ordre des valeurs de champ. Si le nombre et l’ordre des champs et les valeurs ne correspondent pas, une erreur se produit.  
  
 Si le **Recordset** objet prend en charge la mise à jour par lot, vous pouvez mettre en cache plusieurs modifications à un ou plusieurs enregistrements localement jusqu'à ce que vous appeliez la [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) (méthode). Si vous modifiez l’enregistrement en cours ou ajouter un nouvel enregistrement lorsque vous appelez le **UpdateBatch** (méthode), ADO appelle automatiquement la **mise à jour** méthode pour enregistrer les modifications en attente dans l’enregistrement en cours avant transmettre les modifications par lot au fournisseur.  
  
 Si vous passez de l’enregistrement vous ajoutez ou modifiez avant d’appeler le **mise à jour** (méthode), ADO appelle automatiquement **mise à jour** pour enregistrer les modifications. Vous devez appeler la [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) méthode si vous souhaitez annuler toutes les modifications apportées à l’enregistrement actif ou supprimer un enregistrement qui vient d’être ajouté.  
  
 L’enregistrement actif reste actif après avoir appelé la **mise à jour** (méthode).  
  
## <a name="record"></a>Record  
 Le **mise à jour** méthode finalise les ajouts, suppressions et mises à jour des champs dans le [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection d’un **enregistrement** objet.  
  
 Par exemple, les champs supprimés avec la **supprimer** méthode sont marquées pour suppression immédiatement, mais restent dans la collection. Le **mise à jour** méthode doit être appelée pour supprimer réellement ces champs à partir de la collection du fournisseur.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Fields, collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Update et CancelUpdate, exemple de méthodes (VB)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Update et CancelUpdate, exemple de méthodes (VC ++)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [AddNew, méthode (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [CancelUpdate, méthode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode, propriété](../../../ado/reference/ado-api/editmode-property.md)   
 [UpdateBatch, méthode](../../../ado/reference/ado-api/updatebatch-method.md)
