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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919254"
---
# <a name="cursortype-property-ado"></a>CursorType, propriété (ADO)
Indique le type de curseur utilisé dans un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) . La valeur par défaut est **adOpenForwardOnly**.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **CursorType** pour spécifier le type de curseur à utiliser lors de l’ouverture de l’objet **Recordset** .  
  
 Seul un paramètre **adOpenStatic** est pris en charge si la propriété [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) est définie sur **adUseClient**. Si une valeur non prise en charge est définie, aucune erreur ne se produit. le **CursorType** le plus proche pris en charge sera utilisé à la place.  
  
 Si un fournisseur ne prend pas en charge le type de curseur demandé, il peut retourner un autre type de curseur. La propriété **CursorType** est modifiée pour correspondre au type de curseur réel utilisé lorsque l’objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) est ouvert. Pour vérifier les fonctionnalités spécifiques du curseur retourné, utilisez la méthode [supports](../../../ado/reference/ado-api/supports-method.md) . Une fois le **jeu d’enregistrements**fermé, la propriété **CursorType** revient à sa valeur d’origine.  
  
 Le graphique suivant montre les fonctionnalités du fournisseur (identifiées par **prend en charge** les constantes de méthode) requises pour chaque type de curseur.  
  
|Pour un jeu d’enregistrements de ce CursorType|La méthode supports doit retourner la valeur true pour toutes ces constantes|  
|----------------------------------------|---------------------------------------------------------------------|  
|**adOpenForwardOnly**|Aucun|  
|**adOpenKeyset**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
|**adOpenDynamic**|**adMovePrevious**|  
|**adOpenStatic**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
  
> [!NOTE]
>  Bien que **prenne en charge**(**adUpdateBatch**) peut avoir la valeur true pour les curseurs dynamiques et avant uniquement, pour les mises à jour par lot, vous devez utiliser un curseur de jeu de clés ou statique. Affectez à la propriété [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) la valeur **adLockBatchOptimistic** et à la propriété **CursorLocation** la valeur **adUseClient** pour activer le service de curseur pour OLE DB, ce qui est requis pour les mises à jour par lot.  
  
 La propriété **CursorType** est en lecture/écriture lorsque le **Recordset** est fermé et en lecture seule lorsqu’il est ouvert.  
  
> [!NOTE]
>  **Utilisation des services de données distants** Lorsqu’elle est utilisée sur un objet **Recordset** côté client, la propriété **CursorType** peut avoir la valeur **adOpenStatic**uniquement.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CursorType, LockType et EditMode, exemple de propriétés (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType et EditMode, exemples de propriétés (VC + +)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Supports, méthode](../../../ado/reference/ado-api/supports-method.md)
