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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933273"
---
# <a name="cursortypeenum"></a>CursorTypeEnum
Spécifie le type de curseur utilisé dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|Utilise un curseur dynamique. Ajouts, modifications et suppressions par d’autres utilisateurs sont visibles et tous les types de déplacement dans le **Recordset** sont autorisés, à l’exception des signets, si le fournisseur ne les prennent pas en charge.|  
|**adOpenForwardOnly**|0|Valeur par défaut. Utilise un curseur avant uniquement. Identique à un curseur statique, à ceci près que vous pouvez faire défiler uniquement vers l’avant entre les enregistrements. Cela améliore les performances lorsque vous devez à effectue une seule traverser un **Recordset**.|  
|**adOpenKeyset**|1|Utilise un curseur keyset. Comme un curseur dynamique, à ceci près que vous ne voyez pas les enregistrements par d’autres utilisateurs, bien que les enregistrements supprimés par d’autres utilisateurs ne sont pas accessibles à partir de votre **Recordset**. Modifications de données par d’autres utilisateurs sont toujours visibles.|  
|**adOpenStatic**|3|Utilise un curseur statique, qui est une copie statique d’un jeu d’enregistrements que vous pouvez utiliser pour rechercher des données ou générer des rapports. Ajouts, modifications ou suppressions par d’autres utilisateurs ne sont pas visibles.|  
|**adOpenUnspecified**|-1|Ne spécifie pas le type de curseur.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.CursorType.DYNAMIC|  
|AdoEnums.CursorType.FORWARDONLY|  
|AdoEnums.CursorType.KEYSET|  
|AdoEnums.CursorType.STATIC|  
|AdoEnums.CursorType.UNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
 [CursorType, propriété (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
