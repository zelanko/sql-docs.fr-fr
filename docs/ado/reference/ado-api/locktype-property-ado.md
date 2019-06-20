---
title: LockType, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::LockType
helpviewer_keywords:
- LockType property [ADO]
ms.assetid: 9920c14e-033a-4de1-8149-0ce9737a3246
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a53c6e6e0164b404fdd5b106bae83137d56f319e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697646"
---
# <a name="locktype-property-ado"></a>LockType, propriété (ADO)
Indique le type des verrous placés sur les enregistrements pendant la modification.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) valeur. La valeur par défaut est **adLockReadOnly**.  
  
## <a name="remarks"></a>Notes  
 Définir le **LockType** propriété avant d’ouvrir un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) pour spécifier le type de verrouillage le fournisseur doit utiliser pour l’ouvrir. Lire la propriété pour retourner le type de verrouillage en cours d’utilisation sur une ouverte **Recordset** objet.  
  
 Fournisseurs ne peuvent pas en charge tous les types de verrous. Si un fournisseur ne peut pas prendre en charge demandé **LockType** définition, elle remplacera un autre type de verrouillage. Pour déterminer les fonctionnalités de verrouillage disponibles dans un **Recordset** de l’objet, utilisez le [prend en charge](../../../ado/reference/ado-api/supports-method.md) méthode avec **adUpdate** et **adUpdateBatch**.  
  
 Le **adLockPessimistic** paramètre n’est pas pris en charge si le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété est définie sur **adUseClient**. Si une valeur non pris en charge est définie, aucune erreur n’entraîne ; prise en charge la plus proche **LockType** sera utilisé à la place.  
  
 Le **LockType** propriété est en lecture/écriture lors de la **Recordset** est fermé et en lecture seule lorsqu’il est ouvert.  
  
> [!NOTE]
>  **Utilisation de Service de données à distance** lorsqu’il est utilisé sur une côté client **Recordset** objet, le **LockType** propriété peut uniquement être définie sur **adLockBatchOptimistic**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CursorType, LockType et EditMode, exemple de propriétés (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType et EditMode, exemple de propriétés (VC ++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [CancelBatch, méthode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [UpdateBatch, méthode](../../../ado/reference/ado-api/updatebatch-method.md)
