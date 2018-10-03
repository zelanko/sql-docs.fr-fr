---
title: ADORecordConstruction, Interface | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction
helpviewer_keywords:
- ADORecordConstruction interface [ADO]
ms.assetid: 52a5429e-5829-455e-be3b-31f05cbecf2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21975fb2442aea97e362cd71b24c087f58addc0f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686867"
---
# <a name="adorecordconstruction-interface"></a>ADORecordConstruction, interface
Le **ADORecordConstruction**interface est utilisée pour construire une ADO **enregistrement** objet à partir d’un OLE DB **ligne** objet dans une application C/C++.  
  
 Cette interface prend en charge les propriétés suivantes :  
  
## <a name="properties"></a>Properties  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|En écriture seule.<br />Définit le conteneur d’OLE DB **ligne** objet sur cette ADO **enregistrement** objet.|  
|[Ligne](../../../ado/reference/ado-api/row-property-ado.md)|En lecture/écriture.<br />Obtient/définit une OLE DB **ligne** objet à partir de/sur cette ADO **enregistrement** objet.|  
  
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
  
2.  Requête la **IADORecordConstruction** interface sur le **enregistrement** objet :  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  Appelez le **IADORecordConstruction::put_Row** méthode de propriété pour définir le OLE DB **ligne** objet sur le ADO **enregistrement** objet :  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 La résultante **adoR** objet représente maintenant le ADO **enregistrement** objet construit à partir d’OLE DB **ligne** objet.  
  
 ADO **enregistrement** objet peut également être créé à partir du conteneur de OLE DB **ligne** objet.  
  
## <a name="requirements"></a>Spécifications  
 **Version :** ADO 2.0 et versions ultérieur  
  
 **Bibliothèque :** msado15.dll  
  
 **UUID :** 00000567-0000-0010-8000-00AA006D2EA4
