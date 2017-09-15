---
title: Interface ADORecordConstruction | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADORecordConstruction
helpviewer_keywords:
- ADORecordConstruction interface [ADO]
ms.assetid: 52a5429e-5829-455e-be3b-31f05cbecf2d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3966038215e1d26828d60b739ac6060859eabd67
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="adorecordconstruction-interface"></a>Interface ADORecordConstruction
Le **ADORecordConstruction**interface est utilisée pour construire un ADO **enregistrement** objet OLE DB **ligne** objet dans une application C/C++.  
  
 Cette interface prend en charge les propriétés suivantes :  
  
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|En écriture seule.<br />Définit le conteneur d’OLE DB **ligne** objet cette ADO **enregistrement** objet.|  
|[Ligne](../../../ado/reference/ado-api/row-property-ado.md)|En lecture/écriture.<br />Obtient ou définit un OLE DB **ligne** objet à partir de/sur cette ADO **enregistrement** objet.|  
  
## <a name="methods"></a>Méthodes  
 Aucun.  
  
## <a name="events"></a>Événements  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 Étant donné un OLE DB **ligne** objet (`pRow`), la construction de ADO **enregistrement** objet (`adoR`), s’élève à trois opérations ci-après :  
  
1.  Créer un ADO **enregistrement** objet :  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  Requête le **IADORecordConstruction** de l’interface sur le **enregistrement** objet :  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  Appelez le **IADORecordConstruction::put_Row** méthode propriété OLE DB **ligne** objet ADO **enregistrement** objet :  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 Résultant **adoR** objet représente maintenant l’ADO **enregistrement** objet construit à partir d’OLE DB **ligne** objet.  
  
 ADO **enregistrement** objet peut également être créé à partir du conteneur de OLE DB **ligne** objet.  
  
## <a name="requirements"></a>Spécifications  
 **Version :** ADO 2.0 et versions ultérieur  
  
 **Bibliothèque :** msado15.dll  
  
 **UUID :** 00000567-0000-0010-8000-00AA006D2EA4
