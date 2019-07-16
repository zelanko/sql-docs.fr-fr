---
title: CursorType, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::CursorType
helpviewer_keywords:
- CursorType property [ADO]
ms.assetid: b62c66ca-58d5-430e-9257-eb38c65e48c2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4dc881b96a1e2641d4946340c9462455197f2043
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67919254"
---
# <a name="cursortype-property-ado"></a>CursorType, propriété (ADO)
Indique le type de curseur utilisé dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) valeur. La valeur par défaut est **adOpenForwardOnly**.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **CursorType** propriété pour spécifier le type de curseur qui doit être utilisé lors de l’ouverture du **Recordset** objet.  
  
 Seule la valeur **adOpenStatic** est pris en charge si le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété est définie sur **adUseClient**. Si une valeur non pris en charge est définie, aucune erreur n’entraîne ; prise en charge la plus proche **CursorType** sera utilisé à la place.  
  
 Si un fournisseur ne prend pas en charge le type de curseur demandé, elle peut retourner un autre type de curseur. Le **CursorType** propriété sera modifiée pour correspondre au type de curseur en cours d’utilisation lorsque le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet est ouvert. Pour vérifier les fonctionnalités spécifiques du curseur retourné, utilisez la [prend en charge](../../../ado/reference/ado-api/supports-method.md) (méthode). Après avoir fermé la **Recordset**, le **CursorType** propriété retrouve sa valeur d’origine.  
  
 Le graphique suivant montre les fonctionnalités des fournisseurs (identifié par **prend en charge** constantes de la méthode) requis pour chaque type de curseur.  
  
|Pour un jeu d’enregistrements de ce type de curseur|La méthode prend en charge doit retourner True pour toutes ces constantes|  
|----------------------------------------|---------------------------------------------------------------------|  
|**adOpenForwardOnly**|none|  
|**adOpenKeyset**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
|**adOpenDynamic**|**adMovePrevious**|  
|**adOpenStatic**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
  
> [!NOTE]
>  Bien que **prend en charge**(**adUpdateBatch**) peut être true pour les curseurs dynamiques et avant uniquement, pour les mises à jour de lot, vous devez utiliser soit un curseur keyset ou static. Définir le [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) propriété **adLockBatchOptimistic** et **CursorLocation** propriété **adUseClient** pour activer le curseur Service pour OLE DB, qui est requis pour les mises à jour par lots.  
  
 Le **CursorType** propriété est en lecture/écriture lors de la **Recordset** est fermé et en lecture seule lorsqu’il est ouvert.  
  
> [!NOTE]
>  **Utilisation de Service de données à distance** lorsqu’il est utilisé sur une côté client **Recordset** objet, le **CursorType** propriété peut être définie uniquement au **adOpenStatic**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CursorType, LockType et EditMode, exemple de propriétés (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType et EditMode, exemple de propriétés (VC ++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Supports, méthode](../../../ado/reference/ado-api/supports-method.md)
