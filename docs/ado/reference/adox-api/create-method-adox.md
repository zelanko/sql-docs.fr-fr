---
title: Créer, méthode (ADOX) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 5ca88f95882da8e900e7695f81570b46977db9c9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789657"
---
# <a name="create-method-adox"></a>Create, méthode (ADOX)
Crée un nouveau catalogue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ConnectString*  
 Un **chaîne** valeur utilisée pour se connecter à la source de données.  
  
## <a name="remarks"></a>Notes  
 Le **créer** méthode crée et ouvre un nouvel ADO [connexion](../../../ado/reference/ado-api/connection-object-ado.md) à la source de données spécifiée dans *ConnectString*. En cas de réussite, la nouvelle **connexion** objet est assigné à la [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) propriété.  
  
 Une erreur se produit si le fournisseur ne prend pas en charge la création de catalogues.  
  
## <a name="applies-to"></a>S'applique à  
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer l’exemple de méthode (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection, propriété (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
