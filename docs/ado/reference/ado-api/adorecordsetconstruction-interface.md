---
description: ADORecordsetConstruction, interface
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
author: rothja
ms.author: jroth
ms.openlocfilehash: c17ccfe0a31714d5e2b3945960a4ff3d2ad55d1e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776638"
---
# <a name="adorecordsetconstruction-interface"></a>ADORecordsetConstruction, interface
L’interface **ADORecordsetConstruction** est utilisée pour construire un objet **Recordset** ADO à partir d’un objet d' **ensemble de lignes** OLE DB dans une application C/C++.  
  
 Cette interface prend en charge les propriétés suivantes :  
  
## <a name="properties"></a>Propriétés  
  
|Propriété|Description|  
|-|-|  
|[Chapitre](./chapter-property-ado.md)|Lecture/écriture.<br />Obtient/définit un objet OLE DB **chapitre** à partir de cet objet **Recordset** ADO.|  
|[RowPosition](./rowposition-property-ado.md)|Lecture/écriture.<br />Obtient/définit un objet OLE DB **RowPosition** à partir de cet objet **Recordset** ADO.|  
|[Ensemble de lignes](./rowset-property-ado.md)|Lecture/écriture.<br />Obtient/définit un objet d' **ensemble de lignes** OLE DB à partir de cet objet **Recordset** ADO.|  
  
## <a name="methods"></a>Méthodes  
 Aucun.  
  
## <a name="events"></a>Événements  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 À partir d’un objet d' **ensemble de lignes** OLE DB ( `pRowset` ), la construction d’un objet **Recordset** ADO ( `adoRs` ) se base sur les trois opérations de base suivantes :  
  
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
  
3.  Appelez la `IADORecordsetConstruction::put_Rowset` méthode Property pour définir l' `Rowset` objet OLE DB sur l' `Recordset` objet ADO :  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 L' `adoRs` objet résultant représente maintenant l’objet **Recordset** ADO construit à partir de l’objet d' **ensemble de lignes** OLE DB.  
  
 Vous pouvez également construire un objet **Recordset** ADO à partir d’un OLE DB **chapitre** ou **RowPosition** .  
  
## <a name="requirements"></a>Configuration requise  
 **Version :** ADO 2,0 et versions ultérieures  
  
 **Bibliothèque :** msado15.dll  
  
 **UUID :** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Voir aussi  
 [Recordset, objet (ADO)](./recordset-object-ado.md)   
 [Rowset, propriété (ADO)](./rowset-property-ado.md)