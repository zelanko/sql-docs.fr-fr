---
description: LockType, propriété (ADO)
title: LockType, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 74e86b054ac9d63527cc0f142ee50aa81acbe4b4
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990690"
---
# <a name="locktype-property-ado"></a>LockType, propriété (ADO)
Indique le type de verrou placé sur les enregistrements lors de la modification.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur [LockTypeEnum](./locktypeenum.md) . La valeur par défaut est **adLockReadOnly**.  
  
## <a name="remarks"></a>Notes  
 Définissez la propriété **LockType** avant d’ouvrir un [Recordset](./recordset-object-ado.md) pour spécifier le type de verrouillage que le fournisseur doit utiliser lors de son ouverture. Lisez la propriété pour retourner le type de verrouillage en cours d’utilisation sur un objet **Recordset** ouvert.  
  
 Les fournisseurs ne prennent peut-être pas en charge tous les types de verrous. Si un fournisseur ne prend pas en charge le paramètre **LockType** demandé, il remplace un autre type de verrouillage. Pour déterminer les fonctionnalités de verrouillage réelles disponibles dans un objet **Recordset** , utilisez la méthode [supports](./supports-method.md) avec **adUpdate** et **adUpdateBatch**.  
  
 Le paramètre **adLockPessimistic** n’est pas pris en charge si la propriété [CursorLocation](./cursorlocation-property-ado.md) a la valeur **adUseClient**. Si une valeur non prise en charge est définie, aucune erreur ne se produit. le **LockType** le plus proche pris en charge sera utilisé à la place.  
  
 La propriété **LockType** est en lecture/écriture lorsque le **Recordset** est fermé et en lecture seule lorsqu’il est ouvert.  
  
> [!NOTE]
>  **Utilisation des services de données distants** Lorsqu’elle est utilisée sur un objet **Recordset** côté client, la propriété **LockType** peut uniquement être définie sur **adLockBatchOptimistic**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CursorType, LockType et EditMode, exemple de propriétés (VB)](./cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType et EditMode, exemples de propriétés (VC + +)](./cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Méthode CancelBatch (ADO)](./cancelbatch-method-ado.md)   
 [UpdateBatch, méthode](./updatebatch-method.md)