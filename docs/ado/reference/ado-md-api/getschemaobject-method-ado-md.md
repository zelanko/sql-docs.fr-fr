---
description: GetSchemaObject, méthode (ADO MD)
title: Méthode GetSchemaObject (ADO MD) | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 19af2bf0e7058a8f483da25c0db926ebc19807c6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441011"
---
# <a name="getschemaobject-method-ado-md"></a>GetSchemaObject, méthode (ADO MD)
Récupère un objet de schéma ADO MD ([dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [hiérarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md)ou [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md)) par son [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ObjType*  
 Valeur [SchemaObjectTypeEnum](../../../ado/reference/ado-md-api/schemaobjecttypeenum.md) spécifiant le type d’objet de schéma (dimension, hiérarchie, niveau ou membre) à récupérer.  
  
 *UniqueName*  
 **Chaîne** spécifiant la valeur de la propriété **UniqueName** de l’objet à récupérer.  
  
## <a name="remarks"></a>Notes  
 **GetSchemaObject** récupère les objets à l’aide de leurs noms uniques, comme spécifié par la propriété **UniqueName** . Les noms des objets parents n’ont pas besoin d’être connus, et les collections parentes n’ont pas besoin d’être remplies pour récupérer un objet de schéma.  
  
## <a name="applies-to"></a>S'applique à  
 [CubeDef, objet (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CubeDef, objet (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)
