---
title: CursorTypeEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0e58e1d7660b4bcd014d5e4b80226fc9c3cfb293
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="cursortypeenum"></a>CursorTypeEnum
Spécifie le type de curseur utilisé dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|Utilise un curseur dynamique. Ajouts, modifications et suppressions par d’autres utilisateurs sont visibles et tous les types de déplacement dans la **Recordset** sont autorisés, à l’exception des signets, si le fournisseur ne les prend pas en charge.|  
|**adOpenForwardOnly**|0|Valeur par défaut. Utilise un curseur avant uniquement. Identique à un curseur statique, à ceci près que vous pouvez faire défiler uniquement vers l’avant entre les enregistrements. Cela améliore les performances lorsque vous avez besoin qu’un seul permettent de passer un **Recordset**.|  
|**adOpenKeyset**|1|Utilise un curseur keyset. Identique à un curseur dynamique, sauf que vous ne pouvez pas voir les enregistrements par d’autres utilisateurs, bien que les enregistrements supprimés par d’autres utilisateurs ne sont pas accessibles à partir de votre **Recordset**. Modifications de données par d’autres utilisateurs sont toujours visibles.|  
|**adOpenStatic**|3|Utilise un curseur statique, qui est une copie statique d’un jeu d’enregistrements que vous pouvez utiliser pour rechercher des données ou générer des rapports. Ajouts, modifications ou suppressions par d’autres utilisateurs ne sont pas visibles.|  
|**adOpenUnspecified**|-1|Ne spécifie pas le type de curseur.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
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
