---
title: CursorTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6333934997c9de38b8df1dd08849886ff3dd7f2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933273"
---
# <a name="cursortypeenum"></a>CursorTypeEnum
Spécifie le type de curseur utilisé dans un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|Utilise un curseur dynamique. Les ajouts, modifications et suppressions effectués par d’autres utilisateurs sont visibles, et tous les types de déplacement via le **Recordset** sont autorisés, à l’exception des signets, si le fournisseur ne les prend pas en charge.|  
|**adOpenForwardOnly**|0|Par défaut. Utilise un curseur avant uniquement. Identique à un curseur statique, sauf que vous pouvez faire défiler vers l’avant les enregistrements. Cela améliore les performances lorsque vous devez effectuer une seule passe dans un **jeu d’enregistrements**.|  
|**adOpenKeyset**|1|Utilise un curseur de jeu de clés. Comme un curseur dynamique, sauf que vous ne pouvez pas voir les enregistrements que d’autres utilisateurs ajoutent, bien que les enregistrements supprimés par d’autres utilisateurs ne soient pas accessibles à partir de votre **Recordset**. Les modifications de données effectuées par d’autres utilisateurs sont toujours visibles.|  
|**adOpenStatic**|3|Utilise un curseur statique, qui est une copie statique d’un ensemble d’enregistrements que vous pouvez utiliser pour rechercher des données ou générer des rapports. Les ajouts, modifications ou suppressions effectués par d’autres utilisateurs ne sont pas visibles.|  
|**adOpenUnspecified**|-1|Ne spécifie pas le type de curseur.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.CursorType.DYNAMIC|  
|AdoEnums.CursorType.FORWARDONLY|  
|AdoEnums.CursorType.KEYSET|  
|AdoEnums.CursorType.STATIC|  
|AdoEnums.CursorType.UNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
 [CursorType, propriété (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
