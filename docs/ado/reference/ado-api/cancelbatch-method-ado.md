---
title: Méthode CancelBatch (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_CancelBatch
- Recordset15::CancelBatch
helpviewer_keywords:
- CancelBatch method [ADO]
ms.assetid: dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c
author: rothja
ms.author: jroth
ms.openlocfilehash: c2e9f3b57137b4c113b9e177e9fecefec4070ac0
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763170"
---
# <a name="cancelbatch-method-ado"></a>CancelBatch, méthode (ADO)
Annule une mise à jour par lot en attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.CancelBatchAffectRecords  
```  
  
#### <a name="parameters"></a>Paramètres  
 *AffectRecords*  
 facultatif. Valeur [AffectEnum](../../../ado/reference/ado-api/affectenum.md) qui indique le nombre d’enregistrements affectés par la méthode **CancelBatch** .  
  
## <a name="remarks"></a>Notes  
 Utilisez la méthode **CancelBatch** pour annuler les mises à jour en attente dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) en mode de mise à jour par lot. Si le **jeu d’enregistrements** est en mode de mise à jour immédiate, l’appel de **CancelBatch** sans **adAffectCurrent** génère une erreur.  
  
 Si vous modifiez l’enregistrement en cours ou si vous ajoutez un nouvel enregistrement lorsque vous appelez **CancelBatch**, ADO appelle d’abord la méthode [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) pour annuler les modifications mises en cache. Après cela, toutes les modifications en attente dans le **jeu d’enregistrements** sont annulées.  
  
 L’enregistrement en cours peut ne pas être déterminable après un appel de **CancelBatch** , en particulier si vous étiez en train d’ajouter un nouvel enregistrement. Pour cette raison, il est prudent de définir la position de l’enregistrement actuel sur un emplacement connu dans le **jeu d’enregistrements** après l’appel de la fonction **CancelBatch** . Par exemple, appelez la méthode [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) .  
  
 Si la tentative d’annulation des mises à jour en attente échoue en raison d’un conflit avec les données sous-jacentes (par exemple, si un enregistrement a été supprimé par un autre utilisateur), le fournisseur renvoie des avertissements à la collection d' [Erreurs](../../../ado/reference/ado-api/errors-collection-ado.md) , mais n’interrompt pas l’exécution du programme. Une erreur d’exécution se produit uniquement en cas de conflit sur tous les enregistrements demandés. Utilisez la propriété [Filter](../../../ado/reference/ado-api/filter-property.md) (**adFilterAffectedRecords**) et la propriété [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) pour localiser les enregistrements avec conflits.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [UpdateBatch et CancelBatch, exemples de méthodes (VB)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch et CancelBatch, exemples de méthodes (VC + +)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Cancel, méthode (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Cancel, méthode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelUpdate, méthode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate, méthode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Clear, méthode (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [LockType, propriété (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [UpdateBatch, méthode](../../../ado/reference/ado-api/updatebatch-method.md)
