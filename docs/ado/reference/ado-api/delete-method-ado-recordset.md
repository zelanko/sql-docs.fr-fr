---
title: DELETE, méthode (objet Recordset ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Delete
- Recordset15::Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 1eb9209c-602c-4507-b0c2-6527a599b67d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fab7baf1771ad0600f4c1a0a8cac931f0adcc0a4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695429"
---
# <a name="delete-method-ado-recordset"></a>Delete, méthode (objet Recordset ADO)
Supprime l’enregistrement actif ou un groupe d’enregistrements.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.Delete AffectRecords  
```  
  
#### <a name="parameters"></a>Paramètres  
 *AffectRecords*  
 Un [AffectEnum](../../../ado/reference/ado-api/affectenum.md) valeur qui détermine le nombre d’enregistrements le **supprimer** méthode affectera. La valeur par défaut est **adAffectCurrent**.  
  
> [!NOTE]
>  **adAffectAll** et **adAffectAllChapters** ne sont pas des arguments valides **supprimer**.  
  
## <a name="remarks"></a>Notes  
 À l’aide de la **supprimer** méthode marque l’enregistrement actif ou un groupe d’enregistrements dans une [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet pour la suppression. Si le **Recordset** objet n’autorise pas suppression de l’enregistrement, une erreur se produit. Si vous êtes en mode de mise à jour immédiate, suppressions se produisent immédiatement dans la base de données. Si un enregistrement ne peut pas être supprimé avec succès (en raison de violations d’intégrité de base de données, par exemple), l’enregistrement reste en mode édition après l’appel à [mise à jour](../../../ado/reference/ado-api/update-method.md). Cela signifie que vous devez annuler la mise à jour avec [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) avant de déplacer l’enregistrement en cours (par exemple, avec [fermer](../../../ado/reference/ado-api/close-method-ado.md), [déplacer](../../../ado/reference/ado-api/move-method-ado.md), ou [ NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)).  
  
 Si vous êtes en mode de mise à jour par lot, les enregistrements marqués pour suppression à partir du cache et la suppression se produit lorsque vous appelez le [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) (méthode). Utilisez le [filtre](../../../ado/reference/ado-api/filter-property.md) propriété pour afficher les enregistrements supprimés.  
  
 Extraction des valeurs de champ de l’enregistrement supprimé génère une erreur. Après avoir supprimé l’enregistrement en cours, l’enregistrement supprimé reste actif jusqu'à ce que vous déplacez vers un autre enregistrement. Une fois que vous vous éloignez de l’enregistrement supprimé, il n’est plus accessible.  
  
 Si vous imbriquez des suppressions dans une transaction, vous pouvez récupérer les enregistrements supprimés avec la [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) (méthode). Si vous êtes en mode de mise à jour par lot, vous pouvez annuler une suppression en attente ou un groupe de suppressions en attente avec la [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) (méthode).  
  
 Si la tentative de suppression des enregistrements échoue en raison d’un conflit avec les données sous-jacentes (par exemple, un enregistrement déjà supprimé par un autre utilisateur), le fournisseur retourne des avertissements dans le [erreurs](../../../ado/reference/ado-api/errors-collection-ado.md) collection mais n’interrompt ne pas le programme exécution. Une erreur d’exécution se produit uniquement en cas de conflits sur tous les enregistrements demandés.  
  
 Si le [Unique Table](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) propriété dynamique est définie et le **Recordset** est le résultat de l’exécution d’une opération de jointure sur plusieurs tables, puis le **supprimer** méthode supprime uniquement lignes à partir de la table nommée dans le [Unique Table](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) propriété.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer l’exemple de méthode (VB)](../../../ado/reference/ado-api/delete-method-example-vb.md)   
 [Supprimer l’exemple de méthode (VBScript)](../../../ado/reference/ado-api/delete-method-example-vbscript.md)   
 [Supprimer l’exemple de méthode (VC ++)](../../../ado/reference/ado-api/delete-method-example-vc.md)   
 [DELETE, méthode (Collection de champs ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [DELETE, méthode (Collection de paramètres ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [DeleteRecord, méthode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
