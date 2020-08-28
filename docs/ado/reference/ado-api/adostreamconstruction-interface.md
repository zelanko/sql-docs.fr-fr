---
description: ADOStreamConstruction, interface
title: Interface ADOStreamConstruction | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction
helpviewer_keywords:
- ADOStreamConstruction interface [ADO]
ms.assetid: 92f5a939-3e1a-4b14-a9dd-90e6ce2dec74
author: rothja
ms.author: jroth
ms.openlocfilehash: f6e32b076fa0faa43a3dff46aed66bcadaa2f1ae
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88976160"
---
# <a name="adostreamconstruction-interface"></a>ADOStreamConstruction, interface
L’interface **ADOStreamConstruction** est utilisée pour construire un objet de **flux** ADO à partir d’un objet OLE DB **IStream** dans une application C/C++.  
  
## <a name="properties"></a>Propriétés  
  
|Propriété|Description|  
|-|-|  
|[Flux](./stream-property.md)|Lecture/écriture. Obtient/définit un objet de **flux** OLE DB.|  
  
## <a name="methods"></a>Méthodes  
 Aucun.  
  
## <a name="events"></a>Événements  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 Étant donné un objet OLE DB **IStream** ( `pStream` ), la construction d’un objet de **flux** ADO ( `adoStr` ) se base sur les trois opérations de base suivantes :  
  
1.  Créez un objet de **flux** ADO :  
  
    ```  
    Stream20Ptr adoStr;  
    adoStr.CreateInstance(__uuidof(Stream));  
    ```  
  
2.  Interrogez l’interface **IADOStreamConstruction** sur l’objet de **flux** :  
  
    ```  
    adoStreamConstructionPtr adoStrConstruct=NULL;  
    adoStr->QueryInterface(__uuidof(ADOStreamConstruction),  
                         (void**)&adoStrConstruct);  
    ```  
  
 Appelez la `IADOStreamConstruction::get_Stream` méthode Property pour définir l’objet OLE DB **IStream** sur l’objet ADO **Stream** :  
  
```  
IUnknown *pUnk=NULL;  
pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
adoStrConstruct->put_Stream(pUnk);  
```  
  
 L' `adoStr` objet résultant représente maintenant l’objet de **flux** ADO construit à partir de l’objet OLE DB **IStream** .  
  
## <a name="requirements"></a>Spécifications  
 **Version :** ADO 2,0 ou version ultérieure  
  
 **Bibliothèque :** msado15.dll  
  
 **UUID :** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ADO](./ado-api-reference.md)