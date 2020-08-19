---
description: Delete, méthode (collections ADOX)
title: Delete, méthode (collections ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7345337ab35f4154fd9dc53f749e04dba96dad48
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440111"
---
# <a name="delete-method-adox-collections"></a>Delete, méthode (collections ADOX)
Supprime un objet d’une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 **Variant** qui spécifie le nom ou la position ordinale (index) de l’objet à supprimer.  
  
## <a name="remarks"></a>Notes  
 Une erreur se produit si le *nom* n’existe pas dans la collection.  
  
 Pour les collections de [tables](../../../ado/reference/adox-api/tables-collection-adox.md) et d' [utilisateurs](../../../ado/reference/adox-api/users-collection-adox.md) , une erreur se produit si le fournisseur ne prend pas en charge la suppression de tables ou d’utilisateurs, respectivement. Pour les collections de [procédures](../../../ado/reference/adox-api/procedures-collection-adox.md) et de [vues](../../../ado/reference/adox-api/views-collection-adox.md) , la **suppression** échoue si le fournisseur ne prend pas en charge les commandes persistantes.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Columns, collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
        [Groups, collection (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)  
        [Indexes, collection (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Keys, collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)  
        [Procedures, collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
        [Tables, collection (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Users, collection (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)  
        [Views, collection (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [Procedures, exemple de méthode Delete (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Views, exemple de méthode Delete (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)
