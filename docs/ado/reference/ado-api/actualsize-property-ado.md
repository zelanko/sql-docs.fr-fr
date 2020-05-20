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
author: rothja
ms.author: jroth
ms.openlocfilehash: fd8288fa9f39593cb1f5fb91818925d36d731b9f
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760678"
---
# <a name="actualsize-property-ado"></a>ActualSize, propriété (ADO)
Indique la longueur réelle de la valeur d’un champ, en octets.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Retourne une valeur de **type long** .  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **ActualSize** pour retourner la longueur réelle de la valeur d’un objet [Field](../../../ado/reference/ado-api/field-object.md) . Pour tous les champs, la propriété **ActualSize** est en lecture seule. Si ADO ne peut pas déterminer la longueur de la valeur de l’objet **Field** , la propriété **ActualSize** retourne **adUnknown**.  
  
 Les propriétés **ActualSize** et [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) sont différentes, comme illustré dans l’exemple suivant. Un objet de **champ** avec un type déclaré d' **adVarChar** et une longueur maximale de 50 caractères retourne une valeur de propriété **DefinedSize** de 50, mais la valeur de propriété **ActualSize** renvoyée correspond à la longueur des données stockées dans le champ pour l’enregistrement actif. Les **champs** avec une valeur **DefinedSize** supérieure à 255 octets sont traités comme des colonnes de longueur variable.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ActualSize et DefinedSize, exemple de propriétés (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize et DefinedSize, exemple de propriétés (VC + +)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [DefinedSize, propriété](../../../ado/reference/ado-api/definedsize-property.md)
