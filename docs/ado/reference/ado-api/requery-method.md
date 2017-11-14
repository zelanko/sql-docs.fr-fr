---
title: "Requery (méthode) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- Recordset15::Requery
- Recordset15::raw_Requery
helpviewer_keywords:
- Requery method [ADO]
ms.assetid: d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f59d4c6cdcdb3f34be4361969da15e5af117f995
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="requery-method"></a>Requery (méthode)
Met à jour les données dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet en réexécutant la requête sur laquelle l’objet est basé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Options*  
 Ce paramètre est facultatif. Masque de bits qui contienne [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) et [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valeurs affectant cette opération.  
  
> [!NOTE]
>  Si *Options* a la valeur **adAsyncExecute**, cette opération est exécutée de façon asynchrone et une [RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) événement est déclenché lorsqu’elle est terminée. Le **ExecuteOpenEnum** les valeurs de **adExecuteStream** ou **adExecuteStream** ne doit pas être utilisé avec **Requery**.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **Requery** méthode pour actualiser tout le contenu d’un **Recordset** objet à partir de la source de données en réexécutant la commande d’origine et en extrayant les données une seconde fois. Appel de cette méthode équivaut à appeler le [fermer](../../../ado/reference/ado-api/close-method-ado.md) et [ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md) méthodes successivement. Si vous modifiez l’enregistrement actif ou ajouter un nouvel enregistrement, une erreur se produit.  
  
 Alors que le **Recordset** objet est ouvert, les propriétés qui définissent la nature du curseur ([CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md), [LockType](../../../ado/reference/ado-api/locktype-property-ado.md), [MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md) et ainsi de suite) sont en lecture seule. Par conséquent, le **Requery** méthode ne peut actualiser le curseur actuel. Pour modifier les propriétés du curseur et afficher les résultats, vous devez utiliser le [fermer](../../../ado/reference/ado-api/close-method-ado.md) méthode afin que les propriétés sont en lecture/écriture à nouveau. Vous pouvez ensuite modifier les paramètres de propriété et appelez le [ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md) méthode pour rouvrir le curseur.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Execute, Requery et Clear, méthodes-exemple (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery et Clear, méthodes-exemple (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery et Clear, méthodes-exemple (VC ++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CommandText, propriété (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)

