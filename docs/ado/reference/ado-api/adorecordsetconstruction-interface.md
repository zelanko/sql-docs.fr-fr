---
title: ADORecordsetConstruction, interface | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction
helpviewer_keywords:
- ADORecordsetConstruction interface [ADO]
ms.assetid: 08386eba-f1f7-4879-8ffd-8733930ecb2f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1e1d14255acd4cc7f18abea1c494353ef970903c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920796"
---
# <a name="adorecordsetconstruction-interface"></a>ADORecordsetConstruction, interface
L’interface **ADORecordsetConstruction** est utilisée pour construire un objet **Recordset** ADO à partir d’un objet d' **ensemble de lignes** OLE DB dans une application C/C++.  
  
 Cette interface prend en charge les propriétés suivantes :  
  
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|[Chapitre](../../../ado/reference/ado-api/chapter-property-ado.md)|Lecture/écriture.<br />Obtient/définit un objet OLE DB **chapitre** à partir de cet objet **Recordset** ADO.|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|Lecture/écriture.<br />Obtient/définit un objet OLE DB **RowPosition** à partir de cet objet **Recordset** ADO.|  
|[Ensemble de lignes](../../../ado/reference/ado-api/rowset-property-ado.md)|Lecture/écriture.<br />Obtient/définit un objet d' **ensemble de lignes** OLE DB à partir de cet objet **Recordset** ADO.|  
  
## <a name="methods"></a>Méthodes  
 Aucune.  
  
## <a name="events"></a>Événements  
 Aucune.  
  
## <a name="remarks"></a>Notes  
 À partir d' **Rowset** un objet d'`pRowset`ensemble de lignes OLE DB (), la construction d’un`adoRs`objet **Recordset** ADO () se base sur les trois opérations de base suivantes :  
  
1.  Créez un objet **Recordset** ADO :  
  
    ```  
    Recordset20Ptr adoRs;  
    adoRs.CreateInstance(__uuidof(Recordset));  
    ```  
  
2.  Interrogez l’interface **IADORecordsetConstruction** sur l’objet **Recordset** :  
  
    ```  
    adoRecordsetConstructionPtr adoRsConstruct=NULL;  
    adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),  
                         (void**)&adoRsConstruct);  
    ```  
  
3.  Appelez la `IADORecordsetConstruction::put_Rowset` méthode Property pour définir l’objet `Rowset` OLE DB sur l’objet `Recordset` ADO :  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 L’objet `adoRs` résultant représente maintenant l’objet **Recordset** ADO construit à partir de l’objet d' **ensemble de lignes** OLE DB.  
  
 Vous pouvez également construire un objet **Recordset** ADO à partir d’un OLE DB **chapitre** ou **RowPosition** .  
  
## <a name="requirements"></a>Spécifications  
 **Version :** ADO 2,0 et versions ultérieures  
  
 **Bibliothèque :** msado15. dll  
  
 **UUID :** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Voir aussi  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Rowset, propriété (ADO)](../../../ado/reference/ado-api/rowset-property-ado.md)
