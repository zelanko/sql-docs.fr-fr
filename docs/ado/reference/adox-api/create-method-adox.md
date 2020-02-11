---
title: Create, méthode (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::raw_Create
- _Catalog::Create
helpviewer_keywords:
- Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aafcab3ad379dc25a2681a5d4f0d3f5e8d6eab5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67966670"
---
# <a name="create-method-adox"></a>Create, méthode (ADOX)
Crée un nouveau catalogue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ConnectString*  
 Valeur de **chaîne** utilisée pour se connecter à la source de données.  
  
## <a name="remarks"></a>Notes  
 La méthode **Create** crée et ouvre une nouvelle [connexion](../../../ado/reference/ado-api/connection-object-ado.md) ADO à la source de données spécifiée dans *connectString*. En cas de réussite, le nouvel objet de **connexion** est affecté à la propriété [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) .  
  
 Une erreur se produit si le fournisseur ne prend pas en charge la création de nouveaux catalogues.  
  
## <a name="applies-to"></a>S'applique à  
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Create, exemple de méthode (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection, propriété (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
