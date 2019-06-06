---
title: ADORecordsetConstruction, Interface | Microsoft Docs
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
manager: jroth
ms.openlocfilehash: f08d007395c85ef6b423c7db6c1aed5b39cb27ca
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718548"
---
# <a name="adorecordsetconstruction-interface"></a>ADORecordsetConstruction, interface
Le **ADORecordsetConstruction** interface est utilisée pour construire une ADO **Recordset** objet à partir d’un OLE DB **ensemble de lignes** objet dans une application C/C++.  
  
 Cette interface prend en charge les propriétés suivantes :  
  
## <a name="properties"></a>Properties  
  
|||  
|-|-|  
|[Chapitre](../../../ado/reference/ado-api/chapter-property-ado.md)|En lecture/écriture.<br />Obtient/définit une OLE DB **chapitre** objet à partir de/sur cette ADO **Recordset** objet.|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|En lecture/écriture.<br />Obtient/définit une OLE DB **RowPosition** objet à partir de/sur cette ADO **Recordset** objet.|  
|[Rowset](../../../ado/reference/ado-api/rowset-property-ado.md)|En lecture/écriture.<br />Obtient/définit une OLE DB **ensemble de lignes** objet à partir de/sur cette ADO **Recordset** objet.|  
  
## <a name="methods"></a>Méthodes  
 Aucun.  
  
## <a name="events"></a>Événements  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 Étant donné un OLE DB **ensemble de lignes** objet (`pRowset`), la construction de ADO **Recordset** objet (`adoRs`) s’élève à trois opérations ci-après :  
  
1.  Créer un ADO **Recordset** objet :  
  
    ```  
    Recordset20Ptr adoRs;  
    adoRs.CreateInstance(__uuidof(Recordset));  
    ```  
  
2.  Requête la **IADORecordsetConstruction** interface sur le **Recordset** objet :  
  
    ```  
    adoRecordsetConstructionPtr adoRsConstruct=NULL;  
    adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),  
                         (void**)&adoRsConstruct);  
    ```  
  
3.  Appelez le `IADORecordsetConstruction::put_Rowset` méthode de propriété pour définir le OLE DB `Rowset` objet sur le ADO `Recordset` objet :  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 La résultante `adoRs` objet représente maintenant le ADO **Recordset** objet construit à partir d’OLE DB **ensemble de lignes** objet.  
  
 Vous pouvez également construire ADO **Recordset** objet à partir d’un OLE DB **chapitre** ou **RowPosition** objet.  
  
## <a name="requirements"></a>Configuration requise  
 **Version :** ADO 2.0 et versions ultérieur  
  
 **Bibliothèque :** msado15.dll  
  
 **UUID :** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Rowset, propriété (ADO)](../../../ado/reference/ado-api/rowset-property-ado.md)
