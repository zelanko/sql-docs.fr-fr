---
title: "Create (méthode) (ADOX) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Catalog::raw_Create
- _Catalog::Create
helpviewer_keywords: Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b31df006624acdfd66a55c467be5a59dfc6afd1
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="create-method-adox"></a>Create (méthode) (ADOX)
Crée un nouveau catalogue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ConnectString*  
 A **chaîne** valeur utilisée pour se connecter à la source de données.  
  
## <a name="remarks"></a>Notes  
 Le **créer** méthode crée et ouvre un nouvel objet ADO [connexion](../../../ado/reference/ado-api/connection-object-ado.md) à la source de données spécifiée dans *ConnectString*. En cas de réussite, la nouvelle **connexion** objet est assigné à la [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) propriété.  
  
 Une erreur se produit si le fournisseur ne prend pas en charge la création de catalogues.  
  
## <a name="applies-to"></a>S'applique à  
 [Catalog, objet (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un exemple de méthode (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [ActiveConnection, propriété (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
