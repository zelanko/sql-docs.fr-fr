---
title: Getschemaobject, méthode (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- GetSchemaObject
- Cellset::GetSchemaObject
helpviewer_keywords:
- GetSchemaObject method [ADO MD]
ms.assetid: 36b754b4-6b17-4dd1-a925-bca46938b7c4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 690c81a46c62c8844780e82b5c82a0ff7301105d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949764"
---
# <a name="getschemaobject-method-ado-md"></a>GetSchemaObject, méthode (ADO MD)
Récupère un objet de schéma ADO MD ([Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [hiérarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md), ou [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md)) par son [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ObjType*  
 Un [SchemaObjectTypeEnum](../../../ado/reference/ado-md-api/schemaobjecttypeenum.md) valeur spécifiant le type d’objet de schéma (Dimension, hiérarchie, niveau ou membre) à récupérer.  
  
 *UniqueName*  
 Un **chaîne** spécifiant le **UniqueName** valeur de propriété de l’objet à récupérer.  
  
## <a name="remarks"></a>Notes  
 **GetSchemaObject** récupère des objets à l’aide de leurs noms uniques, comme spécifié par le **UniqueName** propriété. Les noms des objets parents n’êtes pas obligé d’être connu, et les collections de parent n’êtes pas obligé d’être renseignée pour récupérer un objet de schéma.  
  
## <a name="applies-to"></a>S'applique à  
 [CubeDef, objet (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CubeDef, objet (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)
