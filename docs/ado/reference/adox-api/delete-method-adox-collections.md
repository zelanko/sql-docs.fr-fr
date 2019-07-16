---
title: DELETE, méthode (Collections ADOX) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: be2aa91cf27d7dc12d3cd0c1e0bf719bd43797ab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67966433"
---
# <a name="delete-method-adox-collections"></a>Delete, méthode (collections ADOX)
Supprime un objet d’une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 Un **Variant** qui spécifie le nom ou la position ordinale (index) de l’objet à supprimer.  
  
## <a name="remarks"></a>Notes  
 Une erreur se produit si le *nom* n’existe pas dans la collection.  
  
 Pour [Tables](../../../ado/reference/adox-api/tables-collection-adox.md) et [utilisateurs](../../../ado/reference/adox-api/users-collection-adox.md) collections, une erreur se produit si le fournisseur ne prend pas en charge la suppression des tables ou des utilisateurs, respectivement. Pour [procédures](../../../ado/reference/adox-api/procedures-collection-adox.md) et [vues](../../../ado/reference/adox-api/views-collection-adox.md) collections, **supprimer** échoue si le fournisseur ne prend pas en charge les commandes persistantes.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Columns, collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Groups, collection (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Indexes, collection (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys, collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Procedures, collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|[Tables, collection (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|  
|[Users, collection (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|[Views, collection (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)||  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures Delete, exemple de méthode (VB)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Views, exemple de méthode Delete (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)
