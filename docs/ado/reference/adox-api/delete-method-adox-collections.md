---
title: "DELETE, méthode (Collections ADOX) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Views::Delete
- Groups::Delete
- Indexes::raw_Delete
- Columns::raw_Delete
- Tables::Delete
- Keys::Delete
- Users::Delete
- Users::raw_Delete
- Keys::raw_Delete
- Procedures::raw_Delete
- Views::raw_Delete
- Indexes::Delete
- Procedures::Delete
- Groups::raw_Delete
- Tables::raw_Delete
- Columns::Delete
helpviewer_keywords:
- delete method [ADOX]
ms.assetid: e6b6e3a4-8952-4d79-81f4-51019c338374
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 72dd3f6d514b20bb28f9daee6fc16c5c7c346095
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="delete-method-adox-collections"></a>DELETE, méthode (Collections ADOX)
Supprime un objet d’une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 A **Variant** qui spécifie le nom ou la position ordinale (index) de l’objet à supprimer.  
  
## <a name="remarks"></a>Notes  
 Une erreur se produit si le *nom* n’existe pas dans la collection.  
  
 Pour [Tables](../../../ado/reference/adox-api/tables-collection-adox.md) et [utilisateurs](../../../ado/reference/adox-api/users-collection-adox.md) collections, une erreur se produit si le fournisseur ne prend pas en charge suppression des tables ou des utilisateurs, respectivement. Pour [procédures](../../../ado/reference/adox-api/procedures-collection-adox.md) et [vues](../../../ado/reference/adox-api/views-collection-adox.md) collections, **supprimer** échoue si le fournisseur ne prend pas en charge les commandes persistantes.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Collection de colonnes (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Collection de groupes (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Collection d’index (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Collection de clés (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Collection de procédures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|[Collection de tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|  
|[Collection d’utilisateurs (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|[Collection de vues (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)||  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de méthode (VB) de suppression de procédures](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Exemple de méthode (VB) de suppression de vues](../../../ado/reference/adox-api/views-delete-method-example-vb.md)

