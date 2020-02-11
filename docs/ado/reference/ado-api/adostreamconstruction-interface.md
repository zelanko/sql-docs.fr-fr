---
title: Interface ADOStreamConstruction | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 70a6dd02722a34159b345a83b32897aa8c38d0ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920788"
---
# <a name="adostreamconstruction-interface"></a>ADOStreamConstruction, interface
L’interface **ADOStreamConstruction** est utilisée pour construire un objet de **flux** ADO à partir d’un objet OLE DB **IStream** dans une application C/C++.  
  
## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|[Stream, propriété](../../../ado/reference/ado-api/stream-property.md)|Lecture/écriture. Obtient/définit un objet de **flux** OLE DB.|  
  
## <a name="methods"></a>Méthodes  
 Aucun.  
  
## <a name="events"></a>Événements  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 Étant donné un **** objet OLE DB IStream`pStream`(), la construction d’un objet de **flux** ADO (`adoStr`) se base sur les trois opérations de base suivantes :  
  
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
  
 L’objet `adoStr` résultant représente maintenant l’objet de **flux** ADO construit à partir de l’objet OLE DB **IStream** .  
  
## <a name="requirements"></a>Spécifications  
 **Version :** ADO 2,0 ou version ultérieure  
  
 **Bibliothèque :** msado15. dll  
  
 **UUID :** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ADO](../../../ado/reference/ado-api/ado-api-reference.md)
