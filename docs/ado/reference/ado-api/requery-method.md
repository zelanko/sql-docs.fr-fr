---
title: Méthode Requery | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Requery
- Recordset15::raw_Requery
helpviewer_keywords:
- Requery method [ADO]
ms.assetid: d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1
author: rothja
ms.author: jroth
ms.openlocfilehash: 29b2d0cba996e3f41a12df93babe8d9b86a8fbeb
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82756512"
---
# <a name="requery-method"></a>Requery, méthode
Met à jour les données dans un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) en exécutant à nouveau la requête sur laquelle l’objet est basé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Options*  
 facultatif. Masque de répercussion qui contient des valeurs [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) et [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) affectant cette opération.  
  
> [!NOTE]
>  Si *options* a la valeur **adAsyncExecute**, cette opération s’exécute de façon asynchrone et un événement [RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) est émis lorsqu’elle se termine. Les valeurs **ExecuteOpenEnum** de **adExecuteNoRecords** ou **adExecuteStream** ne doivent pas être utilisées avec **Requery**.  
  
## <a name="remarks"></a>Remarques  
 Utilisez la méthode **Requery** pour actualiser la totalité du contenu d’un objet **Recordset** à partir de la source de données en réémettant la commande d’origine et en extrayant les données une deuxième fois. L’appel de cette méthode équivaut à appeler les méthodes [Close](../../../ado/reference/ado-api/close-method-ado.md) et [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) à la suite. Si vous modifiez l’enregistrement en cours ou ajoutez un nouvel enregistrement, une erreur se produit.  
  
 Lorsque l’objet **Recordset** est ouvert, les propriétés qui définissent la nature du curseur ([CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md), [LockType](../../../ado/reference/ado-api/locktype-property-ado.md), [maxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md), etc.) sont en lecture seule. Ainsi, la méthode **Requery** peut uniquement actualiser le curseur actuel. Pour modifier l’une des propriétés de curseur et afficher les résultats, vous devez utiliser la méthode [Close](../../../ado/reference/ado-api/close-method-ado.md) afin que les propriétés soient à nouveau en lecture/écriture. Vous pouvez ensuite modifier les paramètres de propriété et appeler la méthode [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) pour rouvrir le curseur.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Execute, Requery et Clear, exemples de méthodes (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery et Clear, exemple de méthode (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery et Clear, exemples de méthodes (VC + +)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CommandText, propriété (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)
