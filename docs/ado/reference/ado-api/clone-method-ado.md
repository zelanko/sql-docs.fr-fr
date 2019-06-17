---
title: Clone, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::Clone
- Recordset20::raw_Clone
helpviewer_keywords:
- Clone method [ADO]
ms.assetid: ad49265f-1c05-4271-9bbf-7c00010ac18c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fbeedf9e56c1f0606a7c8f842baedc9d11ad3929
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698797"
---
# <a name="clone-method-ado"></a>Clone, méthode (ADO)
Crée un doublon [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet depuis une **Recordset** objet. Si vous le souhaitez, spécifie que le clone doit être en lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set rstDuplicate = rstOriginal.Clone (LockType)  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Recordset** référence d’objet.  
  
#### <a name="parameters"></a>Paramètres  
 *rstDuplicate*  
 Une variable objet qui identifie le doublon **Recordset** objet devant être créé.  
  
 *rstOriginal*  
 Une variable objet qui identifie le **Recordset** objet à dupliquer.  
  
 *LockType*  
 Facultatif. Un [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) valeur qui spécifie le type de verrou de l’original **Recordset**, ou en lecture seule **Recordset**. Les valeurs valides sont **adLockUnspecified** ou **adLockReadOnly**.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **Clone** dupliqué de la méthode de création de plusieurs **Recordset** objets, en particulier si vous voulez conserver plusieurs enregistrements en cours dans un ensemble donné d’enregistrements. À l’aide de la **Clone** méthode est plus efficace que la création et ouverture d’un nouvel **Recordset** objet qui utilise la même définition que l’original.  
  
 Le [filtre](../../../ado/reference/ado-api/filter-property.md) propriété de l’original **Recordset**, le cas échéant, ne seront pas appliquées pour le clone. Définir le **filtre** propriété du nouveau **Recordset** pour filtrer les résultats. La méthode la plus simple pour copier tout existant **filtre** valeur consiste à affecter directement, comme suit.  
  
```  
rsNew.Filter = rsOriginal.Filter  
```  
  
 L’enregistrement en cours d’un clone nouvellement créé est défini sur le premier enregistrement.  
  
 Modifications apportées à un **Recordset** objet sont visibles dans tous ses clones, quel que soit le type de curseur. Toutefois, après l’exécution de [Requery](../../../ado/reference/ado-api/requery-method.md) sur l’original **Recordset**, les clones ne seront plus synchronisés à l’original.  
  
 Fermeture de la version d’origine **Recordset** ne ferme pas ses copies, ni ne le fait fermeture d’une copie de fermer la version d’origine ou les autres copies.  
  
 Vous ne pouvez cloner un **Recordset** objet qui prend en charge des signets. Les valeurs de signet sont interchangeables ; Autrement dit, une référence de signet à partir d’un **Recordset** objet fait référence au même enregistrement dans un de ses clones.  
  
 Certains **Recordset** événements sont déclenchés seront produit également dans toutes les **Recordset** clone. Toutefois, étant donné que l’enregistrement actif peut différer entre cloné **Recordsets**, les événements ne peuvent pas être valides pour le clone. Par exemple, si vous modifiez une valeur d’un champ, un [WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md) événement se produit dans les modifications **Recordset** et dans tous les clones. Le *champs* paramètre de la **WillChangeField** événement de cloné **Recordset** (où la modification a été effectuée pas) fait référence aux champs de l’enregistrement actif du clone, qui peut être un autre enregistrement à l’enregistrement en cours de l’original **Recordset** où la modification s’est produite.  
  
 Le tableau suivant fournit une liste complète de tous les **Recordset** événements. Cette propriété indique si elles sont valides et déclenchées pour tous les clones recordset générés à l’aide de la **Clone** (méthode).  
  
|Événement|Déclenché dans clones ?|  
|-----------|--------------------------|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|Non|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|Non|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|Non|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Oui|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Non|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Oui|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Non|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Oui|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Oui|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Non|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Non|  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Clone, exemple de méthode (VB)](../../../ado/reference/ado-api/clone-method-example-vb.md)   
 [Clone, exemple de méthode (VBScript)](../../../ado/reference/ado-api/clone-method-example-vbscript.md)   
 [Clone, exemple de méthode (VC++)](../../../ado/reference/ado-api/clone-method-example-vc.md)   
