---
title: ActualSize, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b864f480542c7ff649bf9b830ba445517dafb91b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698895"
---
# <a name="actualsize-property-ado"></a>ActualSize, propriété (ADO)
Indique la longueur réelle de la valeur d’un champ en octets.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Retourne un **Long** valeur.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **ActualSize** propriété pour retourner la longueur réelle d’un [champ](../../../ado/reference/ado-api/field-object.md) valeur de l’objet. Pour tous les champs, les **ActualSize** propriété est en lecture seule. Si ADO ne peut pas déterminer la longueur de la **champ** valeur de l’objet, le **ActualSize** retourne de la propriété **adUnknown**.  
  
 Le **ActualSize** et [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) propriétés sont différentes, comme indiqué dans l’exemple suivant. Un **champ** objet avec un type déclaré de **adVarChar** et une longueur maximale de 50 caractères retourne un **DefinedSize** valeur de propriété de 50, mais le  **ActualSize** valeur de propriété retournée est la longueur des données stockées dans le champ de l’enregistrement actif. **Champs** avec un **DefinedSize** supérieure à 255 octets sont traitées en tant que colonnes de longueur variable.  
  
## <a name="applies-to"></a>S'applique à  
 [Field, objet](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ActualSize et DefinedSize, exemple de propriétés (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize et DefinedSize, exemple de propriétés (VC ++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [DefinedSize, propriété](../../../ado/reference/ado-api/definedsize-property.md)
