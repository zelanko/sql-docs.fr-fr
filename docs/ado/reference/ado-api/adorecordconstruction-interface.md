---
title: Interface ADORecordConstruction | Microsoft Docs
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
ms.openlocfilehash: c56ba0b9d7ebebbf4a9e4baf669bbdc6eb84355e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920806"
---
# <a name="adorecordconstruction-interface"></a>ADORecordConstruction, interface
L’interface **ADORecordConstruction**est utilisée pour construire un objet **enregistrement** ADO à partir d’un objet OLE DB **Row** dans une application C/C++.  
  
 Cette interface prend en charge les propriétés suivantes :  
  
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|En écriture seule.<br />Définit le conteneur d’un objet OLE DB **Row** sur cet objet ADO **Record** .|  
|[Haut](../../../ado/reference/ado-api/row-property-ado.md)|Lecture/écriture.<br />Obtient/définit un objet de **ligne** OLE DB à partir de cet objet **enregistrement** ADO.|  
  
## <a name="methods"></a>Méthodes  
 Aucun.  
  
## <a name="events"></a>Événements  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 À partir d' **** un objet Row`pRow`OLE DB (), la construction d’un objet **Record** ADO (`adoR`) s’élève aux trois opérations de base suivantes :  
  
1.  Créez un objet **enregistrement** ADO :  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  Interrogez l’interface **IADORecordConstruction** sur l’objet **Record** :  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  Appelez la méthode de propriété **IADORecordConstruction ::p ut_Row** pour définir l’objet de **ligne** OLE DB sur l’objet ADO **Record** :  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 L’objet **Ador** qui en résulte représente maintenant l’objet **Record** ADO construit à partir de l’objet OLE DB **Row** .  
  
 Un objet **Record** ADO peut également être construit à partir du conteneur d’un objet OLE DB **Row** .  
  
## <a name="requirements"></a>Spécifications  
 **Version :** ADO 2,0 et versions ultérieures  
  
 **Bibliothèque :** msado15. dll  
  
 **UUID :** 00000567-0000-0010-8000-00AA006D2EA4
