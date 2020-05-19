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
author: rothja
ms.author: jroth
ms.openlocfilehash: c936eb8016be0851fa6d3ecff1f624eab6c895f3
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82748675"
---
# <a name="clone-method-ado"></a>Clone, méthode (ADO)
Crée un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dupliqué à partir d’un objet **Recordset** existant. Spécifie éventuellement que le clone doit être en lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set rstDuplicate = rstOriginal.Clone (LockType)  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une référence **d’objet Recordset** .  
  
#### <a name="parameters"></a>Paramètres  
 *rstDuplicate*  
 Variable objet qui identifie l’objet **Recordset** dupliqué à créer.  
  
 *rstOriginal*  
 Variable objet qui identifie l’objet **Recordset** à dupliquer.  
  
 *Verrou*  
 facultatif. Valeur [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) qui spécifie le type de verrou du **Recordset**d’origine ou un **jeu d’enregistrements**en lecture seule. Les valeurs valides sont **adLockUnspecified** ou **adLockReadOnly**.  
  
## <a name="remarks"></a>Remarques  
 Utilisez la méthode **clone** pour créer plusieurs objets **Recordset** dupliqués, en particulier si vous souhaitez conserver plusieurs enregistrements actifs dans un ensemble donné d’enregistrements. L’utilisation de la méthode **clone** est plus efficace que la création et l’ouverture d’un nouvel objet **Recordset** qui utilise la même définition que l’original.  
  
 La propriété [Filter](../../../ado/reference/ado-api/filter-property.md) du **Recordset**d’origine, le cas échéant, ne sera pas appliquée au clone. Définissez la propriété **Filter** du nouvel ensemble d' **enregistrements** pour filtrer les résultats. La façon la plus simple de copier une valeur de **filtre** existante consiste à l’assigner directement, comme suit.  
  
```  
rsNew.Filter = rsOriginal.Filter  
```  
  
 L’enregistrement actuel d’un clone nouvellement créé est défini sur le premier enregistrement.  
  
 Les modifications que vous apportez à un objet **Recordset** sont visibles dans tous ses clones, quel que soit le type de curseur. Toutefois, après l’exécution de [Requery](../../../ado/reference/ado-api/requery-method.md) sur le **jeu d’enregistrements**d’origine, les clones ne sont plus synchronisés avec l’original.  
  
 La fermeture de l' **objet Recordset** d’origine ne ferme pas ses copies et ne ferme pas non plus la copie d’origine ou de l’une des autres copies.  
  
 Vous pouvez cloner un objet **Recordset** qui prend en charge les signets uniquement. Les valeurs de signet sont interchangeables ; autrement dit, une référence de signet d’un objet **Recordset** fait référence au même enregistrement dans l’un de ses clones.  
  
 Certains événements du **Recordset** qui sont déclenchés se produisent également dans tous les clones de l’ensemble **d’enregistrements** . Toutefois, étant donné que l’enregistrement en cours peut différer d’un **jeu d’enregistrements**cloné à un autre, les événements peuvent ne pas être valides pour le clone. Par exemple, si vous modifiez la valeur d’un champ, un événement [WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md) se produit dans le **jeu d’enregistrements** modifié et dans tous les clones. Le paramètre *Fields* de l’événement **WillChangeField** d’un **jeu d’enregistrements** cloné (où la modification n’a pas été apportée) fait référence aux champs de l’enregistrement actuel du clone, qui peut être un enregistrement différent de l’enregistrement actif du **Recordset** d’origine où la modification s’est produite.  
  
 Le tableau suivant fournit une liste complète de tous les événements du **Recordset** . Elle indique si elles sont valides et déclenchées pour tous les clones d’ensemble d’enregistrements générés à l’aide de la méthode **clone** .  
  
|Événement|Déclenché dans les clones ?|  
|-----------|--------------------------|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|No|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|No|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|No|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Yes|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|No|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Yes|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|No|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Yes|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Yes|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|No|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|No|  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Clone, exemple de méthode (VB)](../../../ado/reference/ado-api/clone-method-example-vb.md)   
 [Clone, exemple de méthode (VBScript)](../../../ado/reference/ado-api/clone-method-example-vbscript.md)   
 [Clone, exemple de méthode (VC++)](../../../ado/reference/ado-api/clone-method-example-vc.md)   
